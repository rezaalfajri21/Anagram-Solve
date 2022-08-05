<template>
  <div class="about">
    <h1>Input = {{input}} <button v-on:click="destroy()">Delete</button></h1>

    <input v-model="keyword" type="text">
    <button v-on:click="add(keyword)">Add</button>
    

    <h1 v-if="clicked">Output = {{baru3}} <button v-on:click="reset()">Reset</button></h1>
    <br><br>
    <button v-if="!clicked" v-on:click="sort(input)">Sort</button>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'About',
  data(){
    return{
      input:  ['kita', 'atik', 'tika', 'aku', 'kia', 'makan', 'kua'],
      keyword: '',
      baru : [],
      baru2 : [],
      baru3: [],
      clicked : false,
    }
  },
   async created(){
      this.sort();
      document.title = "Movies";
  },
  mounted() {
    this.sort();
  },
  methods:{
    add(keyword) {
      this.input.push(keyword);
      console.log(this.input);
    },
    destroy() {
      this.input = [];
    },
    reset() {
      this.clicked = false;
      this.input = ['kita', 'atik', 'tika', 'aku', 'kia', 'makan', 'kua'],
      this.baru = [];
      this.baru2 = [];
      this.baru3 = [];
    },
    async sort(text){
      var a;
      // a = text[5].split('').sort().join('');
      // console.log(a);

      for(var i = 0; i < text.length; i++) {
        console.log(text[i]);
        a = text[i].split('').sort().join('');
        this.baru[i] = a;
        console.log(this.baru[i]);
      }
      this.baru2 = this.baru.filter((el, index) => this.baru.indexOf(el) === index );
      console.log(this.baru2);

      for(var j = 0; j < this.baru2.length; j++) {
        var sama = [];
        for(var k = 0; k < this.baru.length; k++) {
          if(this.baru2[j] === this.baru[k]) {
            sama.push(this.input[k]);
          }
        }
        this.baru3.push(sama);
      }
      console.log(this.baru3);
      this.clicked = true;
    },
  }
}
</script>