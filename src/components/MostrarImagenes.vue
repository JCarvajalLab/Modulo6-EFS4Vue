<template>
<h1>Galeria</h1>
    <div class="gallery-container">
        <div class="image-gallery">
        <div class="scroll-container" @scroll="handleScroll">
            <div
            v-for="(photo, index) in visiblePhotos"
            :key="index"
            class="image-item"
            @click="selectPhoto(photo)"
            >
            <img :src="photo.url" :alt="photo.description" />
            </div>
        </div>
        </div>

        <MostrarDetalles
        v-if="selectedPhoto"
        :photo="selectedPhoto"
        @close="selectedPhoto = null"
        class="details"
        />
    </div>
</template>


<script>
import MostrarDetalles from '@/components/MostrarDetalles.vue'

export default{
        components: {
            MostrarDetalles,
    },
    data(){
        return{
            photos: [
                {url: 'https://picsum.photos/200/300', description: ' Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Curabitur pretium tincidunt lacus, ut laoreet eros blandit a.', author:"autor 1"},
                {url: 'https://picsum.photos/id/28/200/300', description: ' Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla facilisi. Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam. Eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit.', author:"autor 2"},
                { url: 'https://picsum.photos/id/25/200/300', description: ' Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin gravida nibh vel velit auctor aliquet. Aenean sollicitudin, lorem quis bibendum auctor, nisi elit consequat ipsum, nec sagittis sem nibh id elit. Duis sed odio sit amet nibh vulputate cursus a sit amet mauris. Morbi accumsan ipsum velit. Nam nec tellus a odio tincidunt auctor a id libero.', author: 'Autor 3' },
                { url: 'https://picsum.photos/id/10/200/300', description: ' Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.', author: 'Autor 4' },
            ],
            visibleStart :0,
            visibleEnd:4,
            selectedPhoto:null,
        };
    },
    computed:{
        visiblePhotos(){
            return this.photos.slice(this.visibleStart, this.visibleEnd);
        },
    },

    methods: {
        handleScroll(event) {
            const container = event.target;
            if(container.scrollleft + container.clientWidth >= container.scrollWhidth ){
                this.visibleStart = Math.min(this.visibleStart + 2, this.photos.length -2);
                this.visibleEnd = Math.min(this.visibleEnd + 2, this.photos.length);
            } else if (container.scrollleft === 0){
                this.visibleStart = Math.max(this.visibleStart - 2, 0);
                this.visibleEnd = Math.max(this.visibleEnd - 2, 2);
            }
        },

        selectPhoto(photo){
            this.selectedPhoto = photo;
            },
        },
    };
</script>

<style>
.gallery-container {
  display: flex; /* Usar flexbox para alinear la galería y los detalles */
  text-align: center;
}

.image-gallery {
  width: 400px; /* Ajusta el ancho según sea necesario */
  height: 400px; /* Establece una altura fija para mostrar solo una imagen */
  display: flex;
  flex-direction: column; /* Cambia a columna para mostrar verticalmente */
    overflow-y: auto; /* Permite el desplazamiento vertical */
  
    border: 1px solid #ccc;
}

.scroll-container {
  display: flex;
  flex-direction: column; /* Asegúrate de que el contenedor también sea columna */
}

.image-item {
  margin: 0; /* Sin margen para que solo se vea una imagen a la vez */
  cursor: pointer;
}

img {
  max-width: 100%; /* Asegúrate de que las imágenes se ajusten al ancho del contenedor */
  max-height: 100%; /* Asegúrate de que las imágenes no excedan la altura del contenedor */
  object-fit: cover; /* Asegúrate de que la imagen cubra el área del contenedor */
    margin-bottom: 10px;
    margin-top: 10px;
}

.details {
  margin-left: 20px; /* Espacio entre la galería de imágenes y los detalles */
  flex: 1; /* Permite que el componente de detalles ocupe el espacio restante */
}
</style>