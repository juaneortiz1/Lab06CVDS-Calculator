
# Despliega mi primera aplicación en Azure

## Mi primer despliegue en la nube

### Parte I - Despliegue de mi aplicación React (frontend) en Azure

1. Accedo a [Azure for Students](https://azure.microsoft.com/es-es/free/students/) utilizando mi correo institucional.
2. ![image](https://github.com/juaneortiz1/Lab06CVDS-Calculator/assets/97971732/0b3ac1dc-c0cc-4aec-bc96-76bd75a1e4c4)
3. Creo un presupuesto de 1 dólar para mi cuenta.

![image](https://github.com/juaneortiz1/Lab06CVDS-Calculator/assets/97971732/0b3ac1dc-c0cc-4aec-bc96-76bd75a1e4c4)
![image](https://github.com/juaneortiz1/Lab06CVDS-Calculator/assets/97971732/0b3ac1dc-c0cc-4aec-bc96-76bd75a1e4c4)

### Parte II - Despliegue de mi aplicación web Spring MVC (o backend Spring Boot)

#### Creación del servidor MySQL en Azure

1. Inicio [Azure Cloud Shell](https://docs.microsoft.com/en-in/azure/cloud-shell/overview) desde el portal de Azure.
2. Para implementar en un grupo de recursos, ejecuto el siguiente comando:

```shell
az group create --name MyResourceGroup --location westus
```
![image](https://github.com/juaneortiz1/Lab06CVDS-Calculator/assets/97971732/5d69fb6d-3f2c-4a6a-98f6-d681991a916d)

![image](https://github.com/juaneortiz1/Lab06CVDS-Calculator/assets/97971732/58a5e26e-1fee-4515-bced-d0630e7ae244)


3. Creo un plan de servicio de aplicaciones:

```shell
az appservice plan create --resource-group MyResourceGroup --name MyPlan --sku F1
```
![image](https://github.com/juaneortiz1/Lab06CVDS-Calculator/assets/97971732/f6d7fa3f-36ad-47d7-85cc-e32907e15590)

4. Finalmente, creo el servidor MySQL con un nombre de servidor único:

```shell
az account list-locations --query "[].{DisplayName:displayName, Name:name}" -o table # elijo la región
az configure --defaults location=eastus # configuro la región
az mysql flexible-server create --resource-group MyResourceGroup --name pongaunnombreunico --admin-user mysqldbuser --admin-password P2ssw0rd@123 --sku-name Standard_B1ms
```
![image](https://github.com/juaneortiz1/Lab06CVDS-Calculator/assets/97971732/b5322cb4-9591-449b-85a5-a82ba16bb089)

![image](https://github.com/juaneortiz1/Lab06CVDS-Calculator/assets/97971732/c16f36af-0981-4f1f-8855-3eee3e5400f7)

> Importante: Introduzco un nombre de servidor SQL único. Utilizo minúsculas para el valor del campo "Nombre del servidor de base de datos".

#### Actualización de la configuración de mi aplicación web

1. Navego hasta el grupo de recursos que he creado. Debería ver un servidor **Azure Database for MySQL** aprovisionado. Selecciono el servidor de base de datos.

![imagen1](assets/img1.png)


2. Selecciono **Properties**. Guardo el **Server name** y el **Server admin login name** en un bloc de notas.

![imagen2](assets/img2.png)
![image](https://github.com/juaneortiz1/Lab06CVDS-Calculator/assets/97971732/1814658f-7ae3-4805-badd-82572e4a9a15)


3. Selecciono **Connection security** y habilito la opción **Allow access to Azure services**. Guardo los cambios.

![imagen3](assets/img3.png)

4. Modifico las cadenas de conexión de mi aplicación web para que se conecte correctamente a la base de datos. 

5. Desde Azure Portal, selecciono la aplicación web que he creado. Voy a **Configuración** > **Configuración de la aplicación** > **Cadenas de conexión** y agrego una nueva cadena de conexión MySQL.
6. ![image](https://github.com/juaneortiz1/Lab06CVDS-Calculator/assets/97971732/c7848847-f016-4d57-958a-d3209db19a8c)


7. Introduzco la cadena de conexión adecuada y hago clic en Guardar.

## Ejercicio 2: Actualización de mi aplicación web

![image](https://github.com/juaneortiz1/Lab06CVDS-Calculator/assets/97971732/7819972b-399e-4a6a-96f7-61f4c6086374)
![image](https://github.com/juaneortiz1/Lab06CVDS-Calculator/assets/97971732/99fdbae0-838e-4328-80f4-d0ad4a284665)
![image](https://github.com/juaneortiz1/Lab06CVDS-Calculator/assets/97971732/9a899616-6551-42df-b414-272d5b7e44b6)
![image](https://github.com/juaneortiz1/Lab06CVDS-Calculator/assets/97971732/2cb58f2e-6b14-47a0-8d6d-3fa2b6f49409)
![image](https://github.com/juaneortiz1/Lab06CVDS-Calculator/assets/97971732/6ffdcaa2-7f08-44e5-85ee-7d8e2411f31b)
![image](https://github.com/juaneortiz1/Lab06CVDS-Calculator/assets/97971732/36cfcfd6-a69c-484f-a3f7-8ed6456da000)
![image](https://github.com/juaneortiz1/Lab06CVDS-Calculator/assets/97971732/8a484f2c-df11-43fb-89f3-1997f5912836)

 
 




