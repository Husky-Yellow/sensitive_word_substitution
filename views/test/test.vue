<template>
  <div>
    <el-input
      placeholder="关键字"
      v-model="likestr"
      style="width:240px;"
    ></el-input>
    <el-button type="primary" icon="el-icon-plus" round @click="verStr"
      >处理</el-button
    >
    <el-input
      placeholder="关键字*"
      v-model="prolikestr"
      style="width:240px;"
    ></el-input>
    处理后：{{ verlikestr }}
  </div>
</template>

<script>
import { filterSensitiveWord, myReplace } from "@/utils/test";
export default {
  data() {
    return {
      likestr: "",
      verlikestr: "",
      prolikestr: "",
    };
  },
  methods: {
    verStr() {
      const temp = filterSensitiveWord(this.likestr);
      this.verlikestr = temp;
      this.prolikestr = this.likestr;
      temp.forEach((element) => {
        let star_count = element.length;
        let starstr = "";
        for (let i = 0; i < star_count; i++) {
          starstr += "*";
        }
        this.prolikestr = myReplace(this.prolikestr, element, starstr);
      });
    },
  },
};
</script>

<style></style>
