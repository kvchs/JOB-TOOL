<template>
  <div class="app-container">
    <aside>
      此工具用于VR视频上传
    </aside>

    <el-form ref="form" :model="form" label-width="80px">

      <el-form-item label="视频格式">
        <el-checkbox-group v-model="form.type">
          <el-checkbox label="180全景(110)" name="type" />
          <el-checkbox label="180左右(111)" name="type" />
          <el-checkbox label="180上下(112)" name="type" />
          <el-checkbox label="360全景(120)" name="type" />
          <el-checkbox label="360左右(121)" name="type" />
          <el-checkbox label="360上下(122)" name="type" />
          <el-checkbox label="非全景(130)" name="type" />
          <el-checkbox label="3D左右(131)" name="type" />
          <el-checkbox label="3D上下(132)" name="type" />
        </el-checkbox-group>
      </el-form-item>
      <el-form-item label="视频类型">
        <el-radio-group v-model="form.resource">
          <el-radio label="作品" />
          <el-radio label="广告" />
        </el-radio-group>
      </el-form-item>

      <el-form-item label="上传文件">
        <el-upload
          class="upload-demo"
          drag
          action="https://jsonplaceholder.typicode.com/posts/"
          multiple
        >
          <i class="el-icon-upload" />
          <div class="el-upload__text">将文件拖到此处，或<em>点击上传</em></div>
          <div slot="tip" class="el-upload__tip">只能支持.mp4格式</div>
        </el-upload>

      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="onSubmit">立即上传</el-button>
      </el-form-item>
    </el-form>

    <aside>
      此工具用于将视频推入Feed流
    </aside>
    <el-form>

      <el-form-item>

        <el-input v-model="input" placeholder="请输入作品ID（workId）" />
      </el-form-item>

      <el-form-item>
        <el-button type="primary" @click="onSubmit">立即推送</el-button>
      </el-form-item>

    </el-form>

  </div>
</template>

<script>
import Driver from 'driver.js' // import driver.js
import 'driver.js/dist/driver.min.css' // import driver.js css
import steps from './steps'

export default {
  name: 'Guide',
  data() {
    return {
      driver: null,
      form: {
        name: '',
        region: '',
        date1: '',
        date2: '',
        delivery: false,
        type: [],
        resource: '',
        desc: ''
      }
    }
  },
  mounted() {
    this.driver = new Driver()
  },
  methods: {
    guide() {
      this.driver.defineSteps(steps)
      this.driver.start()
    }
  }
}
</script>
