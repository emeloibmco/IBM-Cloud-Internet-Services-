# IBM-Cloud-Internet-Services-

_Implementación de Cloud Internet Services en una aplicaación desplegada en una Instancia de VPC_

<img width="940" alt="BareMetal-Architecture" src="">

## Prerrequisitos 🚀

Para esta Demo se requiere de conocimiento básico de DNS y redes.
Además de esto se requiere tener aprovisionado:
- [VPC.](https://cloud.ibm.com/docs/vpc?topic=vpc-getting-started)
- [Instancia en una VPC](https://cloud.ibm.com/docs/vpc?topic=vpc-vsi_best_practices) con un servicion web configurado en ella.
- [Load Balancer.](https://cloud.ibm.com/docs/vpc?topic=vpc-nlb-vs-elb)
- [Listas de control de accesos](https://cloud.ibm.com/docs/vpc?topic=vpc-using-acls)

## Comenzando 🚀
_Instrucciones_

Para la implementación de Cloud Internet Services en una VPC se procede a la creación de un servicio de Internet Services, siguiendo las siguientes instrucciones:



### Variables 📋

El aprovisionamiento de un BareMetal mensual con el provider terraform cuenta con las siguientes caracteristicas:

| Variable | Información |
| ------------- | ------------- |
| **ibmcloud_apikey**  | [API key](https://cloud.ibm.com/docs/iam?topic=iam-userapikey) unica del usuario que se requiere para aprovisionamiento de recursos |
| **ibm_region**  | Region en la que se encuentra ubicado el datacenter donde se aprovisionará el recurso |
| **bm_hostname** | Nombre del BareMetal a provisionar _No mayusculas_ |
| **bm_os_reference_code** | Referencia del paquete de sistemas operativos a instalar sobre el BareMetal (Depende de la capacidad del procesador elegida)|
|**datacenter**| [Datacenter](https://api.softlayer.com/rest/v3/SoftLayer_Hardware/getCreateObjectOptions.json) en el cual se aprovisionará el BareMetal |
| **bm_domain** | Dominio del Baremetal ´nombre del dominio´.cloud.com |
| **bm_network_speed** | Velocidad de la red |
| **private_network** | Si se requiere de un enlace a la red publica se coloca _false_ de lo contrario _true_ |
| **processor** | [Script con nombres clave de paquetes de procesador](https://api.softlayer.com/rest/v3/SoftLayer_Product_Package/getAllObjects?objectFilter={%22type%22:{%22keyName%22:{%22operation%22:%22BARE_METAL_CPU%22}}}) a instalar sobre el BareMetal (Depende de la capacidad del procesador elegida|
| **key_process** | [Script con nombres clave de procesador](https://api.softlayer.com/rest/v3/SoftLayer_Product_Package/getAllObjects?objectFilter={%22type%22:{%22keyName%22:{%22operation%22:%22BARE_METAL_CPU%22}}}) a instalar sobre el BareMetal (Depende de la capacidad del procesador elegida |
| **disk_key_name** | Nombre clave de disco(s) de almacenamiento |
| **notes** | Notas de información del BareMetal |


Para acceder a información de **api softlayer** se requiere de la [APIkey-ClassicInfrastructure](https://cloud.ibm.com/docs/iam?topic=iam-classic_keys&locale=es) y el usuario de la cuenta 

La variable **bm_os_reference_code** cuenta con las siguientes opciones para SAP - Certified

- OS_WINDOWS_SERVER_2019_DATACENTER_EDITION_64BIT ( Windows Server 2019 Datacenter Edition (64 bit) )
- (5DWPD) ) 
- HARD_DRIVE_2_00_TB_SATA_2 ( 2.00 TB SATA )

### Pasos para el despliegue en Schematics 🔧

Se debe dirigir al simbolo de ![](images/menu.JPG) en donde encontrará la opción de **Schematics** una vez alli se creará un nuevo workspace donde se contará con la siguiente pestaña:
<img width="945" alt="workspace" src="images/workspace.JPG">

En el espacio sobremarcado con rojo se debe pegar el link del repositorio y de ser necesario en la parte de abajo el Token para permisos de acceso. Se presiona el botón sobremarcado con amarillo para adquirir las variables a rellenar. Luego de rellenarlas se debe crear el workspace. En caso de realizar el procedimiento de forma correcta se contará con la siguiente pestaña:
<img width="945" alt="workspace" src="images/workspace1.JPG">

Se debe generar el plan con el botón que aparece en pantalla y de generarse correctamente se podrá aplicar el plan. _Solo hasta aplicar el plan se va a generar facturación_

---
#### Autores: IBM Cloud Tech Sales
