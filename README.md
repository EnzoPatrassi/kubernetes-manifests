1) Estructura del Proyecto
0311at/
├── static-website/
└── kubernetes-manifests/
    ├── volumen/
    ├── despliegue/
    └── servicio/
   
2) Dentro de esas carpetas crear:
static-website/: Archivos index.html y styles.css.
kubernetes-manifests/volumen/: pv.yaml y pvc.yaml.
kubernetes-manifests/despliegue/: deployment.yaml.
kubernetes-manifests/servicio/: service.yaml.

3) Crea dos repositorios vacíos en GitHub:
Uno llamado static-website
Otro llamado kubernetes-manifests

4) Clonar los Repositorios
Clona ambos repositorios en tu máquina local:
git clone https://github.com/EnzoPatrassi/static-website
git clone https://github.com/EnzoPatrassi/kubernetes-manifests

5) Inicializar Git en cada carpeta y hacer push a nuestra cuenta de GitHub. Por ejemplo:

Para static-website:
cd static-website
git init
git remote add origin https://github.com/tu-usuario/static-website.git
git add .
git commit -m "Initial commit"
git push -u origin main

Para kubernetes-manifests:
cd kubernetes-manifests
git init
git remote add origin https://github.com/tu-usuario/kubernetes-manifests.git
git add .
git commit -m "Initial commit"
git push -u origin main

6)Iniciar Minikube:
minikube start -p 0311at

7)Montar el volumen local(Deja esta terminal abierta durante toda la ejecución):
minikube -p 0311at mount "D:/0311at/static-website:/mnt/web"

Aplicar los manifiestos:
Desde el directorio raíz de kubernetes-manifests
kubectl apply -f volumen/
kubectl apply -f despliegue/
kubectl apply -f servicio/

 Acceder a la Aplicación Web:
 minikube -p 0311at service web-static-service
