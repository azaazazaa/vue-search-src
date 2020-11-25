<template>
  <div class="right-content">
    <div 
        class="tag"
        v-for="(value, index) in tags"
        :key="index"
        @click="returnTag(index)"
    >
    {{value}}
    <div class="icons__trash"/>
    </div>
  </div>
</template>

<script>
export default {
    props: {
        massOfTags: Array
    },
    data(){
        return{
        name: 'HelloWorld',
        tags: [],
        
        }
    },
    methods:{
        returnTag(index){
            console.log('Тыкнули на ', index)
            this.$emit('returnTagIndex', index)
            this.tags.splice(index, 1);
            /* this.$set(this.tags, index, "") */
        }
    },
    watch:{
        massOfTags(value){
            this.tags = value;
        }
    }
  
}
</script>

<style lang="scss">
.right-content{
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
    align-items: flex-start;
    flex-basis: 40%;
    height: min-content;
    padding: 0 17px;
}
@mixin random-color(){
  $color: rgb(random(255), random(255), random(255));
}

.tag{
    display: flex;
    align-items: center;
    font-family: 'Regular-bold';
    font-size: 14px;
    height: 30px;
    line-height: 30px;
    align-content: center;
    border-radius: 12px;
    margin: 5px 3px;
    padding: 0 15px 0 10px;
    @for $i from 0 to 100{
        &:nth-child(#{$i}){
            $color: rgb(random(255), random(255), random(255));
            background: $color;
            color: darken($color, 30%);
            &:hover{
                cursor: pointer;
                background-color: lighten($color, 10%);
            }
        }
    }
}
</style>
