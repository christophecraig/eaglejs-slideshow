<template lang='pug'>
#MyFirstSlideshow
  .eg-slideshow
    slide(enter="fadeIn")
      div.container
        h1.main-title 
          span Faciliter la gestion d'une équipe dans le domaine du web
          div.svg-container
            eg-transition(enter="slideInLeft" style="animation-delay: 1s!important;")
              svg(width="1200px" height="1vw" viewbox="0 0 1vw 1200")
                rect(width="1200" height="1vw" style="fill:indianred;")


    slide(enter="fadeIn")
      h2 Comment proposer une interface à la fois #[strong claire] et #[strong complète] pour gérer un macro-planning ?

    slide(:steps=4 enter="fadeIn")
      h3 Le contexte
      ul
        eg-transition(enter="fadeIn" leave="fadeOut")
          li(v-if="step >= 2").
            Besoin d'une interface plus simple
        eg-transition(enter="fadeIn" leave="fadeOut")
          li(v-if="step >= 3").
            Besoin d'une interface plus moderne
        eg-transition(enter="fadeIn" leave="fadeOut")
          li(v-if="step >= 4").
            Besoin de fonctionnalités supplémentaires


    slide(:steps="3" enter='fadeIn')
      h3 L'existant
      eg-transition(enter="fadeIn")
        figure(v-if="step === 2")
          img(src="./assets/mypmb.png")

      eg-transition(enter="fadeIn")
        figure(v-if="step === 3")
          img(src="./assets/openerp.png")

    slide(:steps="7" enter="fadeIn")
      h3 L'application
      ul
        eg-transition(enter="fadeIn")
          li(v-if="step >= 2") Un WebService
            eg-transition(enter="fadeIn" leave="fadeOut")
              p(v-if="step >= 4") Qui interagit avec la base de données
            eg-transition(enter="fadeIn" leave="fadeOut")
              p(v-if="step >= 5") Qui met à disposition des fonctions utilisables par le client
        
        eg-transition(enter="fadeIn")
          div(v-if="step >= 7").
            ci-gira le schéma de l'api présentant également la consommation du webservice par

        eg-transition(enter="fadeIn")
          li(v-if="step >= 3") Une interface utilisateur #[small #[em (le client)]]
            eg-transition(enter="fadeIn" leave="fadeOut")
              p(v-if="step >= 6") Qui utilisera les fonctions fournies par le WebService
</template>

<script>
// import titles from 'title'
import eagle from 'eagle.js'
// import Snap from 'imports-loader?this=>window,fix=>module.exports=0!snapsvg/dist/snap.svg.js'
export default {
  mixins: [eagle.slideshow],
  data () {
    return {
      myRect: {
        color: 'indianred',
        width: 35,
        height: 10,
        x: 0,
        y: 0
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
  },
  created () {

  },
  methods: {

  },
  computed: {
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
}
</style>
