<template>
  <div id="app">
    <div class="block main flex">
      <input-search 
        @addToSkills="addToSkills"
        :returnedSkill="returnedSkill"
        @
      />
      <added-tags 
        :massOfTags="selectedSkills"
        @returnTagIndex="returnTagIndex"
      />
    </div>
  </div>
</template>

<script>
import AddedTags from './components/AddedTags.vue'
import InputSearch from './components/InputSearch.vue'

export default {
  components: { InputSearch, AddedTags },
  data(){
    return{
      selectedSkills: [],
      returnedSkill: '',
    }
  },
  methods:{
    addToSkills(e){
      this.selectedSkills.push(e);
    },
    returnTagIndex(index){
      if(this.returnedSkill === this.selectedSkills[index]){
        this.returnedSkill = this.selectedSkills[index] + ' ';
      }else{
        this.returnedSkill = this.selectedSkills[index]
      }
    }
  }
}
</script>

<style lang="scss">
  .main{
    height: 850px;
    widows: 100%;
  }
  .block{
    background: linear-gradient(0deg, rgba(255, 255, 255, 0.98), rgba(255, 255, 255, 0.98)), linear-gradient(0deg, rgba(68, 0, 184, 0.3), rgba(68, 0, 184, 0.3)), #000000;
    border-radius: 6px;
    padding: 30px 10px 60px 50px;
    
  }
  .flex{
    display: flex;
  }
  .flex__center{
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>