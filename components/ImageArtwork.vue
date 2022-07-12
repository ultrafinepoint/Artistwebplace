<template>
    <img :srcset="require( `~/assets/artwork/${ artwork.slug }/original.jpg` ).srcSet"
       :alt="artwork.alt"
       :title="artwork.alt"
       @click="$emit( 'selectedArtwork', artwork )" />
</template>

<script>
export default {
  props: [ 'artwork' ],
}
</script>
