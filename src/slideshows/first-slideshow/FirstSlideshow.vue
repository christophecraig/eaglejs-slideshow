<template lang='pug'>
#MyFirstSlideshow
  .eg-slideshow
    slide(enter="fadeIn")
      h1.main-title Faciliter la gestion d'une équipe dans le domaine du web
        svg(width="800px" height="12px")
          rect(:width="width" height="12px" style="fill:indianred;")

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
      width: 0
    }
  },
  mounted () {
    console.log('test')
    var _this = this
    window.setTimeout(function () {
      _this.date = Date.now()
      _this.expand()
    }, 600)
  },
  methods: {
    expand () {
      var speed = 18 - ((Date.now() - this.date) / 80)
      if (this.width < 801 && speed > 0) {
        this.width += speed
        requestAnimationFrame(this.expand)
      } else {
        this.stop()
      }
    },
    stop () {
      cancelAnimationFrame(this.expand)
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
        .main-title {
          position: absolute;
          width: 70%;
          margin: 0;
          top: 50%;
          left: 50%;
          transform: translate(-50%, -50%);
        }
        svg {
          margin-left: 10px;
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
