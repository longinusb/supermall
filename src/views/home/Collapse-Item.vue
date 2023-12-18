<template>
    <div class = "collapse-item">
        <div class = "title" @click = "toggleShow">
            <span>{{title}}</span>
            <span>{{title}}</span>
            <span>{{title}}</span>
            <i class = "el-icon-arrow-right" :style = "roundIcon"></i>
        </div>
        <div class = "content" :style = "contentStyle">
            <div class="gap"></div>
            <slot></slot>
        </div>

    </div>
</template>

<script>
export default {
  name: "fl-Collapse-Item",
  mounted() {
    this.$bus.$on("otherToggle", (beforoState, title) => {
      this.contentShow = false;
      if (this.title == title) {
        //状态判断
        this.contentShow = beforoState;
      }
    });
  },
  props: {
    title: {
      type: String
    }
  },
  data() {
    return {
      contentShow: false //显示状态
    };
  },
  methods: {
    toggleShow() {
      this.contentShow = !this.contentShow;
      this.$emit("handleToggle", this.title);
      if (this.$attrs.accordion == "") {
        this.$bus.$emit("otherToggle", this.contentShow, this.title); //手风琴分发所有状态
      }
    }
  },
  computed: {
    roundIcon() {
      if (this.contentShow) {
        return "transform: rotate(225deg);";
      } else {
        return "transform: rotate(135deg);";
      }
    },
    contentStyle() {
      if (this.contentShow) {
        if (this.$attrs.height) {
          return `height:${this.$attrs.height}px`;
        } else {
          return "height:50px";
        }
      } else {
        return "height:0";
      }
    }
  }
};
</script>

<style scoped>
.collapse-item {
  display: flex;
  flex-direction: column;
  padding: 1px 0;
  border-bottom: 1px solid #ccc;
  font-size: 20px;
  line-height: 40px;
}
.collapse-item .title {
  display: flex;
  justify-content: space-between;
  align-items: center;
  cursor: pointer;
}
.collapse-item .content {
  height: 0;
  transition: 0.3s linear;
  overflow: hidden;
}
.collapse-item .el-icon-arrow-right {
  width: 10px;
  height: 10px;
  border-left: 2px solid black;
  border-top: 2px solid black;
  margin-right: 5px;
  transition: 0.1s linear;
}
.gap {
  height: 10px;
}
</style>
