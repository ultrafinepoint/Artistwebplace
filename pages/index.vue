<template>
  <div class="layout-site">
    <header id="header">
      <h1>Joseph Blake</h1>
    </header>
    <main class="layout-page">
      <section id="main_content" class="layout-section">
        <h1 class="text-big">Artwork</h1>
        <ol class="list-labelless layout-block--masonary">
          <li v-for="artwork in artworks"
              :key="artwork.id"
              class="layout-block">
            <article>
              <ImageArtwork :artwork="artwork"
                            @selectedArtwork="openLightbox( artwork )"/>
              <p @click="openLightbox( artwork )">{{ artwork.title }}</p>
            </article>
          </li>
        </ol>
      </section>
      <section id="contents" class="layout-section">
        <h2 class="text-label">Contents</h2>
      </section>
    </main>
    <footer>
      <LightboxArtwork :selectedArtwork="selectedArtwork"
                       v-if="lightboxOpen"
                       @lightboxClose="closeLightbox" />
      <!-- <LightboxArtwork :selectedArtwork="selectedArtwork" v-if="lightboxOpen"/> -->
    </footer>
  </div>
</template>



<script>
export default {
  name: 'IndexPage',
  data: () => {
    return {
      lightboxOpen: false,
      selectedArtwork: {}
    }
  },
  async asyncData({ $content, params, error }) {
    try{
      
      const artworks = await $content( "artwork" )
        .where({ published: true })
        .fetch()

      console.log( artworks );

      return { artworks }
    } catch ( err ) {
      error({
        statusCode: 404,
        message: "Page could not be found"
      })
    }
  },
  methods: {
    testing: function( title ) {
      console.log( title );
    },
    openLightbox: function( artwork ) {
      console.log( artwork );
      this.lightboxOpen = !this.lightboxOpen;
      this.selectedArtwork = artwork;

      console.log( this.lightboxOpen );
    },
    closeLightbox: function() {
      console.log( "blash test!!" );
      this.lightboxOpen = false;
      console.log( this.lightboxOpen );
    }
  }
}
</script>



<style scoped>
img {
  max-width: 100%;
}

#main_content {
  grid-area: main;
}

#contents {
  grid-area: contents;
}

/* Mobile */
@media only screen and ( max-width: 640px ) {
  .layout-page {

  }
}

/* Tablet */
@media only screen and ( max-width: 800px ) and ( min-width: 640px ) {
  .layout-page {
    grid-template-areas: "main contents";
    grid-template-columns: 2fr 1fr;
  }
}

/* Desktop */
@media only screen and ( max-width: 1440px ) and ( min-width: 800px ) {
  .layout-page {
    grid-template-areas: "main contents";
    grid-template-columns: 3fr 1fr;
  }
}

/* TV */
@media only screen and ( min-width: 1440px ) {
  .layout-page {
    grid-template-areas: "main contents";
    grid-template-columns: 4fr 1fr;
  }
}
</style>
