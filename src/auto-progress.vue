<template>
  <div><vue-progress ref="progressbar"></vue-progress></div>
</template>

<script>
import vueProgress from 'vue-top-progress'
import Vue from 'vue'

export default {
    name: "Progressbar",
    components: { vueProgress },
    mounted() {
      var progress = this.$refs.progressbar;

      var listener = { 
        tempOpen: XMLHttpRequest.prototype.open,
        tempSend: XMLHttpRequest.prototype.send,
        callback(){ }
      };

      XMLHttpRequest.prototype.open = function(a='',b='') {
        progress.start();
        listener.tempOpen.apply(this, arguments);
        listener.method = a;  
        listener.url = b;
        if (a.toLowerCase() == 'get') {
          listener.data = b.split('?');
          listener.data = listener.data[1];
        }
      }

      XMLHttpRequest.prototype.send = function(a='',b='') {
        setTimeout(()=>{ progress.done() }, 500);

        listener.tempSend.apply(this, arguments);
        if(listener.method.toLowerCase() == 'post') { listener.data = a };
        listener.callback();
      }
    }
}
</script>
