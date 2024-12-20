# PIC
Tareas PIC

Aplicación Web Modular con Custom Elements
Descripción
Esta aplicación web implementa una estructura modular utilizando Custom Elements de la Web Components API. Cada componente se encapsula con Shadow DOM, asegurando aislamiento de estilos y una arquitectura escalable. Además, se emplean Templates, Slots, y APIs REST para contenido dinámico.

La aplicación incluye los siguientes componentes principales:

Header: Encabezado con un título.
Footer: Pie de página con información de copyright.
Main: Contenedor dinámico para mostrar diferentes páginas.
Menu: Menú de navegación.
SocialProfile: Página de perfil estática.
CustomTable: Tabla que carga datos desde una API REST.
Gallery: Galería de imágenes obtenidas desde una API REST.
Requisitos
Navegador web moderno con soporte para ES6 y Web Components.
Editor de texto o IDE (recomendado: Visual Studio Code).
Acceso a Internet para cargar datos desde las APIs REST.
<pre>
project/
├── components/
│   ├── header.js        
│   ├── footer.js        
│   ├── main.js          
│   ├── menu.js          
│   ├── social-profile.js
│   ├── custom-table.js  
│   └── gallery.js       
├── index.html           
</pre>

Uso
Navegación
La aplicación incluye un menú de navegación que permite acceder a diferentes secciones:

Perfil: Información estática del usuario.
Tabla: Datos dinámicos obtenidos desde una API REST.
Galería: Galería de imágenes desde una API REST.
Componentes
1. Header
Archivo: components/header.js

Define el encabezado de la página con un título estático. Utiliza estilos encapsulados dentro del Shadow DOM.

2. Footer
Archivo: components/footer.js

Muestra el pie de página con derechos de autor.

3. Main
Archivo: components/main.js

Contenedor principal que utiliza un <slot> para renderizar dinámicamente los componentes según la navegación.

4. Menu
Archivo: components/menu.js

Define un menú de navegación con enlaces a las páginas principales. Emite eventos personalizados para cambiar el contenido dinámico del contenedor principal.

5. SocialProfile
Archivo: components/social-profile.js

Muestra un perfil estático del usuario con datos básicos como nombre y correo.

6. CustomTable
Archivo: components/custom-table.js

Carga datos desde la API REST:
https://jsonplaceholder.typicode.com/users
Los datos se renderizan en una tabla con columnas de nombre, correo y ciudad.

7. Gallery
Archivo: components/gallery.js

Obtiene datos desde la API REST:
https://pokeapi.co/
Renderiza imágenes de Pokémon en formato de cuadrícula.

Código Principal
1. index.html
El punto de entrada de la aplicación. Integra los componentes y define el contenedor principal para la navegación dinámica.
<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>Aplicación Web Modular</title>
</head>
<body>
   <custom-header></custom-header>
   <custom-menu></custom-menu>
   <custom-main>
       <social-profile></social-profile>
   </custom-main>
   <custom-footer></custom-footer>

   <script src="./components/header.js"></script>
   <script src="./components/footer.js"></script>
   <script src="./components/main.js"></script>
   <script src="./components/menu.js"></script>
   <script src="./components/social-profile.js"></script>
   <script src="./components/custom-table.js"></script>
   <script src="./components/gallery.js"></script>
   <script>
       document.addEventListener('navigate', (e) => {
           const main = document.querySelector('custom-main');
           switch (e.detail) {
               case 'profile':
                   main.innerHTML = '<social-profile></social-profile>';
                   break;
               case 'table':
                   main.innerHTML = '<custom-table></custom-table>';
                   break;
               case 'gallery':
                   main.innerHTML = '<gallery-page></gallery-page>';
                   break;
           }
       });
   </script>
</body>
</html>
2. Componentes
Se puede observar los componentes JavaScript en la carpeta components/ para ver el código detallado de cada componente.

Estilo
Cada componente tiene estilos encapsulados usando Shadow DOM, lo que evita conflictos con otros elementos en la página.

APIs Utilizadas
Usuarios (Tabla):

URL: https://jsonplaceholder.typicode.com/users
Datos: Nombre, correo, ciudad.
Galería (Pokémon):

URL: https://pokeapi.co/
Datos: Imágenes y nombres de Pokémon.
Pruebas
Abre index.html en un navegador compatible.
Navega entre las secciones utilizando el menú.
Verifica:
Encabezado y pie de página estáticos.
Contenido dinámico de las secciones.
Integración de datos de las APIs.
Notas
Este proyecto está diseñado para fines educativos.
Se pueden extender los componentes o utilizar APIs adicionales según las necesidades.
Licencia
MIT License. Puedes utilizar y modificar este código libremente.
