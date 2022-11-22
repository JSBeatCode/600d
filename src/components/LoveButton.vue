<template>
  <div class="col">
    <br>
    <br>
    <h1 style="color:white">슬기♥승동 "{{remainTime}}" 축하해!♥</h1>
    <br>
    <br>
    <div style="position:relative">
      <div class="heart-btn">
        <div class="content">
          <span class="heart"></span>
          <span class="text"></span>
          <span class="numb"></span>
        </div>
      </div>
    </div>
    <br>
    <br>
    <img src="../assets/jjidol1.jpg" class="rounded" alt="..." style="width:100px;height:100px">
    <img src="../assets/nana1.jpg" class="rounded" alt="..." style="width:100px;height:100px">
    <img src="../assets/nana-jjidol1.jpg" class="rounded" alt="..." style="width:100px;height:100px">
    <br>
    <br>
  </div>
  <div class="col">
    <div id="carouselExampleInterval" class="carousel slide" data-bs-ride="carousel">
      <div class="carousel-indicators">
        <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="0" class="active"
          aria-current="true" aria-label="Slide 1"></button>
        <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="1"
          aria-label="Slide 2"></button>
        <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="2"
          aria-label="Slide 3"></button>
      </div>
      <div class="carousel-inner">
        <div class="carousel-item" data-bs-interval="3000">

            <img src="../assets/love1.jpg" class="rounded" alt="..." style="width:50%;height:50%">
            <rect width="100%" height="100%" fill="#777"></rect>

        </div>
        <div class="carousel-item" data-bs-interval="3000">
          <img src="../assets/love2.jpg" class="rounded" alt="..." style="width:50%;height:50%">

            <rect width="100%" height="100%" fill="#666"></rect>

        </div>
        <div class="carousel-item active" data-bs-interval="3000">
          <img src="../assets/love3.jpg" class="rounded" alt="..." style="width:50%;height:50%">

            <rect width="100%" height="100%" fill="#555"></rect>


        </div>
      </div>
      <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleInterval"
        data-bs-slide="prev">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Previous</span>
      </button>
      <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleInterval"
        data-bs-slide="next">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Next</span>
      </button>
    </div>
  </div>
  <br>
  <br>

</template>
<script>
import {ref, onMounted} from 'vue'

export default {
  setup () {
    const remainTime = ref('');
    const countDown = ref(10)
    const getDate = () => {
      setTimeout(() => {
        const masTime = new Date('2021-03-03 00:00:00');
        const todayTime = new Date();
      
        const diff = todayTime - masTime;

        const diffDay = (Math.floor(diff / (1000*60*60*24)));
        const diffHour = Math.floor((diff / (1000*60*60)) % 24);
        const diffMin = Math.floor((diff / (1000*60)) % 60);
        const diffSec = Math.floor(diff / 1000 % 60);
      
        // const remainTime = `${diffDay}일`;
        // console.log('jsdno0 debug1', diffDay)
        remainTime.value = `${diffDay}일 ${diffHour}시간 ${diffMin}분 ${diffSec}초`;
        // console.log('jsdno0 debug2', remainTime.value)
        // if(diffDay < 600){
          getDate()
        // }
      }, 1000);
    }
    const countDownTimer = () => {
      // console.log('jsdno0 debug2', countDown.value)
                if (countDown.value > 0) {
                    setTimeout(() => {
                      console.log('jsdno0 debug1', countDown.value)
                      countDown.value -= 1
                        countDownTimer()
                    }, 1000)
                }
            }
    onMounted(()=>{
      // console.log('jsdno0 debug3', countDown.value)
      getDate()
    })

    return {
      remainTime,
      getDate,
      countDown,
      countDownTimer
    }
  },
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Montserrat:600&display=swap');

.read-the-docs {
  color: #888;
}

.heart-btn {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.content {
  padding: 13px 16px;
  display: flex;
  border: 2px solid #eae2e1;
  border-radius: 5px;
  cursor: pointer;
}

.content.heart-active {
  border-color: #f9b9c4;
  background: #fbd0d8;
}


.heart {
  position: absolute;
  background: url("../assets/img.png") no-repeat;
  background-position: left;
  background-size: 2900%;
  height: 90px;
  width: 90px;
  top: 50%;
  left: 21%;
  transform: translate(-50%, -50%);
}

.text {
  font-size: 21px;
  margin-left: 30px;
  color: grey;
  font-family: 'Montserrat', sans-serif;
}

.numb:before {
  content: 'I Love You';
  font-size: 21px;
  margin-left: 7px;
  font-weight: 600;
  color: #9C9496;
  font-family: sans-serif;
}

.numb.heart-active:before {
  content: 'Forever';
  color: #000;
}

.text.heart-active {
  color: #000;
}

.heart.heart-active {
  animation: animate .8s steps(28) 1;
  background-position: right;
}

@keyframes animate {
  0% {
    background-position: left;
  }

  100% {
    background-position: right;
  }
}
</style>
