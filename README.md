# docker_compose_php_nginx


# nginx conf 
```nginx
    location ~ \.php$ {
        #docker-compose -> services -> php8
        fastcgi_pass php8:9000;  

        #fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
    }



     location ~ \.php$ {
        #docker-compose -> services -> php
        fastcgi_pass php:9000;  

        #fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
    }

```