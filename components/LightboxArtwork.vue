<template>
  <div class="lightbox">
    <main>
      <section class="image-area">
        <!--
          <img :srcset="require( `~/assets/artwork/${ selectedArtwork.slug }/original.jpg` ).srcSet"
               :alt="selectedArtwork.alt"
               :title="selectedArtwork.alt"
               id="smart-image"/>
          </img>
        -->
        <img :src="require( `~/assets/artwork/${ selectedArtwork.slug }/original.jpg` )"
             :alt="selectedArtwork.alt"
             :title="selectedArtwork.alt"
             id="smart-image"/>
        </img>
      </section>
      <section class="meta layout-section">
        <h1>{{ selectedArtwork.title }}</h1>
        <p>{{ selectedArtwork.description }}</p>
        <p>Need date formatter</p>
      </section>
    </main>
    <div class="lightbox-close" @click="$emit( 'lightboxClose' )">
      <!-- svg -->
      <p>close</p>
    </div>
  </div>
</template>

<script>
import Panzoom from '@panzoom/panzoom';

export default {
  props: [ 'selectedArtwork' ],
  data: () => {
    return {
      // open: true,
    }
  },
  methods: {
    exampleMethod: function() {
      console.log( "this is an example" );
    },
  },
  mounted() {
    const elem = document.getElementById( 'smart-image' );
    /*
    const panzoom = Panzoom( elem, {
      maxScale: 5
    });
    panzoom.pan( 10, 10 );
    panzoom.zoom( 2, { animate: true })
    */

    const panzoom = Panzoom(elem, { canvas: true })
    const parent = elem.parentElement
    // No function bind needed
    parent.addEventListener('wheel', panzoom.zoomWithWheel)

    // This demo binds to shift + wheel
    parent.addEventListener('wheel', function(event) {
      if (!event.shiftKey) return
      panzoom.zoomWithWheel(event)
    })
  }
}
</script>

<style scoped>
.lightbox {
  /* background-color: rgba(0,0,0,0.8); */
  background-color: rgba(255,255,255,0.8);
  backdrop-filter: blur(8px);

  position: absolute;
  top: 0;
  right: 0;
  left: 0;
}

.image-area {
  background: whitesmoke;
}


.lightbox-close {
  background: blue;

  position: absolute;
  right: 0;
  top: 0;

  width: 64px;
  height: 64px;
}

.lightbox img {
  object-fit: contain;
  width: 100%;
}

/* Mobile */
@media only screen and ( max-width: 640px ) {
  .lightbox {
    min-height: 100%;
  }

  .lightbox > main {
    display: flex;
    flex-direction: column;

    gap: 24px;
    padding: 16px;
  }  
}

/* Tablet */
@media only screen and ( max-width: 800px ) and ( min-width: 640px ) {
  .lightbox {
    min-height: 100%;
  }

  .lightbox > main {
    display: flex;
    flex-direction: column;

    gap: 24px;
    padding: 24px;
  }  

}

/* Laptop */
@media only screen and ( max-width: 1440px ) and ( min-width: 800px ) {
  .lightbox > main {
    display: grid;
    grid-template-columns: auto 240px;

    height: 100vh;
    box-sizing: border-box;
    align-content: center;

    gap: 32px;
    /* margin: 32px 0; */
    padding: 32px;
  }  

  .meta {
    justify-content: flex-end; /* swap for full height panel */
    align-self: self-end;
  }
}

/* Desktop */
@media only screen and ( min-width: 1440px ) {
  .lightbox > main {
    display: grid;
    grid-template-columns: auto 320px;

    height: 100vh;
    box-sizing: border-box;
    align-content: center;

    gap: 64px;
    /* margin: 64px 0; */
    padding: 64px;
  }  

  .meta {
    justify-content: flex-end; /* swap for full height panel */
    align-self: self-end;
  }
}
</style>
