<template>
  <Collapse>
    <CollapseItem  v-for = "(item,index) in collapseData" :key = "index" :title = "item.title" accordion height="300">
    	<b>{{item.content}}</b>
    </CollapseItem>
</Collapse>
</template>

<script>
import Collapse from "./Collapse";
import CollapseItem from "./Collapse-Item";
export default {
  name: "Home",
  components: {
    Collapse,
    CollapseItem
  },
  data() {
    return {
      collapseData: [
        {
          title: "标题1",
          content:
            "与现实生活一致：与现实生活的流程、逻辑保持一致，遵循用户习惯的语言和概念；"
        },
        {
          title: "标题2",
          content:
            "控制反馈：通过界面样式和交互动效让用户可以清晰的感知自己的操作；"
        },
        {
          title: "标题3",
          content:
            "清晰明确：语言表达清晰且表意明确，让用户快速理解进而作出决策；"
        },
        {
          title: "标题4",
          content:
            "用户决策：根据场景可给予用户操作建议或安全提示，但不能代替用户进行决策；"
        }
      ]
    };
  }
};
</script>

<style scoped>
</style>
