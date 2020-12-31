<template>
  <div class="THREADCONTENTS" id="THREADCONTENTS">
    <h3 class="thread_title">
      <!--标题 start-->
      <span>标题 </span>
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
        <dd v-html="item.content"></dd>
        <!--内容 end-->
        <!--层 end-->
      </span>
      <textarea class="iden" v-model="name" placeholder="名称"></textarea>
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
        this.list.push({
          name: this.name,
          time: "2020/12/26 12:34:56(土)",
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
      localStorage.setItem("key", JSON.stringify(this.list));
    },
    loadthread: function() {
      var data1 = JSON.parse(localStorage.getItem("key"));
      var temp = 0;
      this.list = [];
      /*
      map[count] =list.length
      map[i]=list[i]

      for(const i of data1){
        this.list[i]=data1[i];
      }
      */
      while (data1[temp].content != "") {
        this.list.push({
          name: data1[temp].name,
          time: data1[temp].time,
          ID: data1[temp].ID,
          content: data1[temp].content,
        });
        temp++;
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
div.THREADCONTENTS {
  z-index: 1;
  width: 93%;
  margin: 0.5em auto 0.75em auto;
  padding: 0.75em;
  border: 1px solid #333;
  color: #333;
  border-radius: 0.75em / 0.75em;
  background: #efefef;
  font-size: 1em;
}

a {
  border-width: 0px;
}

a:link {
  background: transparent;
  color: #0000cc;
}

a:active {
  background: transparent;
  color: #0000cc;
}

a:visited {
  background: transparent;
  color: #0000cc;
}

h3 {
  margin: 0;
  padding: 0.5em 0;
  text-align: left;
  font-size: 1em;
}

h3 span.common {
  padding: 0.5em;
  border-radius: 0.5em / 0.5em;
  background: #39f;
  color: #fff;
  font-size: 1em;
}

h3 span {
  padding: 0 0 0.5em 1em;
  color: #ff0000;
  font-size: 1.5em;
}

h3.thread_title {
  font-family: Saitamaar, "MS Gothic";
  margin: 0;
  padding: 0 2em 0 3em;
  text-indent: -4em;
}

div.board_header {
  margin: 0 1em 1em 1em;
  padding: 0.5em;
  color: #333;
  background: #efe;
  border-radius: 0.25em / 0.25em;
  font-size: 1em;
  height: 15em;
  overflow-y: scroll;
}

div.keyword {
  margin: 0;
  padding: 0;
  color: #333;
  background: inherit;
  font-size: 1em;
}

dt {
  margin: 0px 0.5em;
  padding: 0px;
  font-size: 1em;
}

dd {
  margin-bottom: 2em;
  font-size: 1em;
  font-weight: normal;
  white-space: pre-line;
}

span.keyword0 {
  padding: 0.5em;
  border-radius: 0.5em / 0.5em;
  background: #39f;
  color: #fff;
  font-size: 0.75em;
  line-height: 2.5em;
  word-break: keep-all;
}

span.keyword1 {
  padding: 0.5em;
  border-radius: 0.5em / 0.5em;
  background: #f63;
  color: #fff;
  font-size: 0.75em;
  line-height: 2.5em;
  word-break: keep-all;
}

textarea.iden {
  font-family: Saitamaar, "MS Gothic", Simsun;
  white-space: pre-line;
  width: 30%;
  height: 10%;
}

textarea.txt {
  font-family: Saitamaar, "MS Gothic", Simsun;
  width: 80%;
  height: 60%;
  min-height: 200px;
  white-space: pre-line;
}
</style>
