<template>
  <div class="THREADCONTENTS" id="THREADCONTENTS">
    <h3 class="thread_title">
      <!--标题 start-->
      <span>{{threadname}}</span>
      <!--标题的保存回头再写-->
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
        <dd>{{item.content}}</dd>
        <!--内容 end-->
        <!--层 end-->
      </span>
      <textarea class="thtitle" v-model="thtitle" placeholder="标题"></textarea>
      <button @click="changetitle">更改标题</button>
      <textarea class="iden" v-model="name" placeholder="名称"></textarea>
      <textarea class="iden" v-model="ttime" placeholder="时间"></textarea>
      <textarea class="iden" v-model="iden" placeholder="ID"></textarea>
      <textarea class="txt" v-model="txt" placeholder="输入文本"></textarea>
      <button @click="addcomponent">发送</button>
      <br />
      <textarea
        class="iden"
        v-model="deliden"
        placeholder="要删除的楼层数"
      ></textarea>
      <button @click="delcomponent">删除</button>
    </dl>
    <textarea
      class="iden"
      v-model="threadname"
      placeholder="读取/储存名"
    ></textarea>
    <button @click="savethread">导出帖子</button>
    <button @click="loadthread">导入帖子</button>
    <!--帖子 end-->
  </div>
</template>
<script>
export default {
  name: "THREADCONTENTS",
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
    addcomponent: function() {
      if (this.txt) {
        if (!this.iden) {
          this.iden = "r0SeYa5A1";
        }
        if (!this.name) {
          this.name = "（　´∀）・∀）,,ﾟД)";
        }
        if(!this.ttime){
          this.ttime="2020/12/26(土) 12:34:56";
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
      this.list.splice(this.deliden - 1, 1);
      this.deliden = "";
    },
    savethread: function() {
      if (!this.threadname) {
        this.threadname = "thread-default";
      }
      localStorage.setItem(this.threadname, JSON.stringify(this.list));
    },
    loadthread: function() {
      if (!this.threadname) {
        this.threadname = "thread-default";
      }
      var data1 = JSON.parse(localStorage.getItem(this.threadname));
      this.list = [];
      for (const i of data1) {
        this.list.push(i);
      }
      /*
      map[count] =list.length
      map[i]=list[i]
      */
    },
    changetitle:function(){
      this.threadname = this.thtitle;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import "./style.css";
</style>
