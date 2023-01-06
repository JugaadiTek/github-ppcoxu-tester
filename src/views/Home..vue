<script setup>
import NavBar         from "./components/NavBar.vue";
import hero           from "./components/hero.vue";
import newsletter     from "./components/newsletter.vue";
import servicescard   from "./components/servicescard.vue";
import FAQs           from "./components/FAQs.vue";
import postfeed       from "./components/postfeed.vue";
import artcont        from "./components/artcont.vue";
import optionslice    from "./components/optionslice.vue";
import optionsliceArt from "./components/optionsliceArt.vue";
import Postfeed       from "./components/postfeed.vue";
//import { ref } from 'vue';

// var slices = await fetch(`http:src/content/components/home.json`).then((r) => r.json());
var  = await fetch(`http:src/content/components/NavBar.json`).then((r) => r.json());
console.log(NavBar);




//const sliceContent = require('json-loader!./Home.json');
// console.log(sliceContent);
//import { navcontent } from './content/components/NavBar.js';

//console.log(ref);
//import { navcontent } from './NavBar.js';
//const navigations = ref(default);

//console.log([{navcontent,json2,json3}]) ;
//import { footercontent } from  './content/conponents/newsletter.js';

/*
var items = [],

function default {
  data() {
    return {
      items: []
    };
  },
  methods: {
    fetchItems() {
      const options = {method: 'GET'};
      console.log(options);

      fetch('http://localhost:5173/src/content/components/Home.json', options)
        .then(response => response.json())

        .then((data) => (this.items = data));
          console.log(this.items);
    }
  },
  mounted() {
    this.fetchItems();
  }
};
console.log(items);
*/


// export default {
//   data() {
//     return {
//       items: []
//     };
//   },
//   methods: {
//     fetchItems() {
//       fetch("https://l2wwalg3.directus.app/items/test")
//         .then((response) => response.json())
//         .then((data) => (this.items = data));
//       console.log(this);
//     }
//   },
//   mounted() {
//     this.fetchItems();
//   }
// };
</script>

<template>
  <header v-for="item in items"></header>
  <main>
    <!---------------------- NAVIGATION BAR ---------------------->
    <nav class="mainNav nogap darkbg">
      <NavBar :navbtn="navigationbar.sliceContent" />
    </nav>

    <!---<div class="wrapper">-->
    <section
      v-for="(slice, index) in slices"
      :class="[slice.alt, slice.component]"
      :id="`section_` + index"
      :key="index"
    >
      <!--  style="min-height:80vh; background-image:url('src/assets/BG Blank.jpg');background-size:cover;background-repeat:no-repeat;background-position:center center;"  -->
      <div v-if="slice.component == 'hero'">
        <hero :herocont="slice.sliceContent" />
      </div>

      <div class="container" v-else-if="slice.component == 'optionsliceArt'">
        <optionsliceArt :optionsliceArtCont="slice.sliceContent" />
      </div>

      <div class="container" v-else-if="slice.component == 'optionslice'">
        <optionslice :optionsliceCont="slice.sliceContent" />
      </div>

      <div class="container" v-else-if="slice.component == 'artcont'">
        <artcont :artcontent="slice.sliceContent" />
      </div>

      <div class="container" v-else-if="slice.component == 'postfeed'">
        <postfeed :postfeedCont="slice.sliceContent" />
      </div>

      <div class="container" v-else-if="slice.component == 'FAQs'">
        <FAQs :FAQcont="slice.sliceContent" />
      </div>

      <div class="container" v-else-if="slice.component == 'servicecard'">
        <servicescard :servicecardCont="slice.sliceContent" />
      </div>
    </section>
  </main>

  <!-- ----------------------------- FOOTER ----------------------------- -->

  <!--<footer class="container lavanderbg nogap-bottom" >
      <newsletter/>
    </footer>-->
</template>

<style></style>
