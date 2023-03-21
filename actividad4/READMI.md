# Actividad 4

##### Creamos el script que contendra el mensaje que queremos mostrar

    #!/bin/bash
    
    echo "Hola desde el script, la fecha actual es: $(date +%Y-%m-%d)"

##### Le damos permisos de ejecucion 
chmod +x actividad4.sh

    chmod +x actividad4.sh

##### Creamos el archivo de servicio con lo siquiente: 

    sudo nano /etc/systemd/system/actividad4.service


##### ejecutamos los siguientes comandos para poder tener el servicio: 

    sudo systemctl daemon-reload   
    sudo systemctl start actividad4.service   


##### por ultimo si deseamos podemos verificar nuestro servicio:

    sudo systemctl status actividad4.service 
