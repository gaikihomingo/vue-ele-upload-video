# vue-ele-upload-video | 使得视频上传更加容易

[![MIT Licence](https://badges.frapsoft.com/os/mit/mit.svg)](https://opensource.org/licenses/mit-license.php)
[![npm](https://img.shields.io/npm/v/vue-ele-upload-video.svg)](https://www.npmjs.com/package/vue-ele-upload-video)
[![size](https://img.shields.io/bundlephobia/minzip/vue-ele-upload-video.svg)](https://www.npmjs.com/package/vue-ele-upload-video)
[![download](https://img.shields.io/npm/dw/vue-ele-upload-video.svg)](https://npmcharts.com/compare/vue-ele-upload-video?minimal=true)

## 介绍

vue-ele-upload-video 对 element-ui 中 upload 组件进一步封装，使得视频上传更加容易

## 效果图

![效果图](./public/example.gif)

## 在线示例

[https://codepen.io/dream2023/pen/ZNVvBg/](https://codepen.io/dream2023/pen/ZNVvBg/)

## 安装

```bash
npm install vue-ele-upload-video --save
```

## 使用

```js
// 全局引入
import EleUploadVideo from 'vue-ele-upload-video'
Vue.component(EleUploadVideo.name, EleUploadVideo)
```

```js
// 局部引入
import EleUploadVideo from 'vue-ele-upload-video'
export default {
  components: {
    EleUploadVideo
  }
}
```

## 示例(上传到七牛云)

```html
<template>
  <ele-upload-video
    :data="{
      token: token
    }"
    :fileSize="20"
    @error="handleUploadError"
    :responseFn="handleResponse"
    style="margin: 50px"
    action="https://upload.qiniup.com/"
    v-model="video"
  />
</template>

<script>
  export default {
    data() {
      return {
        // 上传时需要携带后台请求的token
        token: 'xxxx',
        video: ''
      }
    },
    methods: {
      handleUploadError(error) {
        console.log('error', error)
      },
      handleResponse(response) {
        return 'https://www.xxx.com/upload/video/' + response.id
      }
    }
  }
</script>
```

## Props 参数

```js
Props: {
  // value
  Value: {
    Type: String
  },
  // Upload address
  Action: {
    Type: String,
    Required: true
  },
  // response handler
  responseFn: Function,
  // file size limit (Mb)
  fileSize: {
    Type: Number
  },
  // display width (px)
  Width: {
    Type: Number,
    Default: 360
  },
  // display height (default auto)
  Height: {
    Type: Number
  },
  // Is the prompt displayed?
  isShowTip: {
    Type: Boolean,
    Default: true
  },
  // file type
  fileType: {
    Type: Array
  },
    / / Set the request header for uploading (same official website)
  Headers: Object,
  / / Support to send cookie credential information (same official website)
  withCredentials: {
    Type: Boolean,
    Default: false
  },
  // Additional parameters attached when uploading (same official website)
  Data: {
    Type: Object
  },
  // Uploaded file field name (same official website)
  Name: {
    Type: String,
    Default: 'file'
  },
    / / Override the default upload behavior, you can customize the implementation of the upload (same official website)
  httpRequest: Function,
  // Accept the uploaded file type (this parameter is invalid in thumbnail-mode mode) (same official website)
  Accept: String
}
```

## 参考链接

- [element-ui upload 组件](https://element.eleme.cn/#/zh-CN/component/upload)
- [element-ui progress 组件](https://element.eleme.cn/#/zh-CN/component/progress)
