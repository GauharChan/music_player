<template>
  <div class="hello">
    <audio  controls="controls" autoplay="autoplay" :src="music" :id = "audioId" @ended="next()"></audio>
    <div class="content">
      <div class="animated" v-for="(list, index) in lists" :key="index">
        <p :class="{animated:true, pp:list.mm}" @click="change(index)">{{list.name}}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      lists:[
        {name:'陈奕迅 eason and the duo band - 我们万岁',src:require('./music/陈奕迅 eason and the duo band - 我们万岁.mp3'),mm:false,id:0},
        {name:'陈奕迅 eason and the duo band - 8：15pm (Intro)',src:require('./music/陈奕迅 eason and the duo band - 8：15pm (Intro).mp3'),mm:false,id:1},
        {name:'陈奕迅 eason and the duo band - Devotion (Interlude)',src:require('./music/陈奕迅 eason and the duo band - Devotion (Interlude).mp3'),id:2},
        {name:'陈奕迅 eason and the duo band - Originality  (Interl',src:require('./music/陈奕迅 eason and the duo band - Originality  (Interl.mp3'),id:3},
        {name:'陈奕迅 eason and the duo band - R U N',src:require('./music/陈奕迅 eason and the duo band - R U N.mp3'),id:4},
        {name:'陈奕迅 eason and the duo band - Unity (Interlude)',src:require('./music/陈奕迅 eason and the duo band - Unity (Interlude).mp3'),id:5},
        {name:'陈奕迅 eason and the duo band - 蠢',src:require('./music/陈奕迅 eason and the duo band - 蠢.mp3'),id:6},
        {name:'陈奕迅 eason and the duo band - 疯狂的朋友',src:require('./music/陈奕迅 eason and the duo band - 疯狂的朋友.mp3'),id:7},
        {name:'陈奕迅 eason and the duo band - 海里睡人',src:require('./music/陈奕迅 eason and the duo band - 海里睡人.mp3'),id:8},
        {name:'陈奕迅 eason and the duo band - 渐渐',src:require('./music/陈奕迅 eason and the duo band - 渐渐.mp3'),id:9},
        {name:'陈奕迅 eason and the duo band - 敬烟',src:require('./music/陈奕迅 eason and the duo band - 敬烟.mp3'),id:10},
        {name:'陈奕迅 eason and the duo band - 可一可再',src:require('./music/陈奕迅 eason and the duo band - 可一可再.mp3'),id:11},
        {name:'陈奕迅 eason and the duo band - 龙舌兰',src:require('./music/陈奕迅 eason and the duo band - 龙舌兰.mp3'),id:12},
        {name:'陈奕迅 eason and the duo band - 破坏王',src:require('./music/陈奕迅 eason and the duo band - 破坏王.mp3'),id:13},
        
      ],
      music:require('./music/陈奕迅 eason and the duo band - 我们万岁.mp3'),
      audioId:0
    }
  },
  methods: {
    change(index){
      this.music = this.lists[index].src;
      this.audioId = this.lists[index].id;
      for (let i = 0; i < this.lists.length; i++) {
        if(index == i){
          this.lists[index].mm = true;
        }else{
          this.lists[i].mm = false;
        }
      }
    },
    // 自动播放下一首
    next(){
      let that = this
      let tt = parseInt(that.audioId);
        if(tt == that.lists[tt].id){
          tt += 1
          that.music = that.lists[tt].src
          that.audioId +=1
          for (let i = 0; i < this.lists.length; i++) {
            if(tt == i){
              this.lists[tt].mm = true;
            }else{
              this.lists[i].mm = false;
            }
          }
      }
    }
  },
  watch: {
    
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.content{
  border: 1px solid rgb(231, 133, 5);
  margin: 20px auto;
  text-align: left;
}
p{
  border-bottom: 1px solid rgb(247, 196, 130);
  padding-left: 10px;
  
}
.pAnimate{
  animation: bounceln 1s;
}
.pp{
  animation: pulse 1s;
  color: rgb(231, 133, 5);
}
</style>
