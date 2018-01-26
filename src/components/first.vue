<template>
  <div id="upload" class="box">
    <h2>大爱无疆</h2>
    <div class="main">
      <li><input type="file" name="photo" id="photo" class="uoload" @change="getImg()" multiple=""></li>
      <li> <textarea rows="4" cols="20" class="fonttxt" name="photoinfo"  placeholder="照片介绍"> </textarea></li>
      <li> <button class="fontbtn">提交</button></li>
      
    </div>
    <img height="200" alt="" :src="imgsrc">
    <div v-text="msg"></div>
    <div>{{ msg }}</div>
    <ul>
    <template v-for="item in items">
      <img :src="item">
    </template>
    </ul>
  </div>
</template>

<style scoped>
.box h2{padding:20px 0}
.main{background: #333; padding: 50px 30px;}
.main li{text-align: center; padding: 10px 0; text-align: left;}
.fonttxt{width: 400px; padding: 5px 10px;border-radius: 3px;border: none; font-size: 20px;}
.fontbtn{width: 100px; height: 40px; background: #fff; display: inline-block; color: #000; font-size: 14px; text-align: center; line-height: 40px;border-radius: 5px; border:none; cursor: pointer; outline: none; line-height: 40px;}
.fontbtn:hover{background: rgba(255, 255, 255, .9)}
.uoload{font-size: 16px;}
</style>
<script>
export default {
  data(){
    return {
      items : [],
      files : [],
      msg: '123',
      imgsrc: ''
    }
  },
  methods: {
    getImg: function(){
      let myfile = document.getElementById("photo").files;
      this.msg = myfile[0].name;
      //for(let i in this.files){
        let file = myfile[0];
        let reader = new FileReader();
        this.msg = file.name;
        reader.readAsDataURL(file);
        reader.onload = function(){
          this.imgsrc = reader.result;
          console.log(this.imgsrc);
          //this.items.push({img: this.result});
        }
        
      //}
    }
  }
}

document.addEventListener("keypress",subFont);
function subFont(e){
  var flen = doc.querySelector(".fonttxt").value.length;
  if(e.charCode == "13" && flen > 0){
      console.log(flen)
  }
}
</script>
