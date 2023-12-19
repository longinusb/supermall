<template>
<timeline :timeline-list="dongtai"></timeline>

</template>

<script>
import Timeline from "./timeLine";
export default {
  name: "Category",
  components: {
    Timeline
  },
  data() {
    return {
      dongtai: [
        {
          date: "2023-12-20",
          title: "2222",
          content: "123"
        },
        {
          date: "2023-12-20",
          title: "2222",
          content: "123"
        },
        {
          date: "2023-12-20",
          title: "2222",
          content: "123"
        }
      ]
    };
  }
};
</script>

<style scoped>
</style>
