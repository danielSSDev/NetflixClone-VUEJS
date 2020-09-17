<template>
  <div class="index">
   <p>OLA MUNDOOOO</p>
  </div>
</template>

<script>
import Tmdb  from '../tmdb';

export default {
  name: 'index',

  props: {
    msg: String
  },
  computed:{
    // Tmdb:function(value){
    //   console.log('VALOR', value)
    // }
  },

  mounted(){
    let list = Tmdb.getHomeList()
  Promise.all(list).then(function (value){
    console.log('FILME', value)
  })

  },

  methods:{
  }
}
</script>


