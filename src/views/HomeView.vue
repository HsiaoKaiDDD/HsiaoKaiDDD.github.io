<script>
export default {
  data() {
    return {
      count: 1,
      className: 'red text-blue-500 text-6xl',
      inputType: 'text',
      changeRed: 'bg-blue-500',
      showPassword: false,
      newTextValue: '',
    };
  },
  
  // function
  methods: {
    // 增加數字
    addCount(){
      this.count++;
    },
    // 更換顏色
    changeColor(){
      this.changeRed = 'bg-red-500';
      console.log(this.changeRed);
    },
    // 更換密碼顯示
    togglePassword(){
      this.showPassword = !this.showPassword;
    },
    getInputValue(e){
      console.log(e.target.value);
    }
  },
};
</script>

<template>
  <div class="flex flex-col gap-y-2">
    <h1 class="text-8xl font-bold">{{ count }}</h1>
    <!-- v-on 事件 -->
    <button type="button" v-on:click="addCount()">我是按鈕</button>
    <button type="button" @click="count--" class="w-full">減我</button>

    <!-- v-bind 屬性綁定 -->
    <div v-bind:class="className">5</div>
    <input v-bind:type="inputType" class="text-black">
    <input :type="inputType" class="text-black">

    <!-- 練習1-->
    <button type="button" @click="changeColor()">按我變紅色</button>
    <div class="w-[100px] h-[100px]" :class="changeRed">
      {{ changeRed === 'bg-blue-500' ? '我現在是藍色' : '我現在是紅色' }}
    </div>

    <!-- 練習2 -->
    <button type="button" @click="togglePassword()">顯示/關閉密碼</button>
    <input :type="showPassword ? 'text' : 'password'" class="text-black">

    <input type="text" class="text-black" @input="(e) => getInputValue(e)">

    <!-- v-model 雙向綁定-->
    <div>v-model</div>
    <input v-model="newTextValue" type="text" class="text-black">
    {{ newTextValue }}
  </div>
  <main>
    <TheWelcome />
  </main>
</template>
