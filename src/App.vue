<template>

  <div class="menu">
    <!-- <태그 v-for="작명 in 몇회" :key="작명"> -->
    <!-- 가지고 있는 object 리스트를 집어널기 가능, 두가지 방법이 있음 -->
    <!-- <태그 v-for="작명 in 리스트이름" :key="작명"> -->
    <!-- <태그 v-for="(작명1, 작명2) in 리스트이름" :key="작명2"> -->
    <!-- 아래 방법에서 (작명1, 작명2) 중에서 첫번째 작명은 -->
    <!-- 리스트가 담고있는 데이터를 나타내고 두번째 작명은 index값을 나타냄 -->
    <a v-for="a in 메뉴들" :key="a">{{ a }}</a>
    <a v-for="(a, i) in 메뉴들" :key="i">{{ i }}. {{ a }}</a>
  </div>


  <div>
    <h4 class="red" :style="스타일">aaa{{products[0]}}</h4>
    <!-- 데이터 바인딩 - 중괄호 2개 사이에 변수명 입력 {{ 변수명 }} -->
    <!-- 데이터 바인딩 하는 이유 -->
    <!-- html에 하드코딩하면 나중에 변경이 어려움 -->
    <!-- Vue의 실시간 자동 렌더링 기능을 사용하기 위해서 -->
    <!-- 다만 애초에 바뀔일이 없으면 데이터 바인딩이 불필요 -->
    <p>{{ price1 }} 만원</p>
  </div>
  <div>
    <h4>{{products[1]}}</h4>
    <p>{{ price2 }} 만원</p>
  </div>
  <div>
    <h4>{{products[2]}}</h4>
    <p>{{ price3 }} 만원</p>
    <p>asdas</p>
  </div>

  <div v-for="p in products" :key="p">
    <h4>{{p}}</h4>
    <p>50 만원</p>
    <p>asasasadasdsaad</p>
  </div>
</template>

<script>

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
      스타일 : 'color : blue',
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      메뉴들 : ['Home', 'Shop', 'About'],
    }
  },
  components: {
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
</style>
