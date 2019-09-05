<template>
  <div id="app">
    <dynamic-form :field="fieldMap" :form="formData" @updateForm="receiveData">
      <template slot="share">
        <el-button type="primary" icon="el-icon-share"></el-button>
      </template>
    </dynamic-form>
  </div>
</template>
<script>
import DynamicForm from "./views/DynamicForm";
export default {
  components: {
    DynamicForm
  },
  data() {
    return {
      fieldMap: {
        name: {
          name: "name",
          label: "名称",
          type: "text",
          size: "mini"
        },
        sex: {
          name: "sex",
          label: "性别",
          type: "radio",
          size: "small",
          options: {
            list: [
              {
                name: "sex",
                label: "男",
                value: 0
              },
              {
                name: "sex",
                label: "女",
                value: 1
              }
            ]
          }
        },
        age: {
          name: "age",
          label: "年龄",
          type: "text",
          size: "medium"
        },
        city: {
          name: "city",
          label: "地区",
          type: "select",
          size: "small",
          options: {
            list: [
              {
                name: "beijing",
                label: "北京",
                value: 0
              },
              {
                name: "shanghai",
                label: "上海",
                value: 1
              },
              {
                name: "guangzhou",
                label: "广州",
                value: 3
              }
            ]
          }
        },
        country: {
          name: "country",
          label: "国家",
          type: "checkbox",
          size: "medium",
          options: {
            list: [
              {
                name: "china",
                label: "中国",
                value: 0
              },
              {
                name: "USA",
                label: "美国",
                value: 1
              }
            ]
          }
        },
        submit: {
          name: "submit",
          label: "",
          text: "提交",
          type: "button",
          size: "medium"
        },
        // 非表单元素
        share: {
          label: "分享",
          name: "share",
          isSlot: true
        }
      },
      formData: {
        name: "sutengfei",
        sex: 0,
        age: 18,
        country: []
      },
      disabled: false,
      inline: true
    };
  },
  methods: {
    receiveData(data) {
      console.log("来自动态表单的数据", data);
    }
  }
};
</script>
<style lang="less">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
