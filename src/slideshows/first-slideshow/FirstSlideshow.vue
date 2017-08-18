<template lang='pug'>
#MyFirstSlideshow
  .eg-slideshow
    slide(enter="fadeIn" leave="fadeOutDownBig")
      div.container
        h1.main-title 
          span Faciliter la gestion d'une équipe dans le domaine du web
          div.svg-container
            eg-transition(enter="slideInLeft" style="animation-delay: 1s!important;")
              svg(width="1200px" height="1vw" viewbox="0 0 1vw 1200")
                rect(width="1200" height="1vw" style="fill:indianred;")
        svg(id="test" version="1.1" width="300" height="200")
        input(type="color" v-model="myRect.color")
        input(type="range" v-model="myRect.r" step="2" min="10" max="200")
        form
          input(v-model="myRect.cx" type="number")
          input(v-model="myRect.cy" type="number")
        div(@click="move") Enorme

    slide(enter="slideInDown")
      h3 Hey modify me !
      p.
        Come on modify me ! If you are running the development server,
        you will see the changes take effect immediaely

    slide(enter="fadeIn" leave="fadeOut")
      h3 Want cool effects?
      p.
        Code your own, or try stealing for the other slideshows !

    slide(enter='fadeIn')
      h3 
</template>

<script>
// import titles from 'title'
import eagle from 'eagle.js'
import Snap from 'imports-loader?this=>window,fix=>module.exports=0!snapsvg/dist/snap.svg.js'
export default {
  mixins: [eagle.slideshow],
  data () {
    return {
      width: 0,
      myRect: {
        color: 'indianred',
        r: 15,
        cx: 100,
        cy: 100
      }
    }
  },
  infos: {
    // These infos appear on the home page, below the slideshow's thumbnail
    title: 'Présentation soutenance PFE',
    description: 'Faciliter la gestion d\'une équipe dans le domaine du web',
    path: 'presentation'
  },
  updated () {
    this.updateShape()
  },
  created () {
    var _S = Snap(document.getElementById('test'))
    this.shape = _S.rect(150, 50, 100, 100)
    this.shape.attr({
      fill: 'indianred'
    })
  },
  methods: {
    updateShape () {
      this.shape.attr({
        fill: this.shapeColor,
        width: this.shapeR,
        height: this.shapeR
      })
    },
    move () {
      this.shape.animate({
        x: this.computedCoordinates.cx,
        y: this.computedCoordinates.cy
      }, 500)
    }
  },
  computed: {
    shapeColor () {
      return this.myRect.color
    },
    shapeR () {
      return this.myRect.r
    },
    computedCoordinates () {
      return {
        cx: this.myRect.cx,
        cy: this.myRect.cy
      }
    }
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
        overflow: hidden;
        .main-title {
          position: relative;
        }
        .svg-container {
          position: absolute;
          bottom: 0;
          margin-left: 0px;
          z-index: -1;
          transform-origin: right;
          overflow: hidden;
          transform: scale3d(0.84, 1, 1);
        }
      }
    }
  }
  .eg-slide-content {
    width: 25em;
    max-width: 80%;
    margin: 0 auto;
  }
  .slideInLeft {
    transition-delay: 35s
  } // .fadeOut {
  //   position: absolute;
  //   top: 0;
  // }
}
</style>
