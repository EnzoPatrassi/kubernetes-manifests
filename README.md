## 1) Estructura del Proyecto
```bash
0311at/
│
├── static-website/  
└── kubernetes-manifests/
    ├── volumen/ 
    ├── despliegue/ 
    └── servicio/
```
## 2) Dentro de esas carpetas crear:
```bash
static-website/: Archivos index.html y styles.css.
kubernetes-manifests/volumen/: pv.yaml y pvc.yaml.
kubernetes-manifests/despliegue/: deployment.yaml.
kubernetes-manifests/servicio/: service.yaml.
```
## 3) Crea dos repositorios vacíos en GitHub:
```bash
Uno llamado static-website
Otro llamado kubernetes-manifests
```
## 4) Clonar los Repositorios
Clona ambos repositorios en tu máquina local:
```bash
git clone https://github.com/EnzoPatrassi/static-website
git clone https://github.com/EnzoPatrassi/kubernetes-manifests
```
## 5) Inicializar Git en cada carpeta y hacer push a nuestra cuenta de GitHub. Por ejemplo:
Para static-website:
```bash
cd static-website
git init
git remote add origin https://github.com/EnzoPatrassi/static-website.git
git add .
git commit -m "Initial commit"
git push -u origin main
``` 
Para kubernetes-manifests:
```bash
cd kubernetes-manifests
git init
git remote add origin https://github.com/EnzoPatrassi/kubernetes-manifests.git
git add .
git commit -m "Initial commit"
git push -u origin main
```
## 6)Iniciar Minikube:
```bash
minikube start -p 0311at
```
## 7)Montar el volumen local(Deja esta terminal abierta durante toda la ejecución):
```bash
minikube -p 0311at mount "D:/0311at/static-website:/mnt/web"
```
## 8)Aplicar los manifiestos (desde otra ventana de Powershell):
Desde el directorio raíz de kubernetes-manifests
```bash
kubectl apply -f volumen/
kubectl apply -f despliegue/
kubectl apply -f servicio/
```
## 9)Acceder a la Aplicación Web:
```bash
minikube -p 0311at service web-static-service
```
