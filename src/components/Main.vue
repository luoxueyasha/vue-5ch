<template>
  <div class="THREADCONTENTS" id="THREADCONTENTS">
    <h3 class="thread_title">
      <!--标题 start-->
      <span>{{ threadname }}</span>
      <!--标题 end-->
    </h3>
    <br />
    <!--帖子 start-->
    <dl class="thread" id="thread" style="margin-top: 0px">
      <span v-for="(item, index) in list" v-bind:key="index">
        <!--层 start-->
        <dt>
          <!--发言人 start-->
          {{ index + 1 }} 名前：
          <span class="ttitle" style="color: #228822">
            <strong style="font-family: '思源黑体', '宋体'"
              >{{ item.name }}さん
            </strong>
          </span>
          {{ item.time }}<small style="color: gray">.00</small> ID:{{ item.ID }}
          <!--发言人 end-->
        </dt>
        <!--内容 start-->
        <dd>{{ item.content }}</dd>
        <!--内容 end-->
        <!--层 end-->
      </span>
    </dl>

    <div>
      <EDITOR>{{ EditorContent }}</EDITOR>
    </div>

    <textarea class="iden" v-model="thtitle" placeholder="读取/储存名">
    </textarea>
    <button @click="savethread">导出帖子</button>
    <button @click="loadthread">导入帖子</button>
    <!--帖子 end-->
  </div>
</template>
<script>
//vue
import EDITOR from "./Editor.vue";
export default {
  name: "THREADCONTENTS",
  components: {
    EDITOR,
  },
  data() {
    return {
      list: [],
      name: "",
      iden: "",
      txt: "",
      deliden: "",
      threadname: "thread-default",
    };
  },
  methods: {
    myfunc: function() {},
    /*
    addcomponent: function() {
      if (this.txt) {
        if (!this.iden) {
          this.iden = "r0SeYa5A1";
        }
        if (!this.name) {
          this.name = "（　´∀）・∀）,,ﾟД)";
        }
        if (!this.ttime) {
          this.ttime = "2020/12/26(土) 12:34:56";
        }
        this.list.push({
          name: this.name,
          time: this.ttime,
          ID: this.iden,
          content: this.txt,
        });
        this.txt = "";
      }
    },
    delcomponent: function() {
      //这个要改成删除指定楼层数，而非数组下标的
      //楼层数单独拿出来做一个可自定义内容（且不唯一）
      if (this.deliden) {
        this.list.splice(this.deliden - 1, 1);
        this.deliden = "";
      }
    },
    changetitle: function() {
      this.threadname = this.thtitle;
    },
    savethread: function() {
      if (!this.thtitle) {
        this.thtitle = "thread-default";
      }
      localStorage.setItem(this.thtitle, JSON.stringify(this.list));
    },
    loadthread: function() {
      if (!this.thtitle) {
        this.thtitle = "thread-default";
      }
      this.changetitle();
      var data1 = JSON.parse(localStorage.getItem(this.thtitle));
      this.list = [];
      for (const i of data1) {
        this.list.push(i);
      }
    },
    */
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import "./style.css";
</style>
