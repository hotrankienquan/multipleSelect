<template>
  <div id="app">
    <div id="container">
      <div id="left">

        <div
        v-for="(language, index) in languages"
        v-bind:key="index"
        v-show="language.position == 'left'"
        @click="language.selected = !language.selected"
        v-bind:class="{dangChon:language.selected}"
        >
        {{language.name}}
        </div>

      </div>
    <div>
      <button
      
      @click="languages.filter(lang => lang.position == 'right'
      && lang.selected).forEach(lang => {lang.position = 'left';lang.selected = false})"
      >&lt;</button>
      <button
      @click="languages.filter(lang => 
        lang.selected && lang.position == 'left'
      ).forEach(lang => {lang.position = 'right';lang.selected = false})"
      >	&gt;</button>

      
    </div>

    <div id="right">
      <div
      v-for="(language,index) in languages"
      :key="index"
      @click="language.selected = !language.selected"
      v-show="language.position == 'right'"
      :class="{dangChon:language.selected}"
      >
      {{language.name}}
      </div>
    </div>

    </div>
  </div>
</template>

<script>


export default {
  data() {
    return {
      // hienthiten:true,
      // cities: 
      // [
      //   {name: 'hanoi',editing:false},
      //  {name: 'hcm',editing:false},
      //   {name: 'da nang',editing:false}
      // ]
      languages: [
        {name:'Javascript', selected:false, position:'left'},
        {name:'php', selected:false, position:'right'},
        {name:'golang', selected:false, position:'left'},
        {name:'ruby', selected:false, position:'left'},
        {name:'c++', selected:false, position:'left'},
        {name:'c#', selected:true, position:'left'},
        {name:'python', selected:true, position:'left'},
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#container{
  display: flex;
}
#container #left, #right {
  border: 1px solid black;
  width: 200px;
  margin: 5px;
}
#left div.dangChon, #right div.dangChon {
  background-color: pink;
}
</style>
