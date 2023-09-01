<template>
  <v-container class="d-flex justify-center">

    <v-card max-height="300px" min-height="225px" height="auto" width="300px" class="mx-1" outlined
      style="overflow: hidden; position: relative;">

      <div v-if="isCameraOpen" class="d-flex">
        <video v-show="!isPhotoTaken" ref="camera" autoplay style="width:100%;object-fit: cover;"></video>
      </div>
      <div class="camera-button" v-else @click="toggleCamera">
        <button type="button" class="button is-rounded"
          :class="{ 'is-primary' : !isCameraOpen, 'is-danger' : isCameraOpen}" style="width: 100%;height: 100%;">
          <div v-if="!isCameraOpen">

          </div>
        </button>
      </div>

    </v-card>

    <v-card max-width="600px" outlined>
      <v-card-text>
        <div id="content_activar_screen">
          <h4>Iniciando el capturador de pantalla</h4>
          <p>Sistema para capturar la pantalla de su ordenador. </p>
          <ul>
            <li color="success">Asegúrese de que no se registre ningún dato personal o privado. Se recomienda tener abierta la ventana
              del examen únicamente.</li>
            <li>Salvo excepciones no podrá salir de la ventana del examen hasta que lo termine.</li>
            <li>Cuando salga de la ventana se mostrará una alerta que se comunicará al supervisor.</li>
          </ul>
        </div>
      </v-card-text>
      <v-card-actions class="d-flex justify-center">
        <v-btn depressed>
          Iniciar
        </v-btn>
      </v-card-actions>
    </v-card>

  </v-container>
</template>

<script>

export default{
    data() {
    return {
      isCameraOpen: false,
      isPhotoTaken: false,
      isShotPhoto: false,
      isLoading: false,
      link: '#'
    }
  },
  
  methods: {
    toggleCamera() {
      if(this.isCameraOpen) {
        this.isCameraOpen = false;
        this.isPhotoTaken = false;
        this.isShotPhoto = false;
        this.stopCameraStream();
      } else {
        this.isCameraOpen = true;
        this.createCameraElement();
      }
    },
    
    createCameraElement() {
      this.isLoading = true;
      
      const constraints = (window.constraints = {
				audio: false,
				video: true
			});


			navigator.mediaDevices
				.getUserMedia(constraints)
				.then(stream => {
          this.isLoading = false;
					this.$refs.camera.srcObject = stream;
				})
				.catch(error => {
          this.isLoading = false;
					alert("May the browser didn't support or there is some errors." + error);
				});
    },
    
    stopCameraStream() {
      let tracks = this.$refs.camera.srcObject.getTracks();

			tracks.forEach(track => {
				track.stop();
			});
    },
    
    takePhoto() {
      if(!this.isPhotoTaken) {
        this.isShotPhoto = true;

        const FLASH_TIMEOUT = 50;

        setTimeout(() => {
          this.isShotPhoto = false;
        }, FLASH_TIMEOUT);
      }
      
      this.isPhotoTaken = !this.isPhotoTaken;
      
      const context = this.$refs.canvas.getContext('2d');
      context.drawImage(this.$refs.camera, 0, 0, 450, 337.5);
    },
    
    downloadImage() {
      const download = document.getElementById("downloadPhoto");
      const canvas = document.getElementById("photoTaken").toDataURL("image/jpeg")
    .replace("image/jpeg", "image/octet-stream");
      download.setAttribute("href", canvas);
    }
  }
}

</script>

<style>
.camera-button{
  width: 100%;
  height: 100%;
  position: absolute;
}
</style>