<template>
  <div class="detail">
    <el-form ref="postForm">
      <sticky :class-name="'sub-navbar'">
        <el-button v-if="isEdit" @click="showGuide">显示帮助</el-button>
        <el-button v-loading="loading" type="success" @click="submitForm">{{ isEdit ? '编辑电子书' : '新增电子书' }}</el-button>
      </sticky>
      <div class="detail-container">
        <el-row>
          <warning />
          <el-col :span="24">
            <ebook-upload
              :file-list="fileList"
              :disabled="isEdit"
              @onSuccess="onUploadSuccess"
              @onRemove="onUploadRemove"
            />
          </el-col>
          <el-col />
        </el-row>
      </div>
    </el-form>
  </div>
</template>
<script>

import Sticky from '../../../components/Sticky/index'
import EbookUpload from '../../../components/EbookUpload'
import Warning from './Warning'
export default {
  components: { Sticky, Warning, EbookUpload },
  props: {
    isEdit: Boolean
  },
  data() {
    return {
      loading: false,
      postForm: {
        status: 'draft'
      },
      fileList: []
    }
  },
  methods: {
    submitForm() {
      this.loading = true
      setTimeout(() => {
        this.loading = false
      }, 1000)
    },
    showGuide() {
      console.log('show guide ...')
    },
    onUploadSuccess() {
      console.log('onUploadSuccess')
    },
    onUploadRemove() {
      console.log('onUploadRemove')
    }
  }
}
</script>
