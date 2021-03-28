<template>
  <div class="home">
      <p>{{text}}</p>
      <button v-on:click="increase">버튼</button>
      <br><br>
      <button v-on:click="toggle">버튼</button>
      <div v-bind:class="backgroundColor">
          색이 바껴요
      </div>


      <br>
      <!-- <button @click="test">알림</button> -->
      <button v-on:click="test">알림</button>
      <br>
      
      <br><br><br><br>
      
      
      <p v-if="checked">{{ text1 }}</p>
      <p v-else>가렸음</p>

      <p v-show="checked">show</p>

      <input type="text" v-model="text1" >
      <input type="checkbox" v-model="checked">
      <br><br><br>

      <p>{{location}}</p>
      <select name="location" v-model="location">
        <option value="">구선택</option>
        <option value="관악구">관악구</option>
        <option value="중량구">중량구</option>
        <option value="양천구">양천구</option>
      </select>
     
      <select name="job">
        <!-- <option v-for="dong in dongs" v-bind:value="dong" v-bind:key="dong">{{dong}}</option> -->
        <option v-for="(dong, index) in dongs" v-bind:value="dong" v-bind:key="index + 'dongOption'">{{dong}}</option>
       </select>

  <p>
    당신의 계정은 {{idName}} 입니다 (computed)
  </p>
  <p>
    당신의 계정은 {{userName}} 입니다 (watch)
  </p>
  <input type="text" v-model="email">


  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";
   
export default {
  name: "Home",
  mounted(){
    console.log("Hi, everybody!!!");
  },
  computed: {
    backgroundColor(){
      return {
        "blue-background":this.classToggle,
        "pink-background":!this.classToggle
      }
    },
    idName(){
      return this.email.split("@")[0];
    },
  },
  watch: {
    email() {
      this.userName = this.email.split("@")[0];
    },
    location() {
      if(this.location == "관악구") {
        this.dongs = ["봉천동","12","32","3","4"]  
      }else if(this.location == "중량구"){
        this.dongs = ["양천동","a","b","c","d"]  
      }else if(this.location == "양천구"){
        this.dongs = ["ㅇㅇㅇㅇㅇ동","ㄱ","ㄴ","ㄷ","ㄹ"]  
      }
      console.log("this.location : " + this.location);
      console.log("this.dongs : " + this.dongs);

    },



  },
  data(){
    return {
      text : 1,
      classToggle : true,
      text1 : 1,
      checked : false,
      location : "",
      email : "",
      userName : "",
      dongs : [],
    }
  },
  methods: {
    increase(){
      this.text += 1;
    },
    toggle(){
      this.classToggle = !this.classToggle;
    },
    test(){
      alert("하이");


    }


  },




  // components: {
  //   HelloWorld,
  // },
};
</script>

<style>
.blue-background {
  background : gray;
}

.pink-background {
  background : pink;
}


</style>
