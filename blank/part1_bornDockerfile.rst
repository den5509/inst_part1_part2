Пример Dockerfile: 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Этот файл должен носить имя "Dockerfile" и должен быть размещен в репозитории с лабораторной работой.

.. code-block:: text

  FROM centos:7 # указываем имя образа ОС
  MAINTAINER "Name" <email@email.com> #автор образа и его email
  ENV container docker
  #
  # Обновление и очистка
  RUN yum -y update; yum clean all;
  #
  # Установка пакетов необходимых для выполнения лабораторной работы
  RUN yum -y install make nano gcc git sudo; yum clean all;
  #
  # Создание пользователя student и установка паролей
  RUN useradd -G wheel student; \
  echo -e "root:root123" | chpasswd; \
  echo -e "student:student123" | chpasswd;
  #
  # Определение каталогов монтируемых с хоста в образ
  VOLUME [ "/sys/fs/cgroup" ]
  VOLUME [ "/home/student" ]
  VOLUME [ "/root" ]
  #
  # файлы для выполнение лабораторной работы внутри контейнера
  ADD . /home/student/lab5
  #
  # скрипт, выводящий на экран отчет и запускающий bash
  # при запуске контейнера
  CMD ["/home/student/lab/init"]
  #
  # Порт для проброса на хост
  EXPOSE 80
