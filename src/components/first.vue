<template>
  <div id="upload" class="box">
    <h2>大爱无疆</h2>
    <div class="main">
      <li><input type="file" name="photo" id="photo" class="uoload" @change="getImg()" accept="image/jpeg,image/jpg,image/png"></li>
      <li> <textarea rows="4" cols="20" class="fonttxt" name="photoinfo"  placeholder="照片介绍"> </textarea></li>
      <li> <button class="fontbtn" @click="showImg()">提交</button></li>
    </div>
    <ul class="photos">
      <li v-for="item in imgsrc">
        <img :src="item" width="300px">
      </li>
    </ul>
  </div>
  
</template>


<script>
export default {
  data(){
    return {
      imgsrc: [],
      items: []
    }
  },
  methods: {
    getImg: function(){
      let that = this;
      let myfile = document.getElementById("photo").files[0];
      that.items.push(myfile);
    },
    showImg: function(){
      console.log(this.items);
      let that = this;
      for(let i in that.items){
        let reader = new FileReader();
        let file = that.items[i];
        reader.readAsDataURL(file);
        reader.onload = function(){
          that.imgsrc.push(reader.result);
        }
      }
    }
  }
}
</script>

<style scoped>
.box h2{padding:20px 0}
.main{background: #ff8; padding: 50px 30px;}
.main li{text-align: center; padding: 10px 0; text-align: left;}
.fonttxt{width: 400px; padding: 5px 10px;border-radius: 3px;border: none; font-size: 20px;}
.fontbtn{width: 100px; height: 40px; background: #fff; display: inline-block; color: #000; font-size: 14px; text-align: center; line-height: 40px;border-radius: 5px; border:none; cursor: pointer; outline: none; line-height: 40px;}
.fontbtn:hover{background: rgba(255, 255, 255, .9)}
.uoload{font-size: 16px;}
.photos{text-align: left}
.photos li{padding: 10px; display: inline-block;}
</style>
