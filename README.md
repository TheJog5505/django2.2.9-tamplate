### Start new project
`django-admin startproject BRAND_NEW -n={project-root-dir-name} -n={additional_name_for_configs} --name=nginx,supervisor.conf,celery.conf,uwsgi.ini,README.md --template=https://github.com/TheJog5505/django-tamplate/archive/master.zip`

### After project creation
Rename "BRAND_NEW" dir to "{{ files.0 }}" with command\
`test -d {{project_directory|cut:project_name}}{{files.0}} && echo "Directory '{{project_directory|cut:project_name}}{{files.0}}' already exists!" || mv {{project_directory}}/ {{project_directory|cut:project_name}}{{files.0}}/`

### Some explanation
`project-root-dir-name` and `additional_name_for_configs` using in templates like\
`command=/root/.virtualenvs/{additional_name_for_configs}_env/bin/uwsgi --emperor /var/www/{project-root-dir-name}/conf/dev/uwsgi.ini`\
`command=/root/.virtualenvs/additional_name_for_configs_env/bin/uwsgi --emperor /var/www/project-root-dir-name/conf/dev/uwsgi.ini`


`project-root-dir-name` - using in\
`conf\dev\celery.conf, conf\dev\nginx, conf\dev\supervisor.conf, conf\dev\uwsgi.ini`\
`conf\prod\celery.conf, conf\prod\nginx, conf\prod\supervisor.conf, conf\prod\uwsgi.ini`\
`src\core\handlers.py src\core\urls.py`\
`README.md`\

`additional_name_for_configs` - using in\
`conf\dev\celery.conf, conf\dev\supervisor.conf, conf\dev\uwsgi.ini`\
`conf\prod\celery.conf, conf\prod\supervisor.conf, conf\prod\uwsgi.ini`\
`src\core\celery.py src\core\base.py`\