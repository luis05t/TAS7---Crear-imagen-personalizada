# Contenerización de Aplicación React con Backend simulado usando Docker

---

## 1. Título  
**Implementación de una aplicación React con backend simulado mediante Docker y Dockerfile**

---

## 2. Tiempo de duración  
La práctica se completó en aproximadamente **50 minutos**.

---

## 3. Fundamentos  
En esta práctica se contenerizaron dos aplicaciones utilizando Docker:

- **React Frontend** (`suda-frontend-s6`): Aplicación creada con Vite, encargada de la interfaz de usuario.  
- **mockAPI**: Backend simulado que proporciona endpoints REST para el funcionamiento del frontend.

El frontend se empaquetó mediante un `Dockerfile` que genera un entorno productivo con NGINX.  
El backend simulado se ejecutó localmente como una aplicación Node.js.

### Conceptos clave  
- **Dockerfile**: Archivo que contiene instrucciones para construir una imagen de Docker.  
- **Imagen Docker**: Instantánea de una aplicación con sus dependencias y configuración.  
- **Contenedor Docker**: Instancia ejecutable de una imagen.  
- **Vite**: Herramienta de desarrollo para React que optimiza el tiempo de carga.  
- **NGINX**: Servidor web utilizado para servir archivos estáticos del frontend.

---

## 4. Conocimientos previos  
- Uso básico de Docker (comandos `build`, `run`, `images`, etc.).  
- Fundamentos de React y Node.js.  
- Comprensión de HTTP y APIs REST.  
- Edición de archivos Dockerfile.

---

## 5. Objetivos a alcanzar  
1. Clonar el repositorio `suda-frontend-s6`.  
2. Ejecutar el frontend y verificar su funcionamiento local.  
3. Crear un `Dockerfile` que empaquete la app React para producción.  
4. Construir la imagen Docker.  
5. Ejecutar el contenedor con el frontend.  
6. Ejecutar el backend simulado desde `mockAPI`.

---

## 6. Equipo necesario  
- Sistema operativo windows  
- Docker ≥ 20.10 instalado.  
- Node.js ≥ 18.x y npm.  
- Navegador web (Chrome, Firefox, etc.).  
- Conexión a internet.

---

## 7. Material de apoyo  
- **Docker Docs**: https://docs.docker.com/  
- **Node.js**: https://nodejs.org/  
- **React (Vite)**: https://vitejs.dev/  
- **NGINX Docs**: https://nginx.org/en/docs/  
- **Repositorio Frontend**: https://github.com/Daviddotcoms/suda-frontend-s6  
- **Repositorio Backend simulado**: https://github.com/Daviddotcoms/mockAPI

---

## 8. Procedimiento  

### Parte 1: Clonar los repositorios

```
git clone https://github.com/Daviddotcoms/suda-frontend-s6.git
git clone https://github.com/Daviddotcoms/mockAPI.git
```

#### Parte 2: Verificar funcionamiento del frontend
```
cd suda-frontend-s6
npm install
npm run dev

```

#### Parte 3: Ejecutar backend simulado
```
cd mockAPI
npm install
npm start

```

#### Parte 4: Crear archivo Dockerfile para el frontend
- Ubicado en suda-frontend-s6/Dockerfile:
```
FROM node:18-alpine AS build
WORKDIR /app
COPY . .
RUN npm install
RUN npm run build

FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

```
#### Parte 5: Construir imagen Docker
```
cd suda-frontend-s6
docker build -t suda-frontend .

```
#### #### Parte 6: Construir imagen Docker
```
docker run -d -p 8080:80 --name suda-frontend suda-frontend

```

## 9. Resultados esperados
A continuación se presentan las evidencias visuales del correcto funcionamiento de la contenerización:

* El contenedor del frontend se ejecuta correctamente en el puerto 8080 mediante NGINX:

![Termina](./Imagenes/1.PNG)

* La aplicación React (suda-frontend-s6) carga exitosamente y accede al backend simulado:

![Termina](./Imagenes/2.PNG)

* El backend simulado (mockAPI) se encuentra activo en el puerto 3000:

![Termina](./Imagenes/3.PNG)

* Y al final se puede ver la imgen creada.

![Termina](./Imagenes/4.PNG)
### 10. Audio
Link: https://voca.ro/17E1VR8WprBK 
### 11 Bibliografia
- Docker Documentation. (2025). https://docs.docker.com/

- Vite Official Docs. (2025). https://vitejs.dev/

- Node.js Documentation. (2025). https://nodejs.org/en/docs

- NGINX Docs. (2025). https://nginx.org/en/docs/

- Repositorio frontend: https://github.com/Daviddotcoms/suda-frontend-s6

- Repositorio mockAPI: https://github.com/Daviddotcoms/mockAPI
