<script>
export default {
  // 放變數
  data() {
    return {
      oooo: 25,
      count: 1,
      className: 'red text-blue-500 text-6xl',
      inputType: 'text',
      changeRed: 'bg-blue-500',
      showPassword: false,
      newTextValue: '',
      arr: [1,2,3],
      // workArr:[
      //   {"1",'兆凱','b23333585','man','0905411895'},
      //   {'2','5'}
      // ]
      // ['eric','man','06089845'],
      selectedTab: '',
      userData: []
    };
  },

  computed: {
    getDoubleNum() {
      return this.oooo * 2;
    },
    filterUserData() {
      if(!this.selectedTab) {
        return this.userData;
      }
      return this.userData.filter(user => user.gender === this.selectedTab);
    },
  },
  mounted() {
    this.userData = [
      {
        id:1,
        name: 'stan',
        idNumber: 'B159875456',
        gender: 'man',
        phone: '0908411568',
      },
      {
        id:2,
        name: 'eric',
        idNumber: 'B1589875456',
        gender: 'man',
        phone: '09084115778',
      },
      {
        id:3,
        name: 'opopop',
        idNumber: 'B1593575456',
        gender: 'man',
        phone: '09084118878',
      },
      {
        id:4,
        name: 'hhhhhw',
        idNumber: 'B15988456',
        gender: 'woman',
        phone: '0908447568',
      },
    ]
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
    // 篩選男女
    // filterData(gender) {
    //   console.log("筛选性别:", gender);
    //   this.userData = this.userData.filter(user => user.gender === gender);
    //   console.log(this.userData);
    // },

    getInputValue(e){
      console.log(e.target.value);
    },
    getDouble() {
      return 30;
    },
    // 回傳map + join字串
    // getMapStr() {
    //   return this.mixCheckBoxValue.map(item => item + 2).join();
    // },
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

    // 新增陣列
    addItem() {
      // 當前面是undefined時回傳??後面的值
      const lastItem = this.arr[this.arr.length - 1] ?? 0;
      this.arr.push(lastItem - 1);

      // 空字串變布林值也是false
      
      const b = '';
      console.log(Boolean(b))
      
    },
    // 刪除陣列
    deleteItem() {
      this.arr.pop();
    },
    deleteUserData(id) {
      // this.userData.splice(index,1);
      this.userData = this.userData.filter((user) => user.id !== id);
    },

    changeTab(tab) {
      this.selectedTab = tab;
    }
  },
};
</script>

<template>
  <!-- computed -->
  {{ getDoubleNum }}
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
    <!-- <label>
      <div>{{ getMapStr() }}</div>
      <input v-model="mixCheckBoxValue" type="checkbox" :value="1">
      <input v-model="mixCheckBoxValue" type="checkbox" :value="2">
      <input v-model="mixCheckBoxValue" type="checkbox" :value="3">
    </label> -->

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

    <div v-for="(item, index) in arr" :key="index" class="text-white text-2xl">{{ item }}</div>

    <button type="button" @click="addItem()">新增</button>
    <button type="button" @click="deleteItem()">刪除</button>

    <!-- <div class="w-full flex flex-wrap border-[1px]">
      <div class=" w-1/6 h-[20px]">編號</div>
      <div class=" w-1/6 h-[20px]">姓名</div>
      <div class=" w-1/6 h-[20px]">身分證</div>
      <div class=" w-1/6 h-[20px]">性別</div>
      <div class=" w-1/6 h-[20px]">電話</div>
      <div class=" w-1/6 h-[20px]">功能</div> -->
      <!-- <div v-for="(item, index) in workArr" :key="index" class="border-[0.5px]  h-[20px]">
        {{ index + 1 }}
        {{ item }}
      </div>
      <button type="button" >刪除</button> -->
    <!-- </div> -->
    
    <button type="button" @click="changeTab()">不限</button>
    <button type="button" @click="changeTab('man')">男</button>
    <button type="button" @click="changeTab('woman')">女</button>
    <table class="border-[1px]">
        <thead>
          <tr>
            <th>編號</th>
            <th>姓名</th>
            <th>身分證字號</th>
            <th>姓別</th>
            <th>功能</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(user, index) in filterUserData" :key="index" class="text-center">
            <td>{{ user.id }}</td>
            <td>{{ user.name }}</td>
            <td>{{ user.idNumber }}</td>
            <td>{{ user.gender === 'man' ? '男' : '女' }}</td>
            <td>
              <button type="button" @click="deleteUserData(user.id)">刪除</button>
            </td>
          </tr>
        </tbody>
      </table>
  </div>
  <main>
    <TheWelcome />
  </main>
</template>
