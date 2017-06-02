> A zero configuration progress loading bar component for Vue.js.

Just add a reference and it’s done.
 
The component interact with every ajax requisition to add a google top progress bar style 


# Requirements

- [Vue.js](https://github.com/vuejs/vue) `^2.0.0`
- Module bundler: [webpack](https://github.com/webpack/webpack)

# Installation

``` bash
$ npm install vue-auto-progress --save
```

# Usage

```javascript
<script>
import autoProgress from 'vue-auto-progress'

new Vue({
  el: '#app',
  router,
  data,
  template: '<div><App/><auto-progress/></div>',  
  components: { App, autoProgress }
})

</script>
```

# License

[The MIT License](http://opensource.org/licenses/MIT)