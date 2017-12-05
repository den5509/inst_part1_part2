Mac OS
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

----------

MS Windows
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Контейнеры Windows возможно использовать только в Windows10 Профессиональная и Windows10 Корпоративная (Anniversary Edition). В его рамках вы сможите установить Docker для Windows и запустить контейнеры необходимые для выпонения лабораторных работ. 

Для использования контейнеров Windows Server требуется изоляции Hyper-V в Windows 10, чтобы разработчики получили одинаковую версию ядра и конфигурации, которая будет использоваться применяться в рабочей среде. Необходима система под управлением Windows 10 Anniversary Edition или Creators Update (Профессиональная или Корпоративная). На самом деле это все можно сделать и на виртуальной машине Windows10, однако при этом нужно включить вложенную виртуализацию. Чтобы контейнеры Windows работали, необходимо установить критические обновления. Чтобы узнать версию ОС, запустите winver.exe и сравните указанную версию с версией в журнале обновлений Windows10. Убедитесь, что у вас установлена версия 14393.222 или более поздняя, перед тем как продолжить установку.
Скачайте Docker для Windows и запустите `программу установки. <https://docs.docker.com/docker-for-windows/install/#download-docker-for-windows>`_ 
Сделать это можно на сайте с подробной инструкцией от Docker непсрественно. Не забудьте перезагрузить систему после установки Docker. После перезагрузки запускаем приложение Docker for Windows. Тут необходимо пройти авторизацию по профилю на Docker Hub.
Собственно все, после этого можно приступать к запуску контейнеров через командную строку Windows.


Linux Mint
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Добавляем репозиторий Docker:

.. code-block:: text
    
    sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 \
      --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
      
    # Next, point the package manager to the official Docker repository
    
    sudo apt-add-repository 'deb https://apt.dockerproject.org/repo ubuntu-xenial main'
 
    # Update the package database
 
    sudo apt update
    #
    
    sudo apt install linux-image-generic linux-image-extra-virtual
 
    # Reboot the system so it would be running on the newly installed kernel image
 
    sudo reboot
 
Теперь переходим непосредственно к установке:

.. code-block:: text 

    sudo apt install docker-engine
 
    #
    # Run a Docker container
    # This container is just a test container, and it will run and exit
 
    sudo docker run hello-world
 
    #
   
Ubuntu
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Обновите индекс пакетов:
 
.. code-block:: text  

    sudo apt-get update
    
Теперь можно загрузить и установить пакет Docker. Добавьте в систему GPG-ключ репозитория Docker:

.. code-block:: text  

    sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 \
    --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
    
Добавьте этот репозиторий в APT: 

.. code-block:: text  

    echo "deb https://apt.dockerproject.org/repo ubuntu-xenial main"  
    
    sudo tee /etc/apt/sources.list.d/docker.list

Обновите индекс пакетов:
 
.. code-block:: text  

    sudo apt-get update
    
Следующая команда позволяет переключиться из репозитория Ubuntu 16.04 в репозиторий Docker:

.. code-block:: text  

    apt-cache policy docker-engine
    
Обратите внимание: пакет docker-engine пока не установлен. Версия пакета может отличаться.    
    
Чтобы установить Docker, введите:    
    
.. code-block:: text  

    sudo apt-get install -y docker-engine   
    
После этого программа Docker будет установлена; также это запустит демона и настроит автозапуск процесса. Чтобы убедиться в том, что программа работает, запросите её состояние:    
    
.. code-block:: text  

    sudo systemctl status docker    
    

Настройка команды docker (опционально)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^  
    
По умолчанию команда docker требует привилегий root (или доступа к команде sudo). Также её можно запускать в группе docker, которая создаётся автоматически во время установки программы Docker.

Если вы попытаетесь запустить команду docker без префикса sudo и вне группы docker, вы получите ошибку:

.. code-block:: text  

    docker: Cannot connect to the Docker daemon. Is the docker daemon running on this host?.
    See 'docker run --help'.    
    
Чтобы вам не пришлось набирать префикс sudo каждый раз когда вам нужно запустить команду docker, добавьте своего пользователя в группу docker:
    
.. code-block:: text  

    sudo usermod -aG docker $(whoami)
    
Чтобы активировать это изменение, выйдите из системы и войдите снова.

Чтобы добавить в группу docker пользователя, который не является текущим, укажите в команде его имя:    
    
.. code-block:: text  

    sudo usermod -aG docker username  
    
    
    
    
    
    
    
    
