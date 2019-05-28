<template>
  <div id="translateForm">
    <div class="col-md-6 col-md-offset-3">
      <form v-on:submit="fromSub" class="well form-inline">
        <input class="form-control" type="text" placeholder="输入需要翻译的内容" v-model="ToT">

        <select v-model="language"  class="form-control">
          <option value="en">英语</option>
          <option value="ja">日语</option>
          <option value="zh">国语</option>
          <option value="ko">朝鲜</option>
        </select>
        <input type="submit" value="翻译" class="btn btn-primary">
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "translateForm",
  data() {
    return {
      ToT: "",
      language: ""
    };
  },
  methods: {
    fromSub(e) {
      //   alert(this.ToT);
      this.$emit("fromSub", this.ToT, this.language);
      e.preventDefault();
    }
  },
  created() {
    this.language = "en"
  },
};
</script>

<style>
</style>
