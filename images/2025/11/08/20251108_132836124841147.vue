<template>
  <div>
    <el-form ref="elForm" :model="formData" :rules="rules" size="medium" label-width="100px">
      <el-form-item label="手机号" prop="mobile">
        <el-input v-model="formData.mobile" placeholder="请输入手机号" :maxlength="11" show-word-limit clearable
          prefix-icon='el-icon-mobile' :style="{width: '100%'}"></el-input>
      </el-form-item>
      <el-form-item label="单行文本" prop="field107">
        <el-input v-model="formData.field107" placeholder="请输入单行文本" clearable :style="{width: '100%'}">
        </el-input>
      </el-form-item>
      <el-form-item label="下拉选择" prop="field101">
        <el-select v-model="formData.field101" placeholder="请选择下拉选择" clearable :style="{width: '100%'}">
          <el-option v-for="(item, index) in field101Options" :key="index" :label="item.label"
            :value="item.value" :disabled="item.disabled"></el-option>
        </el-select>
      </el-form-item>
      <el-form-item label="级联选择" prop="field105">
        <el-cascader v-model="formData.field105" :options="field105Options" :props="field105Props"
          :style="{width: '100%'}" placeholder="请选择级联选择" clearable></el-cascader>
      </el-form-item>
      <el-form-item label="滑块" prop="field106" required>
        <el-slider :max='100' :step='1' v-model="formData.field106"></el-slider>
      </el-form-item>
      <el-form-item label="滑块" prop="field103" required>
        <el-slider :max='100' :step='1' v-model="formData.field103"></el-slider>
      </el-form-item>
      <el-form-item label="下拉选择" prop="field102">
        <el-select v-model="formData.field102" placeholder="请选择下拉选择" clearable :style="{width: '100%'}">
          <el-option v-for="(item, index) in field102Options" :key="index" :label="item.label"
            :value="item.value" :disabled="item.disabled"></el-option>
        </el-select>
      </el-form-item>
      <el-form-item label="日期选择" prop="field108">
        <el-date-picker v-model="formData.field108" format="yyyy-MM-dd" value-format="yyyy-MM-dd"
          :style="{width: '100%'}" placeholder="请选择日期选择" clearable></el-date-picker>
      </el-form-item>
      <el-form-item label="时间范围" prop="field104">
        <el-time-picker v-model="formData.field104" is-range format="HH:mm:ss" value-format="HH:mm:ss"
          :style="{width: '100%'}" start-placeholder="开始时间" end-placeholder="结束时间" range-separator="至"
          clearable></el-time-picker>
      </el-form-item>
      <el-form-item size="large">
        <el-button type="primary" @click="submitForm">提交</el-button>
        <el-button @click="resetForm">重置</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>
<script>
export default {
  components: {},
  props: [],
  data() {
    return {
      formData: {
        mobile: '',
        field107: undefined,
        field101: undefined,
        field105: [],
        field106: 0,
        field103: 0,
        field102: undefined,
        field108: null,
        field104: ["16:52:08", "17:54:08"],
      },
      rules: {
        mobile: [{
          required: true,
          message: '请输入手机号',
          trigger: 'blur'
        }, {
          pattern: /^1(3|4|5|7|8|9)\d{9}$/,
          message: '手机号格式错误',
          trigger: 'blur'
        }],
        field107: [{
          required: true,
          message: '请输入单行文本',
          trigger: 'blur'
        }],
        field101: [{
          required: true,
          message: '请选择下拉选择',
          trigger: 'change'
        }],
        field105: [{
          required: true,
          type: 'array',
          message: '请至少选择一个field105',
          trigger: 'change'
        }],
        field102: [{
          required: true,
          message: '请选择下拉选择',
          trigger: 'change'
        }],
        field108: [{
          required: true,
          message: '请选择日期选择',
          trigger: 'change'
        }],
        field104: [{
          required: true,
          type: 'array',
          message: '请至少选择一个field104',
          trigger: 'change'
        }],
      },
      field101Options: [{
        "label": "选项一",
        "value": 1
      }, {
        "label": "选项二",
        "value": 2
      }],
      field105Options: [],
      field102Options: [{
        "label": "选项一",
        "value": 1
      }, {
        "label": "选项二",
        "value": 2
      }],
      field105Props: {
        "multiple": false
      },
    }
  },
  computed: {},
  watch: {},
  created() {},
  mounted() {},
  methods: {
    submitForm() {
      this.$refs['elForm'].validate(valid => {
        if (!valid) return
        // TODO 提交表单
      })
    },
    resetForm() {
      this.$refs['elForm'].resetFields()
    },
    getField105Options() {
      // TODO 发起请求获取数据
      this.field105Options
    },
  }
}

</script>
<style>
</style>
