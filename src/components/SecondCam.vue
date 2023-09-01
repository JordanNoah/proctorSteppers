<template>
    <v-container>
        <v-row justify="center">
            <v-col cols="9" class="d-flex">
                <canvas id="canvas"></canvas>
                <div class="mx-12">
                    <div id="content_activar_mobile">
                        <h4>Activar la segunda cámara</h4>
                        <p>Siga estos pasos para activar la cámara del teléfono:</p>
                        <ul>
                            <li>Capture el código QR con su teléfono. <a id="configurar_permisos" target="new">¿Cómo capturar el
                                    código QR?</a></li>
                            <li>Su teléfono le solicitará permisos para compartir la cámara, debe aceptarlos.</li>
                            <li>En cuanto aparezca la imagen, enfoque el teléfono de forma que se vean el escritorio. Cuando
                                esté listo pulse el botón para continuar.</li>
                        </ul>
                        <div></div>
                    </div>
                </div>
            </v-col>
        </v-row>
    </v-container>
</template>
  
  <script>
  import QRCode from "qrcode";
  
  export default {
    data() {
      return {
        text: "Escribe aquí el texto para el código QR",
      };
    },
    mounted: function() {
        var canvas = document.getElementById('canvas')
        QRCode.toCanvas(canvas, "un texto para el qrcode", (error) => {
          if (error) console.error(error);
          console.log("Código QR generado con éxito.");
        });
    },
  };
  </script>
  
  <style>

#canvas{
    width: 200px!important;
    height: 200px!important;
}
</style>