<template>
  <el-card
    header="ele-form-quill-editor 演示"
    shadow="never"
    style="max-width: 1250px;margin: 20px auto;"
  >
    <ele-form
      :form-data="formData"
      :form-desc="formDesc"
      :request-fn="handleRequest"
      :span="22"
      @request-success="handleSuccess"
    />
  </el-card>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      formData: {},
      formDesc: {
        content: {
          label: '文章内容',
          type: 'quill-editor',
          attrs: {
            action: 'https://www.mocky.io/v2/5cc8019d300000980a055e76',
            responseFn (response, file) {
              // 因为是 mock 地址, 总是返回同一张图片URL
              return response.url
            }
          }
        }
      }
    }
  },
  methods: {
    handleRequest (data) {
      console.log(data)
      return Promise.resolve()
    },
    handleSuccess () {
      this.$message.success('提交成功')
    }
  },
  mounted () {}
}
</script>

<style>
body {
  background-color: #f0f2f5;
}
</style>
