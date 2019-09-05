<template>
  <section>
    <el-form :disabled="disabled" :inline="inline">
      <template v-for="item in field">
        <el-form-item :prop="item.name" :label="item.label" :key="item.name">
          <!-- 文本框 -->
          <template v-if="item.type ==='text'">
            <el-input
              :name="item.name"
              v-model="form[item.name]"
              type="text"
              :placeholder="item.placeholder"
              :size="item.size"
            />
          </template>
          <!-- 单选按钮 -->
          <template v-else-if="item.type === 'radio'">
            <template v-for="radioItem in item.options.list">
              <el-radio v-model="form[item.name]" :label="radioItem.label" :key="radioItem.value"></el-radio>
            </template>
          </template>
          <!-- 下拉选择框 -->
          <template v-else-if="item.type==='select'">
            <el-select v-model="form[item.name]" :placeholder="item.placeholder">
              <template v-for="optionItem in item.options.list">
                <el-option
                  :label="optionItem.label"
                  :value="optionItem.value"
                  :key="optionItem.value"
                />
              </template>
            </el-select>
          </template>
          <!-- 复选框 -->
          <template v-else-if="item.type === 'checkbox'">
            <el-checkbox-group v-model="form[item.name]">
              <template v-for="countryItem in item.options.list">
                <el-checkbox :label="countryItem.label" :key="countryItem.value"></el-checkbox>
              </template>
            </el-checkbox-group>
          </template>
          <!-- 按钮 -->
          <template v-else-if="item.type ==='button'">
            <el-button type="primary" v-text="item.text" @click="eventHandler"></el-button>
          </template>
          <!-- 非表单元素 -->
          <slot :name="item.name" v-if="item.isSlot"></slot>
        </el-form-item>
      </template>
    </el-form>
  </section>
</template>

<script>
export default {
  name: "dynamic-form",
  data() {
    return {};
  },
  props: {
    field: {
      type: Object,
      default: () => {
        return {};
      }
    },
    form: {
      type: Object,
      default: () => {
        return {};
      }
    },
    disabled: {
      type: Boolean,
      default: false
    },
    inline: {
      type: Boolean,
      default: true
    }
  },
  methods: {
    eventHandler() {
      this.$emit("updateForm", this.form);
    }
  }
};
</script>
