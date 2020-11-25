<template>
  <div class="left-content">
    <div class="font-body-bold">Ваши ключевые навыки:</div>
    <div class="font-gray-regular space-bottom">Навыки, по которым вы хотите, чтобы вас искали</div>
    <input class="input-text" type="text" placeholder="Начните вводить здесь" v-model="searchText" /><!-- @blur="showFoundList = false" -->
    <ul v-show="showFoundList">
      <li
        v-for="(value, index) in getFoundList"
        :key="index"
        @click="addToSkills(value[0])"
        :class="value[1] ? '' : 'input-text_disabled'"
      >{{value[0]}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props:{
    returnedSkill: String,
  },
  data(){
    return{
      name: 'HelloWorld',
      searchText: "",
      showFoundList: false,
      skillList: [
        {
          label: 'Программирование',
          value: 'programming',
          isAble: true
        },
        {
          label: 'Критическое мышление',
          value: 'critical Thinking',
          isAble: true
        },
        {
          label: 'Машинное обучение',
          value: 'machineLearning',
          isAble: true
        },
        {
          label: 'Навыки коммуникации',
          value: 'communicationSkills',
          isAble: true
        },
        {
          label: 'Python',
          value: 'python',
          isAble: true
        },
        {
          label: 'Pythonasdascsdvewgvwevweves',
          value: 'python1',
          isAble: true
        }
      ],
    }
  },
  methods:{
    addToSkills(value){
      this.skillList.forEach(element => {
        if((element.label == value) && (element.isAble)){
          element.isAble = false;
          this.$emit('addToSkills', value)
        }
      });
    },
  },
  computed:{
    getFoundList(){
      let founded = [];
      this.skillList.forEach(element => {
        if(element.label.toLowerCase().includes(this.searchText.toLowerCase())){
          founded.push([element.label,element.isAble])
        }
      });
      return founded
    }
  },
  watch: {
    searchText(value){
      this.showFoundList = Boolean(value);
    },
    returnedSkill(value){
      this.skillList.forEach(element => {
        if(element.label == value.trim()){
          element.isAble = true;
        }
      });
    }
  }
  
}
</script>

<style lang="scss" scoped>
.left-content{
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  flex-basis: 60%;
  padding-right: 20px;
  border-right: 3px solid #F3F2F5;
}
.space-bottom{
  margin-bottom: 20px;
}
ul{
  width: 100%;
  padding: 0;
  margin: 0;
  border-radius: 12px;
  font-size: 16px;
  line-height: 19px;
  width: 100%;
  border: 2px solid #F3F2F5;
}
li{
  list-style-type: none;
  background: #FFFFFF;
  align-content: center;
  line-height: 40px;
  height: 40px;
  border-bottom: 2px solid #F3F2F5;
  padding-left: 20px;
  box-sizing: border-box;
  &:last-child{
    border-bottom: none;
    border-bottom-left-radius: 12px;
    border-bottom-right-radius: 12px;
  }
  &:first-child{
    border-top-left-radius: 12px;
    border-top-right-radius: 12px;
  }
  &:hover{
    background: linear-gradient(0deg, rgba(57, 20, 175, 0.1), rgba(57, 20, 175, 0.1)), #FFFFFF;
    cursor: pointer;
  }
}
/* input{

  $[type=text]{

  }
} */

</style>