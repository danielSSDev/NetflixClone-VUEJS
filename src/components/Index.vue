<template>
  <div class="index">
    <div class="movinRow" v-for="item in listMovie" :key="item.value">
      <h2 class="title">{{ item.title }}</h2>

      <div class="list-area">
        <div class="list">
          <div class="item" v-for="movie in item.items.results" :key="movie.item">
            <img :src="`https://image.tmdb.org/t/p/w300${movie.poster_path}`" alt="">
          </div>
        </div>
      </div>

    </div>
  </div>
</template>

<script>
import Tmdb  from '../tmdb';

export default {
  name: 'index',

  data: function(){
    return{
      listMovie: null
    }
  },

  props: {
  },

  mounted(){
    Tmdb.getHomeList().then( value => {
    this.listMovie = value
    console.log('LISTA DE FILME', this.listMovie)

    }).catch(err => {
      console.log('ERROOOOOO', err);
    })
  },

  methods:{
  }
}
</script>

<style>
.movinRow{
  margin-bottom: 30px;
}
.movinRow h2{
  margin: 0px 0px 0px 30px;
}
.list-area{
  overflow-x: hidden;
  margin-left: 30px;
}
.list{
  width: 99999999999999px;
}
.item{
  display: inline-block;
  width: 200px;
  padding: 5px;
  cursor: pointer;
}
.item img{
  max-width: 100%;
  transform: scale(0.9);
  transition: all ease 0.3s;
}
.item img:hover{
  transform: scale(1);
}


</style>


