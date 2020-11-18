<template>
  <li>
  <slot name="pre" :value="value"></slot>
  <span v-if="del">{{title}}</span>
  <span v-else style="text-decoration: line-through">{{title}}</span>
  <slot name="sub"></slot>
  <button v-show="del" @click="handleclick">删除</button>
</li>
</template>

<script>
export default {
  props: {
    title: String,
    del:{
      type:Boolean,
      default:true,
    },
  },
  data:function (){
    return {
      value:Math.random()
    }
  },
  methods:{
    handleclick(){
      console.log('点击删除按钮')
      this.$emit('delete',this.title)
    }
  },


}
</script>

<style scoped>

</style>