Boa tarde Antônio, tudo bem? Espero que sim.

Estou te enviando novamente, veja agora.

Você pode adicionar o seguinte código ao seu projeto para implementar o comportamento de arrastar e soltar (drag-and-drop) com imagens do tipo PNG:

HTML:

<!-- Criamos um container com duas colunas usando o Bootstrap -->
<div class="container">
  <div class="row">
    <div class="col-sm-6">
      <!-- Aqui criamos um card para ser o container do nosso imagem arrastável -->
      <div class="card" id="drag-container">
        <!-- Adicionamos a imagem arrastável -->
        <img class="card-img-top" id="draggable-image" src="draggable-image.png" draggable="true">
      </div>
    </div>
    <div class="col-sm-6">
      <!-- Aqui criamos outro card para ser o container onde a imagem arrastável será solta -->
      <div class="card" id="drop-container">
        <!-- Adicionamos a imagem de destino -->
        <img class="card-img-top" id="target-image" src="target-image.png">
      </div>
    </div>
  </div>
</div>
JavaScript:

// Obtemos a referência para a imagem arrastável
const draggableImage = document.getElementById("draggable-image");


// Obtemos a referência para a imagem de destino
const targetImage = document.getElementById("target-image");


// Adicionamos um evento de "dragstart" à imagem arrastável
draggableImage.addEventListener("dragstart", function (event) {
  // Quando o usuário começa a arrastar a imagem, definimos os dados a serem transferidos como o ID da imagem
  event.dataTransfer.setData("text/plain", event.target.id);
});


// Adicionamos um evento de "dragover" à imagem de destino
targetImage.addEventListener("dragover", function (event) {
  // Prevenimos a ação padrão do navegador (que é impedir o drop)
  event.preventDefault();
});


// Adicionamos um evento de "drop" à imagem de destino
targetImage.addEventListener("drop", function (event) {
  // Prevenimos a ação padrão do navegador (que é impedir o drop)
  event.preventDefault();
  
  // Obtemos os dados transferidos
  const data = event.dataTransfer.getData("text/plain");
  
  // Adicionamos a imagem arrastável como filha da imagem de destino
  event.target.appendChild(document.getElementById(data));
});
Com esse código, você pode arrastar a imagem "draggable-image" para o contêiner "drop-container", onde a imagem será colocada sobre a imagem "target-image". Além disso, você pode usar o Bootstrap para estilizar a página de acordo com as suas necessidades.
