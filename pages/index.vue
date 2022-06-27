<template>
  <div class="layout-site">
    <header id="header">
      <h1>Joseph Blake</h1>
    </header>
    <main class="layout-page">
      <section id="main_content" class="layout-section">
        <h1 class="text-big">Artwork</h1>
        <!-- Image example
        <img :srcset="require( `~/assets/artwork/${ artwork.slug }/original.jpg` ).srcSet"
             :alt="artwork.alt"
             :title="artwork.alt" />
        -->
      </section>
      <section id="contents" class="layout-section">
        <h2 class="text-label">Contents</h2>
          <ol>
            <li>Artwork 1</li>
            <li>Artwork 2</li>
            <li>Artwork 3</li>
            <li>Artwork 4</li>
          </ol>
      </section>
    </main>
  </div>
</template>



<script>
export default {
  name: 'IndexPage'
}
</script>



<style scoped>
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
