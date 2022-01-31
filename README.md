# Домашнее задание к занятию "08.02 Работа с Playbook"

Playbook описывает установку Java из локального архива, скачивание и установку Elasticsearch и Kibana с официальных сайтов
 в локальный Docker-контейнер "ubuntu". 

Параметры, указываемые в файлах vars.yml в соответствующих папках в group_vars/:  
- all  
`java_jdk_version` - версия java;  
`java_oracle_jdk_package` - файл дистрибутива java, который должен находиться в папке files;  
- elasticsearch  
`elastic_version` - версия Elasticsearch;  
  `elastic_home` - путь установки Elasticsearch;
- kibana  
`kibana_version` - версия kibana;  
  `kibana_home` - путь установки kibana.  
  
Структура site.yml состоит из 3 plays:  
- `Install Java` - определение пути установки, копирование и распаковка дистрибутива, 
запись пути в переменную окружения `JAVA_HOME` и `PATH` с помощью шаблона `templates/jdk.sh.j2`.
Все tasks данного play помечены тэгом `java`.  
- `Install Elasticsearch` - определение пути установки, определение URL, скачивание и распаковка дистрибутива, 
запись пути в переменную окружения `ES_HOME` и `PATH` с помощью шаблона `templates/elk.sh.j2`.
Все tasks данного play помечены тэгом `elasticsearch`.  
- `Install Kibana` - определение пути установки, определение URL, скачивание и распаковка дистрибутива, 
запись пути в переменную окружения `KIBANA_HOME` и `PATH` с помощью шаблона `templates/kibana.sh.j2`.
Все tasks данного play помечены тэгом `kibana`.
