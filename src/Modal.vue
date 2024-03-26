<template>
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
</template>

<script>
export default {
    name: 'Modal',
}
</script>
<style>
    
</style>