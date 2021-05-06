
<template>
  <Layout>
<div class="mainContent" >
  <div class="fullPreview" id="capture">
    <div 
    style="display: table-cell; vertical-align: middle"
    contenteditable="true" class="picMessage">
    I am vertically aligned
  </div>
    <!-- <textarea class="picMessage" type="text" placeholder="Place your fu*cking text here"/> -->
  </div>
  <div class="thumbnails">
    <div class="thumb">

    </div>
  </div>
  <div class="controls">
    <button v-on:click="renderPic">скачать
    
    </button>
  </div>
</div>

  </Layout>
</template>

<script>
import html2canvas from 'html2canvas'

export default {
  
  methods: {
//     renderPic: function (event) {
//      html2canvas(document.querySelector("#capture"), {scale: 2}).then(i => {
//     document.body.appendChild(i);
//     var image = i.toDataURL("image/png")
//     .replace("image/png", "image/octet-stream");
// // download.setAttribute("href", image);
//     })
//   }
  renderPic: function (event) {
     html2canvas(document.querySelector("#capture"), {scale: 2}).then(i => {
    saveAs(i.toDataURL(), 'file-name.png');
    })
    function saveAs(uri, filename) {

    var link = document.createElement('a');

    if (typeof link.download === 'string') {

        link.href = uri;
        link.download = filename;

        //Firefox requires the link to be in the body
        document.body.appendChild(link);

        //simulate click
        link.click();

        //remove the link when done
        document.body.removeChild(link);

    } else {

        window.open(uri);

    }
}
  }
  }
}
</script>

<style>
.mainContent {
    display: flex;
    width: 100%;
    height: 100%;
    justify-content: center;
    flex-direction: column;
        align-items: center;

}
.picMessage{
  background: none;
    border: none;
    width: 100%;    
    white-space: normal;
    text-align-last: center;
    font-size: 42px;
    font-family: Lato;
    font-weight: bold;
}
.fullPreview {
    width: 500px;
    height: 500px;
    display: flex;
    
    align-items: center;
    background-color: wheat;
}
</style>
<style>
  @font-face {
    font-family: Lato;
    src: url('../assets/Lato-Regular.ttf');
    font-weight: normal;
  }
  @font-face {
    font-family: Lato;
    src: url('../assets/Lato-Bold.ttf');
    font-weight: Bold;
  }
  @font-face {
    font-family: Euclid;
    src: url('../assets/EuclidCircularB-Bold.otf');
    font-weight: bold;
  }
  @font-face {
    font-family: Euclid;
    src: url('../assets/EuclidCircularB-Regular.otf');
    font-weight: normal;
  }
</style>
