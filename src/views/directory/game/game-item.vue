<template>
  <div class="list-block" v-link="{name: 'room', params: {id: game.room_id}}">
    <image-placeholder :src="game.room_src"></image-placeholder>
    <div class="column">
      <p class="rtitle">{{game.room_name}}</p>
      <p class="up"><i class="icon icon-user"></i> {{game.nickname}}</p>
      <p class="prev"><i class="icon icon-users"></i> {{game.online | fixed}}</p>
    </div>
  </div>
</template>
<script>
import ImagePlaceholder from '../../../components/image-placeholder'
export default {
    props: {
      game: {
        type: Object,
        required: true
      }
    },
    ready () {
      this.getTitle()
    },
    methods: {
      getTitle () {
        this.$dispatch('header-title', this.game.game_name);
       }
    },
    components: {
      ImagePlaceholder
    }
}
</script>
<style lang='scss'>
$font-color:#7E7E7E;
.list-block {
  cursor: pointer;
  position: relative;
  min-height: 1.68rem;
  margin: 0.447rem;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  img {
    width: 10pc;
    height: 5.5pc;
  }
  .column {
    font-size: 12.5px;
    line-height: 1.2;
    margin-left: 0.267rem;
    -webkit-flex: 1;
    flex: 1;
    .rtitle {
      /*color: $font-color;*/
      margin-bottom: 5px;
    }
    .up, .prev {
      color: $font-color;
      margin-top: 10px; 
    }
  }
}
</style>
