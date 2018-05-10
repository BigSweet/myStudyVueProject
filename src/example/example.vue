<template>
  <div >
      <button @click="toast()">
        点击弹出toast
      </button>

         <button @click="loading()">
        点击弹出加载框
      </button>
    <button @click="message()">
        点击弹出提示框
      </button>
       <mt-button @click.native="sheetVisible = true" size="large">点击上拉 action sheet</mt-button>
      <mt-button @click.native="sheetVisible2 = true" size="large">不带取消按钮的 action sheet</mt-button>
       <mt-actionsheet :actions="actions" v-model="sheetVisible"></mt-actionsheet>
       <mt-actionsheet :actions="actions2" v-model="sheetVisible2" cancel-text=""></mt-actionsheet>


       <mt-swipe :auto="4000">
  <mt-swipe-item>1</mt-swipe-item>
  <mt-swipe-item>2</mt-swipe-item>
  <mt-swipe-item>3</mt-swipe-item>
</mt-swipe>
  </div>
</template>

<script>
import Vue from "vue";
import { MessageBox } from "mint-ui";
import { Indicator } from "mint-ui";
import { Toast } from "mint-ui";
export default {
  data() {
    return {
      name: "App",
      sheetVisible: false,
      sheetVisible2: false,
      actions: [],
      actions2: []
    };
  },
  methods: {
    toast() {
      Toast("Upload Complete");
    },
    loading() {
      Indicator.open("Loading...");
    },
    message() {
      MessageBox({
        title: "Notice",
        message: "Are you sure?",
        showCancelButton: true
      });
    }
  },
  components: {},
  mounted() {
    this.actions = [
      {
        name: "拍照",
        method: this.takePhoto
      },
      {
        name: "从相册中选择",
        method: this.openAlbum
      }
    ];
    this.actions2 = [
      {
        name: "确定"
      },
      {
        name: "返回上一步",
        method: this.goBack
      }
    ];
  }
};
</script>

<style>

</style>
