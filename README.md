<html lang="es">
<head>
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
 <title>Identificador Avanzado de Animales</title>
 <style>
   body {
     font-family: 'Arial', sans-serif;
     margin: 0;
     padding: 0;
     background: linear-gradient(135deg, #1e3c72, #2a5298);
     color: #fff;
     text-align: center;
     overflow-x: hidden;
   }
 
   h1 {
     font-size: 2.5rem;
     margin: 0;
     padding: 20px;
     background: rgba(255, 255, 255, 0.1);
     backdrop-filter: blur(10px);
     border-radius: 10px;
     display: inline-block;
     margin-top: 20px;
     box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
   }
 
   .authors {
     font-size: 1rem;
     margin-top: 10px;
     color: rgba(255, 255, 255, 0.8);
   }
 
   nav {
     background: rgba(255, 255, 255, 0.1);
     backdrop-filter: blur(10px);
     padding: 10px 0;
     box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
     position: sticky;
     top: 0;
     z-index: 1000;
   }
 
   nav ul {
     list-style: none;
     margin: 0;
     padding: 0;
     display: flex;
     justify-content: center;
     gap: 15px;
   }
 
   nav ul li a {
     color: #fff;
     text-decoration: none;
     font-size: 1rem;
     padding: 8px 16px;
     border-radius: 20px;
     transition: all 0.3s ease;
     background: rgba(255, 255, 255, 0.1);
   }
 
   nav ul li a:hover {
     background: rgba(255, 255, 255, 0.2);
     transform: translateY(-2px);
     box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
   }
 
   .content {
     padding: 20px;
     max-width: 800px;
     margin: 0 auto;
   }
 
   .file-input {
     margin-top: 25px;
     position: relative;
     display: inline-block;
   }
 
   .file-input input[type="file"] {
     display: none;
   }
 
   .file-input label, .camera-btn {
     background: #4CAF50;
     color: #fff;
     padding: 12px 24px;
     border-radius: 25px;
     cursor: pointer;
     font-size: 0.9rem;
     transition: all 0.3s ease;
     box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
     border: none;
     display: inline-block;
     margin: 5px;
   }
 
   .file-input label:hover, .camera-btn:hover {
     background: #45a049;
     transform: translateY(-2px);
     box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2);
   }
 
   .camera-btn {
     background: #2196F3;
   }
 
   .camera-btn:hover {
     background: #0b7dda;
   }
 
   #result {
     margin-top: 25px;
     background: rgba(255, 255, 255, 0.1);
     backdrop-filter: blur(10px);
     padding: 15px;
     border-radius: 10px;
     box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
     text-align: left;
   }
 
   .animal-info {
     color: black;
     font-weight: bold;
     background: rgba(255, 255, 255, 0.8);
     padding: 4px 8px;
     border-radius: 4px;
     display: inline-block;
   }
 
   .animal-image {
     max-width: 100%;
     max-height: 200px;
     margin-top: 10px;
     border-radius: 8px;
     box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
   }
 
   .info-card {
     background: rgba(255, 255, 255, 0.15);
     padding: 12px;
     border-radius: 8px;
     margin: 8px 0;
   }
 
   .info-title {
     font-weight: bold;
     margin-bottom: 5px;
     color: #000000; /* Cambiado a negro */
     font-size: 1rem;
   }
 
   .taxonomy-grid {
     display: grid;
     grid-template-columns: repeat(2, 1fr);
     gap: 8px;
     margin-top: 8px;
   }
 
   .taxonomy-item {
     background: rgba(255, 255, 255, 0.1);
     padding: 6px;
     border-radius: 4px;
     font-size: 0.85rem;
   }
 
   @keyframes gradientAnimation {
     0% { background-position: 0% 50%; }
     50% { background-position: 100% 50%; }
     100% { background-position: 0% 50%; }
   }
 
   body {
     background: linear-gradient(135deg, #1e3c72, #2a5298, #4CAF50, #45a049);
     background-size: 400% 400%;
     animation: gradientAnimation 15s ease infinite;
   }
 
   .loader {
     border: 4px solid #f3f3f3;
     border-top: 4px solid #4CAF50;
     border-radius: 50%;
     width: 40px;
     height: 40px;
     animation: spin 1s linear infinite;
     margin: 20px auto;
   }
 
   @keyframes spin {
     0% { transform: rotate(0deg); }
     100% { transform: rotate(360deg); }
   }
 
   #cameraContainer {
     display: none;
     margin: 15px auto;
     text-align: center;
   }
 
   #cameraVideo {
     width: 100%;
     max-width: 500px;
     border-radius: 8px;
     background: #000;
   }
 
   #captureBtn {
     display: none;
     margin: 10px auto;
   }
 
   #canvas {
     display: none;
   }
 
   .error-message {
     color: #ff6b6b;
     background: rgba(255, 255, 255, 0.1);
     padding: 12px;
     border-radius: 8px;
     margin-top: 15px;
     font-size: 0.9rem;
   }
 
   .verification-panel {
     margin-top: 15px;
     padding: 12px;
     background: rgba(255, 255, 255, 0.1);
     border-radius: 8px;
     text-align: center;
   }
 
   .verification-btn {
     padding: 8px 16px;
     margin: 5px;
     border: none;
     border-radius: 20px;
     cursor: pointer;
     font-weight: bold;
     transition: all 0.3s;
     font-size: 0.85rem;
   }
 
   .verification-btn.correct {
     background: #4CAF50;
     color: white;
   }
 
   .verification-btn.incorrect {
     background: #f44336;
     color: white;
   }
 
   .alternative-results {
     margin-top: 12px;
   }
 
   .alternative-item {
     display: inline-block;
     margin: 4px;
     padding: 4px 8px;
     background: rgba(255,255,255,0.2);
     border-radius: 4px;
     cursor: pointer;
     font-size: 0.8rem;
     transition: all 0.2s;
   }
 
   .alternative-item:hover {
     background: rgba(255,255,255,0.3);
   }
 
   .confidence-bar {
     height: 4px;
     background: #ddd;
     border-radius: 4px;
     margin-top: 4px;
     overflow: hidden;
   }
 
   .confidence-level {
     height: 100%;
     background: #4CAF50;
   }
 
   .confidence {
     font-size: 0.8rem;
     color: rgba(255, 255, 255, 0.7);
     margin-top: 4px;
   }
 
   /* Nuevos estilos para la barra de progreso */
   .progress-container {
     width: 100%;
     background: rgba(255,255,255,0.1);
     border-radius: 10px;
     margin: 20px 0;
     overflow: hidden;
   }
 
   .progress-bar {
     height: 20px;
     background: linear-gradient(90deg, #4CAF50, #8BC34A);
     width: 0%;
     transition: width 0.3s ease;
     display: flex;
     align-items: center;
     justify-content: center;
     color: white;
     font-size: 0.8rem;
   }
 
   .model-loading-info {
     margin-top: 10px;
     font-size: 0.9rem;
     color: rgba(255,255,255,0.8);
   }

   /* Nuevos estilos para el buscador */
   .search-container {
     margin: 20px auto;
     max-width: 500px;
     display: flex;
     justify-content: center;
     align-items: center;
     gap: 10px;
   }

   #animalSearch {
     padding: 10px 15px;
     width: 70%;
     border-radius: 20px;
     border: none;
     font-size: 0.9rem;
     outline: none;
   }

   #searchButton {
     padding: 10px 20px;
     background: #FF9800;
   }

   #searchButton:hover {
     background: #F57C00;
   }

   .search-results {
     margin-top: 15px;
     text-align: left;
   }

   .search-item {
     padding: 8px 12px;
     margin: 5px 0;
     background: rgba(255,255,255,0.1);
     border-radius: 5px;
     cursor: pointer;
     transition: all 0.2s;
   }

   .search-item:hover {
     background: rgba(255,255,255,0.2);
   }
 
   @media (max-width: 600px) {
     h1 {
       font-size: 1.8rem;
       padding: 15px;
     }
     
     nav ul {
       flex-wrap: wrap;
       gap: 8px;
     }
     
     nav ul li a {
       padding: 6px 12px;
       font-size: 0.9rem;
     }
     
     .file-input label, .camera-btn {
       padding: 10px 20px;
       font-size: 0.85rem;
     }
 
     .progress-bar {
       height: 15px;
       font-size: 0.7rem;
     }

     .search-container {
       flex-direction: column;
     }

     #animalSearch {
       width: 100%;
     }

     #searchButton {
       width: 100%;
     }
   }
 </style>
</head>
<body>
 <nav>
   <ul>
     <li><a href="#inicio">Inicio</a></li>
     <li><a href="#acerca">Acerca de</a></li>
     <li><a href="#contacto">Contacto</a></li>
   </ul>
 </nav>
 
 <div class="content" id="inicio">
   <h1>Identificador de Animales</h1>
   <div class="authors">Por Rodrigo Mesis , Carlos Mendoza y Ariel Flores </div>
   
   <!-- Nuevo: Campo de búsqueda -->
   <div class="search-container">
     <input type="text" id="animalSearch" placeholder="Buscar animal por nombre...">
     <button id="searchButton" class="camera-btn">Buscar</button>
   </div>
   <div id="searchResults" class="search-results"></div>
   
   <div class="file-input">
     <input type="file" id="fileInput" accept="image/*">
     <label for="fileInput">Subir Imagen</label>
   </div>
   
   <button class="camera-btn" id="openCameraBtn">Abrir Cámara</button>
   
   <div id="cameraContainer">
     <video id="cameraVideo" autoplay playsinline></video>
     <button class="camera-btn" id="captureBtn">Tomar Foto</button>
     <canvas id="canvas"></canvas>
   </div>
   
   <div id="result"></div>
 </div>
 
 <div class="content" id="acerca">
   <h2>Acerca de esta aplicación</h2>
   <div class="info-card">
     <p>Esta aplicación utiliza inteligencia artificial avanzada para identificar animales en imágenes. Puedes subir una foto o tomar una con tu cámara, y nuestro sistema te proporcionará información detallada sobre el animal detectado.</p>
   </div>
 </div>
 
 <div class="content" id="contacto">
   <h2>Contacto</h2>
   <div class="info-card">
     <p>Si tienes preguntas o sugerencias, por favor contáctanos:</p>
     <p>Email: rodrigomesis69@gmail.com</p>
   </div>
 </div>
 
 <!-- Incluimos TensorFlow.js y MobileNet -->
 <script src="https://cdn.jsdelivr.net/npm/@tensorflow/tfjs@latest"></script>
 <script src="https://cdn.jsdelivr.net/npm/@tensorflow-models/mobilenet@latest"></script>
 
 <script>
   // Elementos del DOM
   const fileInput = document.getElementById('fileInput');
   const resultDiv = document.getElementById('result');
   const openCameraBtn = document.getElementById('openCameraBtn');
   const cameraContainer = document.getElementById('cameraContainer');
   const cameraVideo = document.getElementById('cameraVideo');
   const captureBtn = document.getElementById('captureBtn');
   const canvas = document.getElementById('canvas');
   const ctx = canvas.getContext('2d');
   const animalSearch = document.getElementById('animalSearch');
   const searchButton = document.getElementById('searchButton');
   const searchResults = document.getElementById('searchResults');

   // Variables de estado
   let cameraStream = null;
   let isCameraOpen = false;
   let model = null;
   let modelLoading = false;
 
   // Mapeo de nombres en inglés a español
   const animalNames = {
     "dog": "perro",
"lacewing":"camarón",
"worm": "Gusano",
"tortuga paslama":"turtoga paslama",
"earthworm": "lombriz",
"ant": "hormiga",
"caterpillar": "oruga",
"jellyfish": "medusa",
"crab": "cangrejo",
"octopus": "pulpo",
"snake": "serpiente",
"scorpion": "escorpión",
"grasshopper": "saltamontes",
"flea": "pulga",
"tick": "garrapata",
"lobster": "langosta",
"shrimp": "camarón",
"slug": "babosa",
"fiddler crab":"cangrejo",
 "jelly fish":"medusa",
    "hermit crab":"pulpo",
 "thunder snake":"lombriz",
   "golden retriever":"perro",
     "sea lion":"foca",
     "tarantula": "Araña",
     "green lizard": "iguana verde",
     "king crab": "pulpo",
     "goldfish": "pez",
     "hen": "gallina",
     "fox squirrel": "ardilla",
     "macaw": "guacamaya",
     "electric ray": "perro",
     "chesapeake bay retriever": "perro",
     "kite": "Búho",
     "wallaby": "perro",
     "snail": "caracol",
     "madagascar cat": "mapachito",
     "skunk": "zorrillo",
     "coucal": "Paloma de Castilla",
     "sea urchin": "erizo de mar",
     "magpie": "zanate",
     "squirrel monkey": "zorro cola pelada",
     "cat": "gato",
     "malinois": "pastor belga malinois",
     "bird": "pájaro",
     "boa constrictor": "culebra boa",
     "horse": "caballo",
     "fly": "mosca",
     "water buffalo": "danto o tapir",
     "loggerhead": "paslama",
     "elephant": "elefante",
     "toucan": "Tucán",
     "lion": "león",
     "sidewinder": "culebra barba amarilla",
     "tiger": "tigre",
     "bear": "oso",
     "bee eater": "guardabarranco",
     "zebra": "cebra",
     "maypole": "jirafa",
     "weasel":"raton",
     "monkey": "mono",
     "giant panda": "panda",
     "howler monkey": "mono Congo",
     "hare": "canguro",
     "armadillo": "cusuco",
     "penguin": "pingüino",
     "dolphin": "delfín",
     "whale": "ballena",
     "great white shark": "tiburón",
     "turtle": "tortuga",
     "frog": "rana"
   };
 
   // Base de datos de animales (ampliada)
   const animalDatabase = {
     "perro": {
       nombre: "Perro (Canis lupus familiaris)",
       tipo: "terrestre",
       info: "Mamífero doméstico de la familia de los cánidos. Existen más de 400 razas con características muy diversas.",
       alimentacion: "Omnívoro (adaptado a dieta doméstica, pero principalmente carnívoro).",
       clasificacion: "Mamífero",
       habitat: "Global (domesticado), originario de Eurasia.",
       caracteristicas: "Tamaño variable (desde 1 kg hasta 90 kg). Excelente olfato (10,000-100,000 veces más sensible que humanos).",
       curiosidades: "Pueden entender hasta 250 palabras y gestos. Su nariz tiene huella única como nuestras huellas digitales.",
       esperanza_vida: "10-13 años (varía por raza)",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Mammalia",
         orden: "Carnivora", familia: "Canidae", genero: "Canis",
         especie: "C. lupus familiaris"
       }
     },
     // Agregar esto dentro del objeto animalDatabase (antes del cierre })
"Gusano": {
  nombre: "Gusano (Clase Oligochaeta)",
  tipo: "terrestre",
  info: "Los gusanos son animales invertebrados de cuerpo alargado y blando, sin extremidades. Desempeñan un papel crucial en la fertilización del suelo.",
  alimentacion: "Detritívoro (materia orgánica en descomposición).",
  clasificacion: "Anélido",
  habitat: "Suelos húmedos, materia orgánica en descomposición.",
  caracteristicas: "Cuerpo cilíndrico y segmentado, carece de esqueleto, respiración cutánea.",
  curiosidades: "Algunas especies pueden regenerar partes de su cuerpo si son cortadas.",
  esperanza_vida: "1-8 años según especie",
  esqueleto: "Invertebrado",
  taxonomia: {
    reino: "Animalia", filo: "Annelida", clase: "Clitellata",
    orden: "Haplotaxida", familia: "Lumbricidae", genero: "Eisenia",
    especie: "E. fetida (ejemplo)"
  }
},
"lombriz": {
  nombre: "Lombriz de tierra (Lumbricus terrestris)",
  tipo: "terrestre",
  info: "Anélido muy beneficioso para la agricultura por su capacidad de airear y fertilizar el suelo.",
  alimentacion: "Detritívoro (hojas en descomposición y materia orgánica del suelo).",
  clasificacion: "Anélido",
  habitat: "Suelos húmedos y ricos en materia orgánica.",
  caracteristicas: "Cuerpo segmentado con anillos, moco protector, fotosensible.",
  curiosidades: "Puede consumir hasta el 90% de su peso corporal diariamente.",
  esperanza_vida: "4-8 años",
  esqueleto: "Invertebrado",
  taxonomia: {
    reino: "Animalia", filo: "Annelida", clase: "Clitellata",
    orden: "Haplotaxida", familia: "Lumbricidae", genero: "Lumbricus",
    especie: "L. terrestris"
  }
},
"hormiga": {
  nombre: "Hormiga (Familia Formicidae)",
  tipo: "terrestre",
  info: "Insectos sociales que viven en colonias organizadas con división de trabajo.",
  alimentacion: "Omnívoro (insectos, néctar, semillas, hongos).",
  clasificacion: "Insecto",
  habitat: "Prácticamente todos los ecosistemas terrestres.",
  caracteristicas: "Cuerpo dividido en cabeza, tórax y abdomen. Antenas articuladas.",
  curiosidades: "Algunas colonias pueden tener millones de individuos. Cultivan hongos para alimentarse.",
  esperanza_vida: "Semanas a años (reinas hasta 30 años)",
  esqueleto: "Invertebrado",
  taxonomia: {
    reino: "Animalia", filo: "Arthropoda", clase: "Insecta",
    orden: "Hymenoptera", familia: "Formicidae", genero: "Varía",
    especie: "Varía"
  }
},
"oruga": {
  nombre: "Oruga (Larva de Lepidoptera)",
  tipo: "terrestre",
  info: "Etapa larval de mariposas y polillas, caracterizada por su alto consumo de vegetación.",
  alimentacion: "Herbívoro (hojas, tallos, frutos).",
  clasificacion: "Insecto",
  habitat: "Plantas hospederas específicas.",
  caracteristicas: "Cuerpo segmentado con múltiples patas falsas, mandíbulas fuertes.",
  curiosidades: "Algunas producen seda para formar capullos. Muchas tienen defensas químicas.",
  esperanza_vida: "2 semanas a varios meses (según especie)",
  esqueleto: "Invertebrado",
  taxonomia: {
    reino: "Animalia", filo: "Arthropoda", clase: "Insecta",
    orden: "Lepidoptera", familia: "Varía", genero: "Varía",
    especie: "Varía"
  }
},
"medusa": {
  nombre: "Medusa (Clase Scyphozoa)",
  tipo: "acuático",
  info: "Organismos marinos gelatinosos con tentáculos urticantes, parte del plancton.",
  alimentacion: "Carnívoro (pequeños peces, zooplancton).",
  clasificacion: "Cnidario",
  habitat: "Océanos, desde superficie hasta profundidad.",
  caracteristicas: "Cuerpo gelatinoso en forma de campana con tentáculos.",
  curiosidades: "Algunas especies son bioluminiscentes. Las más venenosas pueden ser mortales.",
  esperanza_vida: "Horas a varios años (según especie)",
  esqueleto: "Invertebrado",
  taxonomia: {
    reino: "Animalia", filo: "Cnidaria", clase: "Scyphozoa",
    orden: "Semaeostomeae", familia: "Ulmaridae", genero: "Aurelia",
    especie: "A. aurita (ejemplo)"
  }
},
"cangrejo": {
  nombre: "Cangrejo (Infraorden Brachyura)",
  tipo: "acuático",
  info: "Crustáceos con caparazón duro y pinzas, adaptados a diversos ambientes acuáticos.",
  alimentacion: "Omnívoro (algas, moluscos, detritos, peces pequeños).",
  clasificacion: "Crustáceo",
  habitat: "Océanos, ríos, manglares y tierra húmeda.",
  caracteristicas: "Diez patas (dos convertidas en pinzas), caparazón ancho.",
  curiosidades: "Caminan de lado. Algunas especies pueden regenerar extremidades.",
  esperanza_vida: "3-12 años",
  esqueleto: "Invertebrado",
  taxonomia: {
    reino: "Animalia", filo: "Arthropoda", clase: "Malacostraca",
    orden: "Decapoda", familia: "Varía", genero: "Varía",
    especie: "Varía"
  }
},
"pulpo": {
  nombre: "Pulpo (Orden Octopoda)",
  tipo: "acuático",
  info: "Moluscos cefalópodos muy inteligentes con ocho brazos y gran capacidad de camuflaje.",
  alimentacion: "Carnívoro (cangrejos, moluscos, peces pequeños).",
  clasificacion: "Molusco",
  habitat: "Fondos marinos y arrecifes de coral.",
  caracteristicas: "Tres corazones, cerebro complejo, capacidad de cambiar color/textura.",
  curiosidades: "Pueden resolver puzzles y usar herramientas. Escapan de acuarios.",
  esperanza_vida: "1-5 años (la mayoría muere después de reproducirse).",
  esqueleto: "Invertebrado",
  taxonomia: {
    reino: "Animalia", filo: "Mollusca", clase: "Cephalopoda",
    orden: "Octopoda", familia: "Octopodidae", genero: "Octopus",
    especie: "O. vulgaris (ejemplo)"
  }
},
"serpiente": {
  nombre: "Serpiente (Suborden Serpentes)",
  tipo: "terrestre",
  info: "Reptiles sin patas con cuerpo alargado, algunas especies son venenosas.",
  alimentacion: "Carnívoro (roedores, aves, huevos, otros reptiles).",
  clasificacion: "Reptil",
  habitat: "Diversos: desiertos, selvas, praderas, agua.",
  caracteristicas: "Cuerpo alargado sin extremidades, lengua bífida, muda de piel.",
  curiosidades: "Algunas pueden volar planeando. Las pitones matan por constricción.",
  esperanza_vida: "10-25 años según especie",
  esqueleto: "Vertebrado",
  taxonomia: {
    reino: "Animalia", filo: "Chordata", clase: "Reptilia",
    orden: "Squamata", familia: "Varía", genero: "Varía",
    especie: "Varía"
  }
},
"escorpión": {
  nombre: "Escorpión (Orden Scorpiones)",
  tipo: "terrestre",
  info: "Artrópodos con pinzas y cola venenosa, principalmente nocturnos.",
  alimentacion: "Carnívoro (insectos, arañas, pequeños vertebrados).",
  clasificacion: "Arácnido",
  habitat: "Desiertos, bosques tropicales, zonas rocosas.",
  caracteristicas: "Ocho patas, pinzas delanteras, aguijón venenoso en cola.",
  curiosidades: "Fluorescen bajo luz UV. Sólo 25 de 1500 especies son peligrosas para humanos.",
  esperanza_vida: "2-10 años",
  esqueleto: "Invertebrado",
  taxonomia: {
    reino: "Animalia", filo: "Arthropoda", clase: "Arachnida",
    orden: "Scorpiones", familia: "Varía", genero: "Varía",
    especie: "Varía"
  }
},
"saltamontes": {
  nombre: "Saltamontes (Suborden Caelifera)",
  tipo: "terrestre",
  info: "Insectos herbívoros con potentes patas traseras para saltar.",
  alimentacion: "Herbívoro (hojas, pasto, cultivos).",
  clasificacion: "Insecto",
  habitat: "Praderas, campos agrícolas, zonas herbáceas.",
  caracteristicas: "Patas traseras largas para saltar, antenas cortas, alas en adultos.",
  curiosidades: "Algunas especies forman plagas devastadoras (langostas). Producen sonido frotando patas.",
  esperanza_vida: "1-2 años",
  esqueleto: "Invertebrado",
  taxonomia: {
    reino: "Animalia", filo: "Arthropoda", clase: "Insecta",
    orden: "Orthoptera", familia: "Acrididae", genero: "Schistocerca",
    especie: "S. americana (ejemplo)"
  }
},
"pulga": {
  nombre: "Pulga (Orden Siphonaptera)",
  tipo: "terrestre",
  info: "Pequeños insectos parásitos sin alas que se alimentan de sangre.",
  alimentacion: "Hematófago (sangre de mamíferos y aves).",
  clasificacion: "Insecto",
  habitat: "Pelaje/plumas de hospederos, alfombras, camas.",
  caracteristicas: "Cuerpo comprimido lateralmente, patas traseras adaptadas para saltar.",
  curiosidades: "Pueden saltar hasta 200 veces su longitud. Transmiten enfermedades como peste bubónica.",
  esperanza_vida: "2-3 meses",
  esqueleto: "Invertebrado",
  taxonomia: {
    reino: "Animalia", filo: "Arthropoda", clase: "Insecta",
    orden: "Siphonaptera", familia: "Pulicidae", genero: "Pulex",
    especie: "P. irritans (pulga humana)"
  }
},
"garrapata": {
  nombre: "Garrapata (Orden Ixodida)",
  tipo: "terrestre",
  info: "Arácnidos parásitos que se alimentan de sangre y transmiten enfermedades.",
  alimentacion: "Hematófago (sangre de mamíferos, aves, reptiles).",
  clasificacion: "Arácnido",
  habitat: "Hierba alta, arbustos, esperando hospederos.",
  caracteristicas: "Cuerpo plano antes de alimentarse, se hincha con sangre.",
  curiosidades: "Algunas pueden transmitir Lyme, babesiosis y otras enfermedades graves.",
  esperanza_vida: "Meses a 3 años según especie",
  esqueleto: "Invertebrado",
  taxonomia: {
    reino: "Animalia", filo: "Arthropoda", clase: "Arachnida",
    orden: "Ixodida", familia: "Ixodidae", genero: "Ixodes",
    especie: "I. scapularis (ejemplo)"
  }
},
"langosta": {
  nombre: "Langosta (Familia Nephropidae)",
  tipo: "acuático",
  info: "Crustáceos marinos grandes y valiosos comercialmente, con pinzas poderosas.",
  alimentacion: "Omnívoro (moluscos, algas, detritos, peces pequeños).",
  clasificacion: "Crustáceo",
  habitat: "Fondos marinos rocosos o arenosos.",
  caracteristicas: "Pinzas grandes (una trituradora y otra cortadora), antenas largas.",
  curiosidades: "Pueden vivir hasta 100 años. Migran en filas por el fondo marino.",
  esperanza_vida: "50-100 años",
  esqueleto: "Invertebrado",
  taxonomia: {
    reino: "Animalia", filo: "Arthropoda", clase: "Malacostraca",
    orden: "Decapoda", familia: "Nephropidae", genero: "Homarus",
    especie: "H. americanus (langosta americana)"
  }
},
"camarón": {
  nombre: "Camarón (Infraorden Caridea)",
  tipo: "acuático",
  info: "Crustáceos decápodos de pequeño tamaño, importantes en cadenas alimenticias acuáticas.",
  alimentacion: "Omnívoro (algas, detritos, pequeños invertebrados).",
  clasificacion: "Crustáceo",
  habitat: "Océanos, estuarios, algunos en agua dulce.",
  caracteristicas: "Cuerpo alargado, antenas largas, abdomen desarrollado.",
  curiosidades: "Algunas especies limpian parásitos de peces. Pueden hacer ruido chasqueando sus pinzas.",
  esperanza_vida: "1-6 años",
  esqueleto: "Invertebrado",
  taxonomia: {
    reino: "Animalia", filo: "Arthropoda", clase: "Malacostraca",
    orden: "Decapoda", familia: "Palaemonidae", genero: "Macrobrachium",
    especie: "M. rosenbergii (ejemplo)"
  }
},
"babosa": {
  nombre: "Babosa (Orden Pulmonata)",
  tipo: "terrestre",
  info: "Moluscos gasterópodos sin concha externa, parientes terrestres de los caracoles.",
  alimentacion: "Herbívoro (hojas, hongos, frutas en descomposición).",
  clasificacion: "Molusco",
  habitat: "Ambientes húmedos: jardines, bosques, bajo piedras.",
  caracteristicas: "Cuerpo blando y alargado, moco protector, tentáculos retráctiles.",
  curiosidades: "Producen un moco que dificulta su captura por depredadores. Algunas son venenosas.",
  esperanza_vida: "1-6 años",
  esqueleto: "Invertebrado",
  taxonomia: {
    reino: "Animalia", filo: "Mollusca", clase: "Gastropoda",
    orden: "Pulmonata", familia: "Limacidae", genero: "Limax",
    especie: "L. maximus (babosa grande)"
  }
},
     "foca": {
    nombre: "Foca (Familia Phocidae)",
    tipo: "acuático",
    info: "Mamíferos marinos adaptados a la vida acuática. Existen 33 especies de focas verdaderas, principalmente en regiones polares.",
    alimentacion: "Carnívoro (peces, calamares, crustáceos).",
    clasificacion: "Mamífero",
    habitat: "Océanos, especialmente en zonas frías del Ártico y Antártida.",
    caracteristicas: "Cuerpo hidrodinámico, extremidades en forma de aletas, gruesa capa de grasa. Sin orejas externas.",
    curiosidades: "Pueden contener la respiración hasta 2 horas. Las crías nacen con pelaje blanco llamado 'lanugo'.",
    esperanza_vida: "20-30 años (dependiendo de la especie)",
    esqueleto: "Vertebrado",
    taxonomia: {
        reino: "Animalia",
        filo: "Chordata",
        clase: "Mammalia",
        orden: "Carnivora",
        familia: "Phocidae",
        genero: "Varía",
        especie: "Varía"
    }
},
     "iguana verde": {
       nombre: "Iguana Verde (Iguana iguana)",
       tipo: "terrestre",
       info: "Reptil arbóreo de gran tamaño, conocido por su coloración verde brillante y cresta dorsal.",
       alimentacion: "Herbívoro (hojas, flores, frutas). Los juveniles pueden comer insectos.",
       clasificacion: "Reptil",
       habitat: "Selvas tropicales de Centroamérica, Sudamérica y el Caribe.",
       caracteristicas: "Puede medir hasta 2 metros, excelente nadadora, cambia de color según temperatura.",
       curiosidades: "Pueden caer de 15 metros sin lastimarse, su cola se regenera si se corta.",
       esperanza_vida: "10-15 años en libertad (hasta 20 en cautiverio).",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Reptilia",
         orden: "Squamata", familia: "Iguanidae", genero: "Iguana",
         especie: "I. iguana"
       }
     },
     "erizo de mar": {
       nombre: "Erizo de Mar (Clase: Echinoidea)",
       tipo: "acuático",
       info: "Equinodermo marino con caparazón globular cubierto de espinas móviles.",
       alimentacion: "Herbívoro (algas) y detritívoro.",
       clasificacion: "Equinodermo",
       habitat: "Fondos marinos rocosos y arrecifes de coral.",
       caracteristicas: "Cuerpo con simetría pentarradial, posee aparato masticador llamado 'linterna de Aristóteles'.",
       curiosidades: "Sus huevos son un manjar gastronómico, algunas especies viven más de 100 años.",
       esperanza_vida: "30-100 años según especie.",
       esqueleto: "Invertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Echinodermata", clase: "Echinoidea",
         orden: "Varía", familia: "Varía", genero: "Varía",
         especie: "Varía"
       }
     },
     "Búho": {
       nombre: "Búho (Orden Strigiformes)",
       tipo: "aéreo",
       info: "Aves rapaces nocturnas con visión binocular y vuelo silencioso.",
       alimentacion: "Pequeños mamíferos, insectos y otras aves (carnívoro).",
       clasificacion: "Ave",
       habitat: "Bosques, zonas rurales y urbanas con árboles.",
       caracteristicas: "Ojos frontales grandes, cabeza giratoria (270°), plumaje camuflado.",
       curiosidades: "Pueden girar la cabeza casi completamente gracias a vértebras especiales.",
       esperanza_vida: "10-25 años según especie.",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Aves",
         orden: "Strigiformes", familia: "Strigidae/Tytonidae", genero: "Bubo, Tyto, etc.",
         especie: "Ej: Bubo bubo (búho real)"
       }
     },
     "Araña": {
       nombre: "Araña (Orden Araneae)",
       tipo: "terrestre",
       info: "Artrópodos depredadores con ocho patas y capacidad para producir seda. Existen más de 48,000 especies.",
       alimentacion: "Carnívoro (insectos, pequeños vertebrados y otras arañas). Algunas son parasitoides.",
       clasificacion: "Artrópodo",
       habitat: "Todos los continentes excepto la Antártida. Desde desiertos hasta bosques y hogares humanos.",
       caracteristicas: "Ocho patas articuladas y quelíceros con veneno, producen seda mediante hileras, visión múltiple (ojos simples), exoesqueleto de quitina.",
       curiosidades: "La tela de araña dorada (Nephila) es más resistente que el Kevlar. Algunas especies pueden caminar sobre el agua. Las tarántulas usan pelos urticantes como defensa.",
       esperanza_vida: "1 año (la mayoría) hasta 25 años (tarántulas)",
       esqueleto: "Invertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Arthropoda", clase: "Arachnida",
         orden: "Araneae", familia: "Varía", genero: "Varía",
         especie: "Varía"
       }
     },
     "gallina": {
       nombre: "Gallina (Gallus gallus domesticus)",
       tipo: "terrestre",
       info: "Ave doméstica descendiente del gallo bancivo (Gallus gallus).",
       alimentacion: "Omnívoro (granos, insectos, vegetales).",
       clasificacion: "Ave",
       habitat: "Granjas y corrales en todo el mundo.",
       caracteristicas: "Pico corto, cresta roja (en machos), patas escamosas.",
       curiosidades: "Pueden recordar hasta 100 rostros de su especie.",
       esperanza_vida: "5-10 años.",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Aves",
         orden: "Galliformes", familia: "Phasianidae", genero: "Gallus",
         especie: "G. gallus domesticus"
       }
     },
     "pez": {
       nombre: "Pez (Superclase Osteichthyes/Chondrichthyes)",
       tipo: "acuático",
       info: "Vertebrados acuáticos con branquias y aletas. Miles de especies.",
       alimentacion: "Varía (herbívoros, carnívoros, omnívoros).",
       clasificacion: "Pez",
       habitat: "Agua dulce y salada en todo el planeta.",
       caracteristicas: "Escamas, vejiga natatoria (en la mayoría), sangre fría.",
       curiosidades: "Algunas especies cambian de sexo según el ambiente.",
       esperanza_vida: "Desde semanas (killifish) hasta 200 años (tiburón de Groenlandia).",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Depende",
         orden: "Varía", familia: "Varía", genero: "Varía",
         especie: "Varía"
       }
     },
     "pulpo": {
       nombre: "Pulpo (Orden Octopoda)",
       tipo: "acuático",
       info: "Molusco cefalópodo con 8 tentáculos y alta inteligencia.",
       alimentacion: "Carnívoro (cangrejos, moluscos, peces pequeños).",
       clasificacion: "Molusco",
       habitat: "Fondos marinos y arrecifes de coral.",
       caracteristicas: "Tres corazones, sangre azul (hemocianina), camuflaje instantáneo.",
       curiosidades: "Pueden resolver puzzles y usar herramientas como cocos para protegerse.",
       esperanza_vida: "1-5 años (la mayoría muere después de reproducirse).",
       esqueleto: "Invertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Mollusca", clase: "Cephalopoda",
         orden: "Octopoda", familia: "Octopodidae", genero: "Octopus, Enteroctopus, etc.",
         especie: "Ej: Octopus vulgaris"
       }
     },
     "guacamaya": {
       nombre: "Guacamaya (Género Ara)",
       tipo: "aéreo",
       info: "Aves exóticas de colores vibrantes, nativas de las selvas tropicales de América. Pertenecen a la familia de los loros.",
       alimentacion: "Frutas, semillas, nueces e insectos.",
       clasificacion: "Ave",
       habitat: "Selvas tropicales y bosques húmedos de América Central y del Sur.",
       caracteristicas: "Plumaje colorido (rojo, azul, amarillo), pico fuerte, sonidos estridentes y capacidad de imitar palabras.",
       curiosidades: "Viven hasta 60 años en cautiverio. En peligro por deforestación y tráfico ilegal.",
       esperanza_vida: "30-50 años (hasta 60 en cautiverio).",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Aves",
         orden: "Psittaciformes", familia: "Psittacidae", genero: "Ara",
         especie: "Depende de la variedad (ej: A. macao, A. ararauna)"
       }
     },
     "ardilla": {
       nombre: "Ardilla (Familia Sciuridae)",
       tipo: "terrestre",
       info: "Pequeños roedores ágiles conocidos por su cola peluda y hábitos de almacenar nueces.",
       alimentacion: "Nueces, semillas, frutas, brotes e insectos (omnívoro oportunista).",
       clasificacion: "Mamífero",
       habitat: "Bosques, parques urbanos y zonas arboladas (en casi todo el mundo).",
       caracteristicas: "Dientes frontales afilados, cola tupida para equilibrio, patas traseras fuertes para saltar.",
       curiosidades: "Pueden enterrar miles de nueces al año y olvidar algunas, ayudando a plantar árboles.",
       esperanza_vida: "5-10 años en libertad (hasta 15 en cautiverio).",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Mammalia",
         orden: "Rodentia", familia: "Sciuridae", genero: "Sciurus",
         especie: "Varía (ej: S. vulgaris, ardilla roja)"
       }
     },
     "mapachito": {
       nombre: "Mapachito (Procyon lotor)",
       tipo: "terrestre",
       info: "El mapachito, también conocido como mapache, es un mamífero inteligente y curioso, reconocido por su habilidad para manipular objetos con sus patas delanteras.",
       alimentacion: "Omnívoro (frutas, insectos, pequeños animales y basura).",
       clasificacion: "Mamífero",
       habitat: "Bosques, áreas urbanas y suburbanas.",
       caracteristicas: "Tamaño mediano. Pelaje grisáceo con una máscara facial negra y cola anillada.",
       curiosidades: "Los mapaches son conocidos por lavar su comida antes de comerla.",
       esperanza_vida: "2-3 años en estado salvaje, hasta 20 años en cautiverio.",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Mammalia",
         orden: "Carnivora", familia: "Procyonidae", genero: "Procyon",
         especie: "P. lotor"
       }
     },
     "zorrillo": {
       nombre: "Zorrillo (Mephitis mephitis)",
       tipo: "terrestre",
       info: "El zorrillo, también conocido como mofeta, es un mamífero conocido por su habilidad para rociar un líquido maloliente como mecanismo de defensa.",
       alimentacion: "Omnívoro (insectos, pequeños mamíferos, frutas y vegetales).",
       clasificacion: "Mamífero",
       habitat: "Bosques, praderas y áreas suburbanas.",
       caracteristicas: "Tamaño mediano. Pelaje negro con rayas blancas características.",
       curiosidades: "El líquido que rocía el zorrillo puede alcanzar hasta 3 metros de distancia.",
       esperanza_vida: "2-4 años en estado salvaje, hasta 10 años en cautiverio.",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Mammalia",
         orden: "Carnivora", familia: "Mephitidae", genero: "Mephitis",
         especie: "M. mephitis"
       }
     },
     "Paloma de Castilla": {
       nombre: "Paloma de Castilla (Columba livia)",
       tipo: "aéreo",
       info: "La paloma de Castilla, también conocida como paloma bravía, es una especie de ave muy común en áreas urbanas y rurales. Es originaria de Europa, pero se ha extendido por todo el mundo.",
       alimentacion: "Omnívoro (semillas, granos, frutas, insectos y restos de comida).",
       clasificacion: "Ave",
       habitat: "Ciudades, campos, acantilados y áreas rurales.",
       caracteristicas: "Tamaño mediano. Cuerpo robusto, plumaje grisáceo con reflejos verdes y morados en el cuello.",
       curiosidades: "Las palomas de Castilla son excelentes voladoras y pueden orientarse para regresar a su lugar de origen desde grandes distancias.",
       esperanza_vida: "3-5 años en estado salvaje, hasta 15 años en cautiverio.",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Aves",
         orden: "Columbiformes", familia: "Columbidae", genero: "Columba",
         especie: "C. livia"
       }
     },
     "caracol": {
       nombre: "Caracol (Clase Gastropoda)",
       tipo: "terrestre",
       info: "Los caracoles son moluscos gasterópodos conocidos por su concha espiralada y su movimiento lento. Son animales invertebrados que habitan en una variedad de entornos, desde jardines hasta ambientes acuáticos.",
       alimentacion: "Herbívoro (hojas, frutas, hongos, algas) y algunos son omnívoros o carroñeros.",
       clasificacion: "Molusco",
       habitat: "Terrestres, de agua dulce y marinos. Comunes en jardines, bosques, ríos y océanos.",
       caracteristicas: "Tamaño pequeño a mediano. Cuerpo blando protegido por una concha espiralada. Se desplazan mediante un pie musculoso y dejan un rastro de baba.",
       curiosidades: "Los caracoles pueden hibernar durante el invierno o en épocas de sequía, sellando la entrada de su concha con una capa de mucosidad llamada opérculo. Algunas especies son hermafroditas.",
       esperanza_vida: "2-5 años (dependiendo de la especie).",
       esqueleto: "Invertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Mollusca", clase: "Gastropoda",
         orden: "Varía", familia: "Varía", genero: "Varía",
         especie: "Varía"
       }
     },
     "Tucán": {
       nombre: "Tucán (Familia Ramphastidae)",
       tipo: "aéreo",
       info: "El tucán es un ave tropical conocida por su pico grande y colorido. Habita en las selvas de América Central y del Sur.",
       alimentacion: "Omnívoro (frutas, insectos, pequeños reptiles y huevos de otras aves).",
       clasificacion: "Ave",
       habitat: "Selvas tropicales y bosques húmedos.",
       caracteristicas: "Tamaño mediano. Pico grande y colorido, plumaje brillante y cola corta.",
       curiosidades: "El pico del tucán, aunque parece pesado, es ligero debido a su estructura porosa.",
       esperanza_vida: "15-20 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Aves",
         orden: "Piciformes", familia: "Ramphastidae", genero: "Ramphastos",
         especie: "R. toco (Tucán toco), R. sulfuratus (Tucán pico iris)"
       }
     },
     "raton": {
       nombre: "raton (Mus musculus)",
       tipo: "terrestre",
       info: "El ratón es un pequeño mamífero roedor conocido por su presencia en casi todo el mundo. Es un animal muy adaptable y se encuentra tanto en entornos urbanos como rurales.",
       alimentacion: "Omnívoro (semillas, frutas, insectos, restos de comida).",
       clasificacion: "Mamífero",
       habitat: "Campos, bosques, áreas urbanas y rurales.",
       caracteristicas: "Tamaño pequeño. Cuerpo cubierto de pelaje corto, orejas grandes y cola larga.",
       curiosidades: "Los ratones tienen un sentido del olfato muy desarrollado y son capaces de reproducirse rápidamente.",
       esperanza_vida: "1-3 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Mammalia",
         orden: "Rodentia", familia: "Muridae", genero: "Mus",
         especie: "M. musculus"
       }
     },
     "danto o tapir": {
       nombre: "Danto (Tapir)",
       tipo: "terrestre",
       info: "El danto, también conocido como tapir, es un mamífero herbívoro que habita en bosques y selvas de América Central, América del Sur y el sudeste asiático. Es un animal solitario y de hábitos nocturnos.",
       alimentacion: "Herbívoro (hojas, frutas, brotes y ramas).",
       clasificacion: "Mamífero",
       habitat: "Bosques tropicales, selvas y áreas cercanas a ríos.",
       caracteristicas: "Tamaño grande. Cuerpo robusto con una trompa corta y flexible. Pelaje corto y oscuro.",
       curiosidades: "Los tapires son excelentes nadadores y pueden sumergirse en el agua para escapar de depredadores.",
       esperanza_vida: "25-30 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Mammalia",
         orden: "Perissodactyla", familia: "Tapiridae", genero: "Tapirus",
         especie: "T. bairdii (Tapir centroamericano), T. terrestris (Tapir sudamericano)"
       }
     },
     "zorro cola pelada": {
       nombre: "Zorro Cola Pelada (Cerdocyon thous)",
       tipo: "terrestre",
       info: "El zorro cola pelada, también conocido como zorro cangrejero, es un cánido nativo de América del Sur. Es un animal omnívoro y muy adaptable.",
       alimentacion: "Omnívoro (frutas, insectos, pequeños mamíferos, cangrejos).",
       clasificacion: "Mamífero",
       habitat: "Bosques, sabanas, zonas pantanosas y áreas cercanas a ríos.",
       caracteristicas: "Tamaño mediano. Pelaje grisáceo o marrón con manchas oscuras. Cola larga y peluda.",
       curiosidades: "Es conocido por su habilidad para cazar cangrejos y otros animales acuáticos.",
       esperanza_vida: "10-12 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Mammalia",
         orden: "Carnivora", familia: "Canidae", genero: "Cerdocyon",
         especie: "C. thous"
       }
     },
     "zanate": {
       nombre: "Zanate (Quiscalus mexicanus)",
       tipo: "aéreo",
       info: "El zanate, o zanate mayor, es un ave de la familia de los ictéridos conocida por su plumaje negro brillante y su cola larga y ahorquillada. Es común en áreas urbanas y rurales de América Central y del Norte.",
       alimentacion: "Omnívoro (insectos, frutas, semillas, pequeños vertebrados, desechos humanos).",
       clasificacion: "Ave",
       habitat: "Áreas urbanas, campos agrícolas, bosques abiertos y cercanías de cuerpos de agua.",
       caracteristicas: "Tamaño mediano. Plumaje negro iridiscente con reflejos azulados o verdosos. Cola larga y ahorquillada.",
       curiosidades: "Los zanates son aves muy sociales y ruidosas, que a menudo forman grandes bandadas. Además, son conocidos por su habilidad para imitar sonidos, incluyendo el canto de otras aves.",
       esperanza_vida: "8-12 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Aves",
         orden: "Passeriformes", familia: "Icteridae", genero: "Quiscalus",
         especie: "Q. mexicanus"
       }
     },
    
     "gato": {
       nombre: "Gato (Felis catus)",
       tipo: "terrestre",
       info: "Los gatos son animales ágiles y curiosos. Tienen una flexibilidad increíble y pueden saltar hasta 6 veces su longitud corporal.",
       alimentacion: "Carnívoro (carne, pescado).",
       clasificacion: "Mamífero",
       habitat: "Doméstico y salvaje.",
       caracteristicas: "Tamaño pequeño a mediano. Excelente visión nocturna.",
       curiosidades: "Los gatos pasan el 70% de su vida durmiendo.",
       esperanza_vida: "12-15 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Mammalia",
         orden: "Carnivora", familia: "Felidae", genero: "Felis",
         especie: "F. catus"
       }
     },
     "pastor belga malinois": {
       nombre: "Pastor Belga Malinois (Canis lupus familiaris)",
       tipo: "terrestre",
       info: "El Pastor Belga Malinois es una raza de perro conocida por su inteligencia y habilidades en trabajos de protección y rescate.",
       alimentacion: "Omnívoro (carne, vegetales, alimentos procesados).",
       clasificacion: "Mamífero",
       habitat: "Doméstico.",
       caracteristicas: "Tamaño mediano. Muy activo y trabajador.",
       curiosidades: "Es una de las razas más utilizadas en fuerzas policiales y militares.",
       esperanza_vida: "12-14 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Mammalia",
         orden: "Carnivora", familia: "Canidae", genero: "Canis",
         especie: "C. lupus familiaris"
       }
     },
     "pájaro": {
       nombre: "Pájaro (Orden Passeriformes)",
       tipo: "aéreo",
       info: "Los pájaros son animales voladores conocidos por su diversidad de especies y cantos.",
       alimentacion: "Omnívoro (semillas, insectos, frutas).",
       clasificacion: "Ave",
       habitat: "Bosques, ciudades, montañas.",
       caracteristicas: "Tamaño pequeño. Capacidad de vuelo.",
       curiosidades: "Algunas especies pueden imitar sonidos humanos.",
       esperanza_vida: "5-10 años (dependiendo de la especie).",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Aves",
         orden: "Passeriformes", familia: "Varía", genero: "Varía",
         especie: "Varía"
       }
     },
     "culebra boa": {
       nombre: "Culebra Boa (Boa constrictor)",
       tipo: "terrestre",
       info: "La culebra boa, o boa constrictor, es una serpiente no venenosa conocida por su método de caza: envuelve a sus presas con su cuerpo y las asfixia. Es una de las serpientes más grandes y emblemáticas de América.",
       alimentacion: "Carnívoro (pequeños mamíferos, aves, lagartijas).",
       clasificacion: "Reptil",
       habitat: "Bosques tropicales, sabanas y áreas cercanas a ríos en América Central y del Sur.",
       caracteristicas: "Tamaño grande. Cuerpo musculoso y pesado, con patrones de coloración variables (marrón, gris, rojizo).",
       curiosidades: "Las boas pueden tragar presas enteras que son más grandes que su cabeza gracias a su mandíbula flexible. Además, son excelentes nadadoras.",
       esperanza_vida: "20-30 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Reptilia",
         orden: "Squamata", familia: "Boidae", genero: "Boa",
         especie: "B. constrictor"
       }
     },
     "caballo": {
       nombre: "Caballo (Equus ferus caballus)",
       tipo: "terrestre",
       info: "Los caballos son animales fuertes y veloces, utilizados históricamente para transporte y trabajo.",
       alimentacion: "Herbívoro (hierba, heno, granos).",
       clasificacion: "Mamífero",
       habitat: "Praderas, granjas.",
       caracteristicas: "Patas largas y fuertes.",
       curiosidades: "Los caballos pueden dormir tanto de pie como acostados.",
       esperanza_vida: "25-30 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Mammalia",
         orden: "Perissodactyla", familia: "Equidae", genero: "Equus",
         especie: "E. ferus caballus"
       }
     },
     "mosca": {
       nombre: "Mosca (Orden Diptera)",
       tipo: "aéreo",
       info: "Las moscas son insectos pertenecientes al orden Diptera, conocidos por su presencia en casi todos los hábitats del mundo. Son importantes en los ecosistemas como descomponedores, pero también pueden ser vectores de enfermedades.",
       alimentacion: "Omnívoro (materia orgánica en descomposición, néctar, sangre, heces).",
       clasificacion: "Insecto",
       habitat: "Prácticamente en todos los hábitats, especialmente en áreas con materia orgánica en descomposición.",
       caracteristicas: "Tamaño pequeño. Cuerpo dividido en cabeza, tórax y abdomen. Dos alas funcionales y un par de halteres (estructuras para equilibrio).",
       curiosidades: "Las moscas tienen un ciclo de vida corto, que incluye huevo, larva (gusano), pupa y adulto. Algunas especies, como la mosca doméstica, pueden transmitir enfermedades como el cólera y la disentería.",
       esperanza_vida: "15-30 días (dependiendo de la especie y las condiciones ambientales).",
       esqueleto: "Invertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Arthropoda", clase: "Insecta",
         orden: "Diptera", familia: "Varía", genero: "Varía",
         especie: "Varía"
       }
     },
     "paslama": {
       nombre: "Tortuga Paslama (Lepidochelys olivacea)",
       tipo: "acuático",
       info: "La tortuga paslama, o tortuga golfina, es una especie de tortuga marina conocida por sus arribadas masivas durante la época de anidación, donde miles de hembras llegan a las playas para poner sus huevos. Es una especie en peligro de extinción debido a la caza furtiva y la pérdida de hábitat.",
       alimentacion: "Omnívoro (medusas, crustáceos, moluscos, algas).",
       clasificacion: "Reptil",
       habitat: "Océanos tropicales y subtropicales, playas de anidación en costas del Pacífico y el Índico.",
       caracteristicas: "Tamaño mediano. Caparazón ovalado y aplanado de color verde oliva. Aletas adaptadas para nadar.",
       curiosidades: "Las tortugas paslama son conocidas por sus arribadas masivas, donde miles de hembras llegan a la misma playa para anidar. Esto ocurre principalmente en playas de Costa Rica, India, México y Nicaragua.",
       esperanza_vida: "50-60 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Reptilia",
         orden: "Testudines", familia: "Cheloniidae", genero: "Lepidochelys",
         especie: "L. olivacea"
       }
     },
     "elefante": {
       nombre: "Elefante (Loxodonta africana)",
       tipo: "terrestre",
       info: "Los elefantes son los animales terrestres más grandes del mundo, conocidos por su inteligencia y memoria.",
       alimentacion: "Herbívoro (hojas, frutas, corteza).",
       clasificacion: "Mamífero",
       habitat: "Sabanas, bosques.",
       caracteristicas: "Tamaño enorme. Trompa larga y colmillos.",
       curiosidades: "Los elefantes pueden vivir hasta 70 años.",
       esperanza_vida: "60-70 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Mammalia",
         orden: "Proboscidea", familia: "Elephantidae", genero: "Loxodonta",
         especie: "L. africana"
       }
     },
     "león": {
       nombre: "León (Panthera leo)",
       tipo: "terrestre",
       info: "El león es conocido como el 'rey de la selva' y es un depredador dominante en su hábitat.",
       alimentacion: "Carnívoro (carne de caza).",
       clasificacion: "Mamífero",
       habitat: "Sabanas, praderas.",
       caracteristicas: "Tamaño grande. Melena en los machos.",
       curiosidades: "Los leones pueden dormir hasta 20 horas al día.",
       esperanza_vida: "10-14 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Mammalia",
         orden: "Carnivora", familia: "Felidae", genero: "Panthera",
         especie: "P. leo"
       }
     },
     "culebra barba amarilla": {
       nombre: "Culebra Barba Amarilla (Bothrops asper)",
       tipo: "terrestre",
       info: "La culebra barba amarilla, también conocida como terciopelo o Bothrops asper, es una serpiente venenosa muy peligrosa que habita en América Central y del Sur. Es responsable de la mayoría de las mordeduras de serpiente en su área de distribución.",
       alimentacion: "Carnívoro (pequeños mamíferos, aves, lagartijas, anfibios).",
       clasificacion: "Reptil",
       habitat: "Bosques tropicales, áreas cercanas a ríos y zonas agrícolas en América Central y del Sur.",
       caracteristicas: "Tamaño mediano a grande. Cuerpo robusto, cabeza triangular y coloración variable (marrón, gris, verde) con marcas oscuras.",
       curiosidades: "La culebra barba amarilla es una de las serpientes más temidas debido a su veneno hemotóxico, que puede causar necrosis y daño tisular. Es una especie vivípara, lo que significa que da a luz crías vivas en lugar de poner huevos.",
       esperanza_vida: "15-20 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Reptilia",
         orden: "Squamata", familia: "Viperidae", genero: "Bothrops",
         especie: "B. asper"
       }
     },
     "tigre": {
       nombre: "Tigre (Panthera tigris)",
       tipo: "terrestre",
       info: "El tigre es el felino más grande del mundo y es un cazador solitario.",
       alimentacion: "Carnívoro (carne de caza).",
       clasificacion: "Mamífero",
       habitat: "Bosques, selvas.",
       caracteristicas: "Tamaño grande. Rayas únicas en su pelaje.",
       curiosidades: "Los tigres pueden nadar largas distancias.",
       esperanza_vida: "10-15 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Mammalia",
         orden: "Carnivora", familia: "Felidae", genero: "Panthera",
         especie: "P. tigris"
       }
     },
     "oso": {
       nombre: "Oso (Ursus arctos)",
       tipo: "terrestre",
       info: "Los osos son mamíferos grandes y fuertes, conocidos por su hibernación en invierno.",
       alimentacion: "Omnívoro (carne, pescado, frutas, miel).",
       clasificacion: "Mamífero",
       habitat: "Bosques, montañas.",
       caracteristicas: "Tamaño grande. Pelaje grueso.",
       curiosidades: "Los osos pueden correr a velocidades de hasta 50 km/h.",
       esperanza_vida: "20-30 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Mammalia",
         orden: "Carnivora", familia: "Ursidae", genero: "Ursus",
         especie: "U. arctos"
       }
     },
     "guardabarranco": {
       nombre: "Guardabarranco (Eumomota superciliosa)",
       tipo: "aéreo",
       info: "El Guardabarranco es un ave colorida y emblemática de Nicaragua, conocida por su cola larga y su canto melodioso.",
       alimentacion: "Omnívoro (insectos, frutas, pequeños reptiles).",
       clasificacion: "Ave",
       habitat: "Bosques tropicales, zonas montañosas.",
       caracteristicas: "Tamaño pequeño a mediano. Plumaje colorido y cola larga.",
       curiosidades: "El Guardabarranco es el ave nacional de Nicaragua.",
       esperanza_vida: "5-10 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Aves",
         orden: "Coraciiformes", familia: "Momotidae", genero: "Eumomota",
         especie: "E. superciliosa"
       }
     },
     "cebra": {
       nombre: "Cebra (Equus quagga)",
       tipo: "terrestre",
       info: "Las cebras son animales conocidos por sus rayas blancas y negras, que son únicas en cada individuo.",
       alimentacion: "Herbívoro (hierba, hojas).",
       clasificacion: "Mamífero",
       habitat: "Sabanas, praderas.",
       caracteristicas: "Tamaño mediano. Rayas distintivas.",
       curiosidades: "Las rayas de las cebras ayudan a confundir a los depredadores.",
       esperanza_vida: "25-30 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Mammalia",
         orden: "Perissodactyla", familia: "Equidae", genero: "Equus",
         especie: "E. quagga"
       }
     },
     "jirafa": {
       nombre: "Jirafa (Giraffa camelopardalis)",
       tipo: "terrestre",
       info: "La jirafa es el animal más alto del mundo, conocido por su largo cuello y patas.",
       alimentacion: "Herbívoro (hojas de árboles altos).",
       clasificacion: "Mamífero",
       habitat: "Sabanas, bosques abiertos.",
       caracteristicas: "Tamaño muy alto. Cuello largo.",
       curiosidades: "Las jirafas solo necesitan dormir entre 10 minutos y 2 horas al día.",
       esperanza_vida: "25-30 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Mammalia",
         orden: "Artiodactyla", familia: "Giraffidae", genero: "Giraffa",
         especie: "G. camelopardalis"
       }
     },
     "mono": {
       nombre: "Mono (Orden Primates)",
       tipo: "terrestre",
       info: "Los monos son primates inteligentes y sociales, conocidos por su agilidad y comportamiento juguetón.",
       alimentacion: "Omnívoro (frutas, insectos, hojas).",
       clasificacion: "Mamífero",
       habitat: "Bosques, selvas.",
       caracteristicas: "Tamaño pequeño a mediano. Cola larga (en algunas especies).",
       curiosidades: "Algunos monos pueden usar herramientas para obtener comida.",
       esperanza_vida: "20-30 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Mammalia",
         orden: "Primates", familia: "Cercopithecidae", genero: "Macaca",
         especie: "M. mulatta"
       }
     },
     "panda": {
       nombre: "Panda (Ailuropoda melanoleuca)",
       tipo: "terrestre",
       info: "El panda es un animal tranquilo y solitario, conocido por su amor al bambú.",
       alimentacion: "Herbívoro (bambú).",
       clasificacion: "Mamífero",
       habitat: "Bosques de bambú.",
       caracteristicas: "Tamaño mediano. Pelaje blanco y negro.",
       curiosidades: "Los pandas pasan hasta 14 horas al día comiendo bambú.",
       esperanza_vida: "20 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Mammalia",
         orden: "Carnivora", familia: "Ursidae", genero: "Ailuropoda",
         especie: "A. melanoleuca"
       }
     },
     "mono Congo": {
       nombre: "mono congo (Cercopithecus neglectus)",
       tipo: "terrestre",
       info: "El mono Congo, también conocido como mono de Brazza, es un primate tímido y reservado que habita en los bosques de África Central. Es conocido por su distintiva barba blanca y su comportamiento cauteloso.",
       alimentacion: "Omnívoro (frutas, hojas, insectos, pequeños vertebrados).",
       clasificacion: "Mamífero",
       habitat: "Bosques tropicales, pantanos y áreas cercanas a ríos en África Central.",
       caracteristicas: "Tamaño mediano. Pelaje grisáceo con una barba blanca distintiva y una cola larga.",
       curiosidades: "El mono Congo es uno de los primates más sigilosos y difíciles de observar en la naturaleza debido a su comportamiento reservado.",
       esperanza_vida: "20-30 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Mammalia",
         orden: "Primates", familia: "Cercopithecidae", genero: "Cercopithecus",
         especie: "C. neglectus"
       }
     },
     "canguro": {
       nombre: "Canguro (Macropus giganteus)",
       tipo: "terrestre",
       info: "El canguro es un marsupial conocido por sus poderosas patas traseras y su bolsa marsupial.",
       alimentacion: "Herbívoro (hierba, hojas).",
       clasificacion: "Mamífero",
       habitat: "Praderas, bosques abiertos.",
       caracteristicas: "Tamaño mediano a grande. Patas traseras fuertes.",
       curiosidades: "Los canguros pueden saltar hasta 3 veces su altura.",
       esperanza_vida: "8-12 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Mammalia",
         orden: "Diprotodontia", familia: "Macropodidae", genero: "Macropus",
         especie: "M. giganteus"
       }
     },
     "cusuco": {
       nombre: "cusuco (Dasypus novemcinctus)",
       tipo: "terrestre",
       info: "El cusuco, o armadillo de nueve bandas, es un mamífero conocido por su caparazón óseo que le sirve como protección. Es un animal excavador que se encuentra en América, desde el sur de Estados Unidos hasta Argentina.",
       alimentacion: "Omnívoro (insectos, larvas, frutas, pequeños vertebrados).",
       clasificacion: "Mamífero",
       habitat: "Bosques, praderas, zonas semiáridas y áreas cercanas a ríos.",
       caracteristicas: "Tamaño mediano. Caparazón duro y segmentado, patas cortas y fuertes para excavar.",
       curiosidades: "Los cusucos pueden rodarse en una bola para protegerse de los depredadores. Además, son los únicos mamíferos que pueden contraer la lepra.",
       esperanza_vida: "12-15 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Mammalia",
         orden: "Cingulata", familia: "Dasypodidae", genero: "Dasypus",
         especie: "D. novemcinctus"
       }
     },
     "pingüino": {
       nombre: "Pingüino (Aptenodytes forsteri)",
       tipo: "acuático",
       info: "Los pingüinos son aves no voladoras que viven en climas fríos y son excelentes nadadores.",
       alimentacion: "Carnívoro (peces, calamares).",
       clasificacion: "Ave",
       habitat: "Regiones polares.",
       caracteristicas: "Tamaño pequeño a mediano. Plumaje denso y resistente al agua.",
       curiosidades: "Los pingüinos pueden nadar a velocidades de hasta 36 km/h.",
       esperanza_vida: "15-20 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Aves",
         orden: "Sphenisciformes", familia: "Spheniscidae", genero: "Aptenodytes",
         especie: "A. forsteri"
       }
     },
     "delfín": {
       nombre: "Delfín (che Tursiops truncatus)",
       tipo: "acuático",
       info: "Los delfines son mamíferos marinos inteligentes y sociales, conocidos por su comportamiento juguetón.",
       alimentacion: "Carnívoro (peces, calamares).",
       clasificacion: "Mamífero",
       habitat: "Océanos, mares.",
       caracteristicas: "Tamaño mediano. Cuerpo aerodinámico.",
       curiosidades: "Los delfines pueden reconocerse en espejos, lo que indica autoconciencia.",
       esperanza_vida: "40-60 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Mammalia",
         orden: "Cetacea", familia: "Delphinidae", genero: "Tursiops",
         especie: "T. truncatus"
       }
     },
     "ballena": {
       nombre: "Ballena (Balaenoptera musculus)",
       tipo: "acuático",
       info: "Las ballenas son los animales más grandes del planeta, conocidas por sus impresionantes cantos submarinos.",
       alimentacion: "Carnívoro (plancton, peces pequeños).",
       clasificacion: "Mamífero",
       habitat: "Océanos.",
       caracteristicas: "Tamaño enorme. Cuerpo alargado y aletas grandes.",
       curiosidades: "Las ballenas azules pueden medir hasta 30 metros de largo.",
       esperanza_vida: "70-90 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Mammalia",
         orden: "Cetacea", familia: "Balaenopteridae", genero: "Balaenoptera",
         especie: "B. musculus"
       }
     },
     "tiburón": {
       nombre: "Tiburón (Carcharodon carcharias)",
       tipo: "acuático",
       info: "Los tiburones son depredadores marinos conocidos por su agilidad y sentidos agudos.",
       alimentacion: "Carnívoro (peces, mamíferos marinos).",
       clasificacion: "Pez",
       habitat: "Océanos, mares.",
       caracteristicas: "Tamaño variable. Aletas grandes y dientes afilados.",
       curiosidades: "Los tiburones tienen un sexto sentido que les permite detectar campos eléctricos en el agua.",
       esperanza_vida: "20-30 años",
       esqueleto: "Cartilaginoso",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Chondrichthyes",
         orden: "Lamniformes", familia: "Lamnidae", genero: "Carcharodon",
         especie: "C. carcharias"
       }
     },
     "tortuga": {
       nombre: "Tortuga (Chelonoidis nigra)",
       tipo: "acuático",
       info: "Las tortugas son reptiles conocidos por su caparazón protector y su longevidad.",
       alimentacion: "Omnívoro (plantas, insectos, peces).",
       clasificacion: "Reptil",
       habitat: "Océanos, ríos, tierra.",
       caracteristicas: "Tamaño pequeño a grande. Caparazón duro.",
       curiosidades: "Algunas tortugas pueden vivir más de 100 años.",
       esperanza_vida: "50-100 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Reptilia",
         orden: "Testudines", familia: "Testudinidae", genero: "Chelonoidis",
         especie: "C. nigra"
       }
     },
     "rana": {
       nombre: "Rana (Rana temporaria)",
       tipo: "acuático",
       info: "Las ranas son anfibios conocidos por su capacidad de saltar y su piel húmeda.",
       alimentacion: "Carnívoro (insectos, pequeños animales).",
       clasificacion: "Anfibio",
       habitat: "Charcas, ríos, bosques.",
       caracteristicas: "Tamaño pequeño. Piel húmeda y resbaladiza.",
       curiosidades: "Las ranas pueden respirar a través de su piel.",
       esperanza_vida: "5-10 años",
       esqueleto: "Vertebrado",
       taxonomia: {
         reino: "Animalia", filo: "Chordata", clase: "Amphibia",
         orden: "Anura", familia: "Ranidae", genero: "Rana",
         especie: "R. temporaria"
       }
     }
   };
 
   // Función para mostrar carga con barra de progreso
   function showLoader(message = "Analizando imagen...") {
     resultDiv.innerHTML = `
       <div class="loader"></div>
       <div class="info-card">${message}</div>
     `;
   }
 
   // Función para mostrar el progreso de carga del modelo
   function showModelLoadingProgress(progress) {
     const percent = Math.round(progress * 100);
     resultDiv.innerHTML = `
       <div class="info-card">
         <h3 class="info-title">Cargando modelo de IA...</h3>
         <p>Descargando componentes necesarios (${percent}%)</p>
         <div class="progress-container">
           <div class="progress-bar" style="width: ${percent}%">${percent}%</div>
         </div>
         <p class="model-loading-info">Este proceso solo ocurre la primera vez o después de actualizaciones.</p>
       </div>
     `;
   }
 
   // Función para mostrar error
   function showError(message) {
     resultDiv.innerHTML = `
       <div class="error-message">
         ${message}
         <button class="camera-btn" onclick="window.location.reload()" style="margin-top:10px">Reintentar</button>
       </div>
     `;
   }
 
   // Función para cargar el modelo con progreso
   async function loadModelWithProgress() {
     if (model) return model;
     if (modelLoading) {
       showModelLoadingProgress(0.5);
       return;
     }
 
     modelLoading = true;
     
     try {
       // Mostramos progreso inicial
       showModelLoadingProgress(0);
       
       // Creamos un observador de progreso personalizado
       const progressMonitor = {
         percent: 0,
         update: function(p) {
           this.percent = p;
           showModelLoadingProgress(p);
         }
       };
       
       // Simulamos progreso mientras se carga el modelo real
       const progressInterval = setInterval(() => {
         if (progressMonitor.percent < 0.9) {
           progressMonitor.update(progressMonitor.percent + 0.05);
         }
       }, 300);
       
       // Cargamos el modelo real
       model = await mobilenet.load({
         version: 2,
         alpha: 0.5,
         onProgress: (fraction) => {
           // Actualizamos progreso real cuando esté disponible
           progressMonitor.update(Math.max(fraction, progressMonitor.percent));
         }
       });
       
       clearInterval(progressInterval);
       progressMonitor.update(1);
       
       // Pequeña pausa para mostrar el 100%
       await new Promise(resolve => setTimeout(resolve, 500));
       
       modelLoading = false;
       return model;
     } catch (error) {
       clearInterval(progressInterval);
       modelLoading = false;
       showError(`Error al cargar el modelo: ${error.message}`);
       console.error("Error loading model:", error);
       throw error;
     }
   }
 
   // Función para clasificar imagen con TensorFlow.js
   async function classifyImage(imageElement) {
     try {
       if (!model) {
         await loadModelWithProgress();
       }
       
       showLoader();
       const predictions = await model.classify(imageElement);
       
       return {
         predictions: predictions.map(pred => ({
           label: pred.className.split(',')[0],
           score: pred.probability,
           type: getAnimalType(pred.className)
         }))
       };
     } catch (error) {
       showError("Error al analizar la imagen. Intenta nuevamente.");
       console.error("Classification error:", error);
       return { predictions: [] };
     }
   }
 
   // Función para determinar el tipo de animal
   function getAnimalType(label) {
     const lowerLabel = label.toLowerCase();
     
     if (lowerLabel.includes('acuático') || lowerLabel.includes('pez') || lowerLabel.includes('delfín') || lowerLabel.includes('ballena') || lowerLabel.includes('pulpo') || lowerLabel.includes('medusa') || lowerLabel.includes('tiburón') || lowerLabel.includes('tortuga') || lowerLabel.includes('rana')) {
       return "acuático";
     }
     if (lowerLabel.includes('ave') || lowerLabel.includes('pájaro') || lowerLabel.includes('águila') || lowerLabel.includes('loro') || lowerLabel.includes('pingüino') || lowerLabel.includes('mariposa') || lowerLabel.includes('guacamaya') || lowerLabel.includes('zanate') || lowerLabel.includes('guardabarranco') || lowerLabel.includes('paloma')) {
       return "aéreo";
     }
     if (lowerLabel.includes('terrestre') || lowerLabel.includes('mamífero') || lowerLabel.includes('perro') || lowerLabel.includes('gato') || lowerLabel.includes('elefante') || lowerLabel.includes('tigre') || lowerLabel.includes('jirafa') || lowerLabel.includes('oso') || lowerLabel.includes('león') || lowerLabel.includes('cebra') || lowerLabel.includes('rinoceronte') || lowerLabel.includes('panda') || lowerLabel.includes('hormiga') || lowerLabel.includes('tarántula') || lowerLabel.includes('camaleón') || lowerLabel.includes('mapachito') || lowerLabel.includes('zorrillo') || lowerLabel.includes('ardilla') || lowerLabel.includes('ratón') || lowerLabel.includes('cusuco') || lowerLabel.includes('mono')) {
       return "terrestre";
     }
     
     return "desconocido";
   }
 
   // Función para obtener información del animal
   function getAnimalInfo(animalName, tipo, confianza) {
     // Buscar coincidencia exacta o parcial en la base de datos
     const lowerName = animalName.toLowerCase();
     let bestMatch = null;
     let bestScore = 0;
     
     // Primero intentamos traducir el nombre del animal
     const translatedName = animalNames[lowerName] || lowerName;
     
     for (const [key, info] of Object.entries(animalDatabase)) {
       const score = calculateMatchScore(translatedName, key.toLowerCase());
       if (score > bestScore) {
         bestScore = score;
         bestMatch = { ...info, nombre: info.nombre.replace(/\(.*?\)/, `(${animalName})`) };
       }
     }
     
     if (bestMatch) {
       bestMatch.confianza = parseFloat(confianza) || 0;
       return bestMatch;
     }
     
     // Si no se encuentra en la base de datos
     return {
       nombre: animalName,
       tipo: tipo || "desconocido",
       info: "Información no disponible para este animal.",
       alimentacion: "Desconocida.",
       clasificacion: "Desconocida.",
       habitat: "Desconocido.",
       caracteristicas: "Desconocidas.",
       curiosidades: "Desconocidas.",
       esperanza_vida: "Desconocida.",
       esqueleto: "Desconocido",
       taxonomia: {
         reino: "Desconocido", filo: "Desconocido", clase: "Desconocido",
         orden: "Desconocido", familia: "Desconocido", genero: "Desconocido",
         especie: "Desconocido"
       },
       confianza: parseFloat(confianza) || 0
     };
   }
 
   // Función para calcular coincidencia entre nombres
   function calculateMatchScore(input, reference) {
     if (input === reference) return 1.0;
     if (reference.includes(input)) return 0.8;
     if (input.includes(reference)) return 0.7;
     
     const inputWords = input.split(' ');
     const referenceWords = reference.split(' ');
     const matches = inputWords.filter(word =>
       referenceWords.some(refWord => refWord.includes(word) || word.includes(refWord))
     );
     
     return matches.length / Math.max(inputWords.length, referenceWords.length);
   }
 
   // Función para mostrar resultados
   function displayResults(result, imageSrc) {
     if (!result.predictions || result.predictions.length === 0) {
       showError("No se pudo identificar ningún animal en la imagen. Intenta con una foto más clara.");
       return;
     }

     const primary = result.predictions[0];
     const animalInfo = getAnimalInfo(primary.label, primary.type, primary.score);
     
     let html = `
       <div class="info-card">
<p>Animal detectado: <span class="animal-info">${animalInfo.nombre.split(' (')[0]}</span></p>
         <p>Tipo: <span class="animal-info">${animalInfo.tipo}</span></p>
       </p>
         ${imageSrc ? `<img src="${imageSrc}" alt="${animalInfo.nombre}" class="animal-image">` : ''}
       </div>
       
       <div class="info-card">
         <div class="info-title">📝 Información general</div>
         <p>${animalInfo.info}</p>
       </div>
       
       <div class="info-card">
         <div class="info-title">🍽️ Alimentación</div>
         <p>${animalInfo.alimentacion}</p>
       </div>
       
       <div class="info-card">
         <div class="info-title">🏡 Hábitat</div>
         <p>${animalInfo.habitat}</p>
       </div>
       
       <div class="info-card">
         <div class="info-title">🔍 Características</div>
         <p>${animalInfo.caracteristicas}</p>
       </div>
       
       <div class="info-card">
         <div class="info-title">🧐 Datos curiosos</div>
         <p>${animalInfo.curiosidades}</p>
       </div>
       
       <div class="info-card">
         <div class="info-title">⏳ Esperanza de vida</div>
         <p>${animalInfo.esperanza_vida}</p>
       </div>
       
       <div class="info-card">
         <div class="info-title">🦴 Esqueleto</div>
         <p>${animalInfo.esqueleto}</p>
       </div>
       
       <div class="info-card">
         <div class="info-title">📊 Taxonomía</div>
         <div class="taxonomy-grid">
           <div class="taxonomy-item">Reino: ${animalInfo.taxonomia.reino}</div>
           <div class="taxonomy-item">Filo: ${animalInfo.taxonomia.filo}</div>
           <div class="taxonomy-item">Clase: ${animalInfo.taxonomia.clase}</div>
           <div class="taxonomy-item">Orden: ${animalInfo.taxonomia.orden}</div>
           <div class="taxonomy-item">Familia: ${animalInfo.taxonomia.familia}</div>
           <div class="taxonomy-item">Género: ${animalInfo.taxonomia.genero}</div>
           <div class="taxonomy-item">Especie: ${animalInfo.taxonomia.especie}</div>
         </div>
       </div>
       
       <div class="verification-panel">
         <p>¿Es correcta esta identificación?</p>
         <button class="verification-btn correct">Sí, es correcto</button>
         <button class="verification-btn incorrect">No, es incorrecto</button>
       </div>
     `;
     
     // Añadir alternativas si existen
     if (result.predictions.length > 1) {
       html += `
         <div class="info-card alternative-results">
           <div class="info-title">Otras posibilidades:</div>
           ${result.predictions.slice(1, 4).map(pred => `
             <div class="alternative-item">
               ${pred.label} (${(pred.score * 100).toFixed(1)}%)
             </div>
           `).join('')}
         </div>
       `;
     }
     
     resultDiv.innerHTML = html;
     
     // Manejar eventos de los botones
     document.querySelector('.verification-btn.correct')?.addEventListener('click', () => {
       alert('¡Gracias por confirmar! Esto nos ayuda a mejorar.');
     });
     
     document.querySelector('.verification-btn.incorrect')?.addEventListener('click', () => {
       const userInput = prompt("¿Qué animal es realmente?");
       if (userInput) {
         alert(`Gracias por confirmar! Esto nos ayuda a mejorar.') ${userInput}.`);
       }
     });
     
     // Manejar clic en alternativas
     document.querySelectorAll('.alternative-item').forEach(item => {
       item.addEventListener('click', () => {
         const label = item.textContent.split(' (')[0];
         const prediction = result.predictions.find(p => p.label === label);
         if (prediction) {
           const animalInfo = getAnimalInfo(prediction.label, prediction.type, prediction.score);
           displayResults({ predictions: [prediction, ...result.predictions.filter(p => p !== prediction)] }, imageSrc);
         }
       });
     });
   }

   // Función para buscar animal por nombre
   function searchAnimalByName(name) {
     const lowerName = name.toLowerCase().trim();
     if (!lowerName) return;
     
     // Buscar coincidencias exactas primero
     let matches = [];
     
     // 1. Buscar en nombres traducidos
     for (const [engName, espName] of Object.entries(animalNames)) {
       if (espName.toLowerCase() === lowerName) {
         const animalData = animalDatabase[espName] || animalDatabase[engName.toLowerCase()];
         if (animalData) {
           matches.push({
             name: espName,
             data: animalData,
             score: 1.0
           });
         }
       }
     }
     
     // 2. Buscar en la base de datos directamente
     for (const [key, info] of Object.entries(animalDatabase)) {
       const score = calculateMatchScore(lowerName, key.toLowerCase());
       if (score > 0.3) { // Umbral mínimo de coincidencia
         matches.push({
           name: key,
           data: info,
           score: score
         });
       }
     }
     
     // Ordenar por mejor coincidencia
     matches.sort((a, b) => b.score - a.score);
     
     // Mostrar resultados
     if (matches.length > 0) {
       // Mostrar el mejor resultado directamente
       displayAnimalInfo(matches[0].data);
       
       // Mostrar otras coincidencias como sugerencias
       if (matches.length > 1) {
         searchResults.innerHTML = `
           <div class="info-card">
             <div class="info-title">Otras coincidencias:</div>
             ${matches.slice(1, 4).map(match => `
               <div class="search-item" onclick="displayAnimalInfo(${JSON.stringify(match.data).replace(/"/g, '&quot;')}">
                 ${match.name} (${(match.score * 100).toFixed(0)}% coincidencia)
               </div>
             `).join('')}
           </div>
         `;
       } else {
         searchResults.innerHTML = '';
       }
     } else {
       showError("No se encontró información sobre ese animal. Intenta con otro nombre.");
       searchResults.innerHTML = '';
     }
   }
   
   // Función para mostrar información de un animal (sin imagen)
   function displayAnimalInfo(animalInfo) {
     displayResults({
       predictions: [{
         label: animalInfo.nombre.split(' (')[0],
         probability: 1.0,
         type: animalInfo.tipo
       }]
     }, null);
   }

   // Manejar subida de archivo
   fileInput.addEventListener('change', async (e) => {
     const file = e.target.files[0];
     if (!file) return;
     
     const img = new Image();
     img.src = URL.createObjectURL(file);
     
     img.onload = async () => {
       try {
         canvas.width = img.width;
         canvas.height = img.height;
         ctx.drawImage(img, 0, 0, canvas.width, canvas.height);
         
         const result = await classifyImage(img);
         displayResults(result, img.src);
       } catch (error) {
         showError(`Error al procesar la imagen: ${error.message}`);
       }
     };
     
     img.onerror = () => {
       showError('Error al cargar la imagen. Por favor, intenta con otra.');
     };
   });
 
   // Manejar cámara
   openCameraBtn.addEventListener('click', async () => {
     if (isCameraOpen) {
       cameraStream.getTracks().forEach(track => track.stop());
       cameraContainer.style.display = 'none';
       captureBtn.style.display = 'none';
       openCameraBtn.textContent = 'Abrir Cámara';
       isCameraOpen = false;
       return;
     }
     
     try {
       cameraStream = await navigator.mediaDevices.getUserMedia({
         video: {
           facingMode: 'environment',
           width: { ideal: 1280 },
           height: { ideal: 720 }
         }
       });
       
       cameraVideo.srcObject = cameraStream;
       cameraContainer.style.display = 'block';
       captureBtn.style.display = 'block';
       openCameraBtn.textContent = 'Cerrar Cámara';
       isCameraOpen = true;
     } catch (err) {
       showError(`No se pudo acceder a la cámara: ${err.message}`);
     }
   });
 
   // Capturar foto
   captureBtn.addEventListener('click', async () => {
     if (!cameraStream) return;
     
     try {
       canvas.width = cameraVideo.videoWidth;
       canvas.height = cameraVideo.videoHeight;
       ctx.drawImage(cameraVideo, 0, 0, canvas.width, canvas.height);
       
       const img = new Image();
       img.src = canvas.toDataURL('image/jpeg');
       
       img.onload = async () => {
         const result = await classifyImage(img);
         displayResults(result, img.src);
       };
     } catch (error) {
       showError(`Error al capturar la imagen: ${error.message}`);
     }
   });

   // Manejar búsqueda por nombre
   searchButton.addEventListener('click', () => {
     searchAnimalByName(animalSearch.value);
   });

   // Permitir búsqueda al presionar Enter
   animalSearch.addEventListener('keypress', (e) => {
     if (e.key === 'Enter') {
       searchAnimalByName(animalSearch.value);
     }
   });
 
   // Inicialización
   async function init() {
     if (!navigator.mediaDevices?.getUserMedia) {
       openCameraBtn.style.display = 'none';
     }
     
     // Precargar el modelo en segundo plano
     setTimeout(loadModelWithProgress, 1000);
   }
 
   window.addEventListener('DOMContentLoaded', init);

   // Hacer la función displayAnimalInfo accesible desde los elementos del DOM
   window.displayAnimalInfo = displayAnimalInfo;
 </script>
</body>
</html>
