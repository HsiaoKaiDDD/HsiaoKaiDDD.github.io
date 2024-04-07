<script>
export default {
  data() {
    return {
      // count: 1,
      // className: 'red text-blue-500 text-6xl',
      // inputType: 'text',
      // changeRed: 'bg-blue-500',
      // showPassword: false,
      // newTextValue: '',
      textValue : '',
      numberValue : '',
      checkBoxValue: '',
      mixCheckBoxValue: [],
      radioValue: '',
      fileData: null,
      show: true,
      rule: 'if',
      className: 'bg-red-500',
    };
  },
  
  // function
  methods: {
    // 增加數字
    // addCount(){
    //   this.count++;
    // },
    // // 更換顏色
    // changeColor(){
    //   this.changeRed = 'bg-red-500';
    //   console.log(this.changeRed);
    // },
    // // 更換密碼顯示
    // togglePassword(){
    //   this.showPassword = !this.showPassword;
    // },
    getInputValue(e){
      console.log(e.target.value);
    },
    getDouble() {
      return 30;
    },
    // 回傳map + join字串
    getMapStr() {
      return this.mixCheckBoxValue.map(item => item + 2).join();
    },
    // 上傳檔案
    uploadFile(e) {
      const file = e.target.files[0]
      // 判斷是否為圖片
      if (file.type.includes('image/')) {
        // URL.createObjectURL(file)是將字串轉為圖片
        this.fileData = URL.createObjectURL(file);
      }
      console.log(this.fileData);
    },
  },
};
</script>

<template>
  <div class="flex flex-col gap-y-2">
    <h1 class="text-8xl font-bold">{{ count }}</h1>
    <!-- v-on 事件 -->
    <!-- <button type="button" v-on:click="addCount()">我是按鈕</button>
    <button type="button" @click="count--" class="w-full">減我</button> -->

    <!-- v-bind 屬性綁定 -->
    <!-- <div v-bind:class="className">5</div>
    <input v-bind:type="inputType" class="text-black">
    <input :type="inputType" class="text-black"> -->

    <!-- 練習1-->
    <!-- <button type="button" @click="changeColor()">按我變紅色</button>
    <div class="w-[100px] h-[100px]" :class="changeRed">
      {{ changeRed === 'bg-blue-500' ? '我現在是藍色' : '我現在是紅色' }}
    </div> -->

    <!-- 練習2 -->
    <!-- <button type="button" @click="togglePassword()">顯示/關閉密碼</button>
    <input :type="showPassword ? 'text' : 'password'" class="text-black">

    <input type="text" class="text-black" @input="(e) => getInputValue(e)"> -->

    <!-- v-model 雙向綁定-->
    <div>v-model</div>
    <!-- <input v-model="newTextValue" type="text" class="text-black"> -->
    {{ newTextValue }}
    <input v-model="textValue" type="text">
    <input v-model="numberValue" type="number">
    <input v-model="checkBoxValue" type="checkbox" :true-value="1" :false-value="0">
    <label>
      <div>{{ getMapStr() }}</div>
      <input v-model="mixCheckBoxValue" type="checkbox" :value="1">
      <input v-model="mixCheckBoxValue" type="checkbox" :value="2">
      <input v-model="mixCheckBoxValue" type="checkbox" :value="3">
    </label>

    <!-- v-model radio -->
    <label>
      男
      <input v-model="radioValue" type="radio" value="男">
    </label>
    <label>
      女
      <input v-model="radioValue" type="radio" value="女">
    </label>
    <label>
      其他
      <input v-model="radioValue" type="radio" value="其他">
    </label>
    {{radioValue}}

    <!-- 上傳檔案(多圖上傳) -->
    <input type="file" multiple accept="jpg" @change="uploadFile">
    {{ fileData?.name }}
    <img :src="fileData" alt="圖片">
    

    <!-- v-show -->
    <div v-show="show" >出現</div>

    <div v-if="rule === 'if'">{{ rule }}</div>
    <div v-else-if="rule === 'else-if'">{{ rule }}</div>
    <div v-else>沒東西</div>

    <!-- v-bind -->
    <div class="w-[100px] h-[100px]" :class="show ? 'bg-red-500' : 'bg-blue-500'"></div>
    <!-- 判斷true、false變顏色 -->
    <!-- 如果show=true，文字變黃色、如果rule=if，文字變粗體 -->
    <div class="w-[100px] h-[100px] bg-red-500'" :class="{ 'text-yellow-500': show,'font-bold': rule ==='if' }">123</div>
  </div>
  <main>
    <TheWelcome />
  </main>
</template>
