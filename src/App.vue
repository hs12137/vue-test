<template>
  <HelloWorldVue :msg="products[2]"/>

  <!-- 동적인 UI를 만드는 법 -->
  <!-- UI의 현재 상태를 데이터로 저장해둠 -->
  <!-- 데이터에 따라 UI가 어떻게 보일지 작성 -->
  <!-- v-if="조건식"으로 해당 태그가 보일지 안보일지 설정 -->
  <div class="black-bg" v-if="모달창열렸니">
    <div class="white-bg">
      <h4>{{원룸들[clicked].title}}</h4>
      <p>{{원룸들[clicked].content}}</p>
      <p>{{원룸들[clicked].price}}</p>
      <button @click="모달창열렸니 = false">닫기</button>
    </div>
  </div>


  <!-- v-model="변수명"을 통해서 부등호 연산 가능하도록 해줌 -->
  <div>
    <span>하루 용돈이 얼마입니까?</span>
    <input type="number" v-model="money"/>
  </div>
  <div>
    <span v-if="money < 10000">만원 미만입니다.</span>
    <span v-else-if="money < 30000">삼만원 미만입니다.</span>
    <span v-else-if="money < 50000">오만원 미만입니다.</span>
    <span v-else-if="money < 70000">칠만원 미만입니다.</span>
    <span v-else>돈 많네</span>
  </div>

  <h2>v-show 특징</h2>
  <div>
    <button @click="btnClicked">버튼</button>
  </div>
  <div v-show="isVal">
    <p>눈에 안보여도 없어진게 아님</p>
    <p>렌더링은 되었지만 style : display : none과 같은 개념</p>
  </div>
  

  <div class="menu">
    <!-- <태그 v-for="작명 in 몇회" :key="작명"> -->
    <!-- 가지고 있는 object 리스트를 집어널기 가능, 두가지 방법이 있음 -->
    <!-- <태그 v-for="작명 in 리스트이름" :key="작명"> -->
    <!-- <태그 v-for="(작명1, 작명2) in 리스트이름" :key="작명2"> -->
    <!-- 아래 방법에서 (작명1, 작명2) 중에서 첫번째 작명은 -->
    <!-- 리스트가 담고있는 데이터를 나타내고 두번째 작명은 index값을 나타냄 -->
    <a v-for="item in 메뉴들" :key="item">{{ item }}</a>
  </div>

    <!-- 데이터 바인딩 -->
    <!-- html 태그안에 데이터 바인딩시 {{변수명}} -->
    <!-- 속성 안에 데이터 바인딩 시 :속성="변수명" -->
    <!-- 데이터 바인딩 하는 이유 -->
    <!-- html에 하드코딩하면 나중에 변경이 어려움 -->
    <!-- Vue의 실시간 자동 렌더링 기능을 사용하기 위해서 -->
    <!-- 다만 애초에 바뀔일이 없으면 데이터 바인딩이 불필요 -->

    <!-- 이벤트는 @이벤트 로 설정 -->
    <!-- <button @click="자바스크립트"> -->
    <!-- <input @input="자바스크립트" -->
    <!-- 속성 안에 데이터를 넣을때는 속성앞에 : 추가 -->

    <!-- 반복문에서 index값을 i에 받아서 제목을 누르면 clicked에 i 할당해주고 할당된 값을 이용해서 모달에 상품 상세정보 출력 -->
  <div v-for="(data, i) in 원룸들" :key="i">
    <img :src="data.image" class="room-img">
    <h4 @click="모달창열렸니 = true; clicked = i">{{data.title}}</h4>
    <p>{{data.price}}</p>
    <button @click="increase(i)">허위매물신고</button><span>신고 수 : {{신고수[i]}}</span>
  </div>
</template>

<script>
//1. import 변수명 from 경로
//2. 여러개를 한번에 import 해줬다면 받을때도 변수가 하나라도 중괄호로 묶어줘야함
//iomport {변수명} or {변수1, 변수2} from 경로
//3. 변수명 설정 안해주고 import 했으면 변수명 아무거나
import data from "./assets/data.js"
import HelloWorldVue from './components/HelloWorld.vue'

export default {
  name: 'App',
  data() {
    return {
      //자주 변경될 변수들 여기 보관
      //object자료형으로 보관 ex) 변수명 : 값
      //HTML 속성도 바인딩 가능, 속성은 위에서 선언할때 :속성="데이터이름"
      price1 : 80,
      price2 : 70,
      price3 : 90,
      신고수 : [0, 0, 0, 0, 0, 0],
      스타일 : 'color : blue',
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      메뉴들 : ['Home', 'Shop', 'About'],
      모달창열렸니 : false,
      clicked : 0,
      //import 해온 데이터를 데이터 바인딩을 위해 선언
      원룸들 : data,
      money : 0,
      isVal : false,
    }
  },
  methods: {
    //함수명은 한글로 작성하면 안먹을때가 있어서 영어로 작성
    increase(index){
      this.신고수[index]++;
    },
    btnClicked(){
      this.isVal = !this.isVal
    },
  },
  components: {
    HelloWorldVue,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.menu{
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a{
  color: white;
  padding: 10px;
}
.room-img{
  width: 100%;
  margin-top: 40px;
}
body{
  margin: 0;
}
div{
  box-sizing: border-box;
}
.black-bg{
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg{
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>
