# vue-card-carousel

_Please note this is in active development and subject to change until it is out of alpha versions._

## Installation

Via NPM:

```
npm i vue-card-carousel
```

You can choose to either install globally or locally, as desired:

Globally:

```
import Vue from 'vue'
import App from './App.vue'
import VueCardCarousel from "vue-card-carousel";

Vue.use(VueCardCarousel)

new Vue({
  el: '#app',
  render: h => h(App)
})
```

or locally to a component:

```
import { VueCardCarousel } from "vue-card-carousel";

export default {
    components: {
        VueCardCarousel
    }
}
```

## Usage

Most basic usage would be adding the component and passing in the array of items you want displayed:

```
<template>
  <div id="app">
    <VueCardCarousel :elements="elements"></VueCardCarousel>
  </div>
</template>

<script>
import { VueCardCarousel } from "vue-card-carousel";

export default {
  components: {
    VueCardCarousel
  },
  data() {
    return {
      elements: [{ id: 1 }, { id: 2 }, { id: 3 }]
    };
  }
};
</script>
```

However this will be relatively uninteresting. To make the most use of this component, you'll want to add customizations via props and slots like below:

```
<template>
  <div id="app">
    <VueCardCarousel
      :elements="elements"
      :show-footer="false"
      header-color="#28a745"
      footer-color="#17a2b8"
    >
      <template v-slot:header><strong>Header</strong></template>
      <template v-slot:default="slotProps">
        <div v-for="n in 5" :key="n">
          {{ slotProps.iterantProp.id }}. Hello from the Parent
        </div>
      </template>
      <template v-slot:footer><strong>Footer</strong></template>
    </VueCardCarousel>
  </div>
</template>

<script>
import { VueCardCarousel } from "vue-card-carousel";

export default {
  components: {
    VueCardCarousel
  },
  data() {
    return {
      elements: [{ id: 1 }, { id: 2 }, { id: 3 }, { id: 4 }]
    };
  }
};
</script>
```
