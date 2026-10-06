# knote

App Spring Boot para tomar notas (Markdown + imágenes).
Versión 2.0.0: **stateless** — el texto de las notas va en MongoDB y las imágenes en Minio.

## Correr local
```bash
docker run --name=mongo --rm -p 27017:27017 mongo
docker run --name=minio --rm -p 9000:9000 -e MINIO_ACCESS_KEY=mykey -e MINIO_SECRET_KEY=mysecret minio/minio:RELEASE.2022-10-29T06-21-33Z server /data
mvn -Dminio.access.key=mykey -Dminio.secret.key=mysecret spring-boot:run
```
Abrir http://localhost:8080

## Imagen Docker
```bash
mvn clean package -DskipTests
docker build -t <usuario>/knote:2.0.0 .
docker push <usuario>/knote:2.0.0
```

## Kubernetes (Minikube)
```bash
minikube start
kubectl apply -f kube
kubectl get pods --watch
minikube service knote --url
```
