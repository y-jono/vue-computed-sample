<template>
  <ul>  
    <li 
      v-for="(item, index) in customList"
      :key="index"
      class="some"
      :class="{
        customAttr: item.customProp, 
        dependencyAttr: dependencyPropertyList[index]
      }"
    >{{item.hoge}}</li>
  </ul>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      targetList: [
        {hoge:"a", fuga:1},
        {hoge:"b", fuga:2},
        {hoge:"c", fuga:3},
        {hoge:"d", fuga:3},
        {hoge:"e", fuga:4},
      ]
    }
  },
  computed: {
    customList() {
      const customList = this.targetList.map(e => {
        e.customProp = (e.fuga === 3)
        return e;
      });
      return customList;
    },
    dependencyPropertyList() {
      return this.targetList.map(e => {
        const dependencyProperty = (e.fuga !== 3);
        return dependencyProperty;
      });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
