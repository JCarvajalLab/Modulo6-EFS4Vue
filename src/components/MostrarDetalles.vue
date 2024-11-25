<template>
    <div class="image-details">
        <div class="details-container">
        <div class="image-section">
            <img :src="photo.url" :alt="photo.description" />
            <p><strong>Autor:</strong> {{ photo.author }}</p>
            <button @click="$emit('close')">Cerrar</button>
        </div>
        <div class="description-section">
            <h1>Detalles Imagenes</h1>
            <p><strong>Descripción:</strong> {{ photo.description }}</p>
        </div>
        </div>
    </div>
</template>

<script>
    export default{
        props: {
            photo: Object,
        },
    };
</script>

<style>
.image-details {
    border: 1px solid #ccc; /* Bordes del contenedor */
    padding: 20px;
    margin-top: 0px;
    display: flex; /* Usar flexbox para alinear la imagen y la descripción */
}

.details-container {
    display: flex; /* Usar flexbox para organizar la sección de imagen y descripción */
}

.image-section {
    margin-right: 20px; /* Espacio entre la imagen y la descripción */
}

img {
    max-width: 100%; /* Asegúrate de que las imágenes se ajusten al ancho del contenedor */
    max-height: 300px; /* Ajusta la altura máxima según sea necesario */
    object-fit: cover; /* Asegúrate de que la imagen cubra el área del contenedor */
}

h1 {
    font-size: 1.5em; /* Ajusta el tamaño de la fuente según sea necesario */
    margin-bottom: 15px; /* Espacio entre el encabezado y la descripción */
}

.description-section {
    flex: 1; /* Permite que la sección de descripción ocupe el espacio restante */
}

button {
    margin-top: 10px; /* Espacio entre el autor y el botón */
}

p{
    text-align: justify;
}
</style>