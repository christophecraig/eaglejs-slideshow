<template lang='pug'>
#MyFirstSlideshow
  .eg-slideshow
    slide(leave='fadeOut')
      h1 Faciliter la gestion d'une équipe dans le domaine du web
      h4 This is your first slideshow !

    slide(enter='fadeIn' leave='fadeOut')
      h3 Hey modify me !
      p.
        Come on modify me ! If you are running the development server,
        you will see the changes take effect immediaely

    slide(enter='fadeIn' leave='fadeOut')
      h3 Want cool effects?
      p.
        Code your own, or try stealing for the other slideshows !

    slide(enter='fadeIn')
      h3 
</template>

<script>
// import titles from 'title'
import eagle from 'eagle.js'
export default {
  mixins: [eagle.slideshow],
  data () {
    return {
      welcome: 'Bienvenue'
    }
  },
  infos: {
    // These infos appear on the home page, below the slideshow's thumbnail
    title: 'Présentation soutenance PFE',
    description: 'Faciliter la gestion d\'une équipe dans le domaine du web',
    path: 'presentation'
  }
}
</script>

<style lang='scss'>
@import url('https://fonts.googleapis.com/css?family=Rubik');
#MyFirstSlideshow {
  .eg-slideshow {
    font-family: 'Rubik';
    .eg-slide {
      .eg-slide-content {
        width: 25em;
        max-width: 80%;
        margin: 0 auto;
        h1 {
          font-size: 1.5em;
        }
      }
    }
  }
  .eg-slide-content {
    width: 25em;
    max-width: 80%;
    margin: 0 auto;
  }
  .fadeOut {
    position: absolute;
    top: 0;
  }
}
</style>
