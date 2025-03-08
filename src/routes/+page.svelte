<script>
    import { writable } from 'svelte/store';
    import Header from '../components/Header.svelte';
    import MainImage from '../components/MainImage.svelte';
    import MainMessage from '../components/MainMessage.svelte';
    import Calendar from '../components/Calendar.svelte';
    import AnimationFrame from '../components/AnimationFrame.svelte';
  
    let title = "🎉 Happy Birthday!";
    let imageUrl1 = "/main.JPG";
    let imageUrl2 = "/birthday.png";
    let imageUrl3 = "/birthday2.JPG";
    let imageUrl4 = "/main2.png";
    let imageUrl5 = "/main3.jpeg";
    let imageUrl6 = "/main4.png";
    let imageUrl7 = "/main5.jpeg";
    let message1 = "로운이의 11살 생일을 축하합니다! 🎂";
    let message2 = "로운이를 사랑하는 삼촌, 숙모가";
    let message3 = "때론 슬프거나 마음대로 되지 않는 일도 있겠지만,"
    let message4 = "그 뒤엔 어김없이 행복하고 잘 풀리는 순간이 찾아올 거야.";
    let message5 = "그러니까 언제나 즐겁고 신나게, 매 순간을 소중히 살아가길 바라!";
    let message6 = "로운이 너무 보고 싶네~ 남은 기간 건강히 잘 지내다가,";
    let message7 = "한국오면 맛있는거 먹으러 가자~~~";

	const isHeartMode = writable(true);

    function toggleHeartMode() {
		isHeartMode.update(value => !value);
	}
  
    // 캘린더에 사용할 값
    let month = 2; // 3월
    let highlightedDay = 8; // 강조할 날짜 (예: 8일)
  </script>
  
  <style>
    main {
       display: flex;
       flex-direction: column;  
       align-items: center;
       justify-content: flex-start;  
       text-align: center;
       padding: 20px;
       background-color: #f8f9fa;
       height: 100%;  
       overflow-y: auto;  
    }

  
    .calendar-container {
      margin-top: 20px;
    }

  </style>
  
  <main>
    <Header {title} />
    <MainImage imageUrl={imageUrl1} />
    <MainImage imageUrl={imageUrl2} />
    <MainImage imageUrl={imageUrl3} />
    <MainImage imageUrl={imageUrl4} />
    <MainImage imageUrl={imageUrl5} />
    <MainImage imageUrl={imageUrl6} />
    <MainImage imageUrl={imageUrl7} />
    <div class="heart-icon" on:click={toggleHeartMode}>
    ❤️
    </div>
    <MainMessage message={message1} />
    <MainMessage message={message2} />
    <div class="calendar-container">
      <Calendar {month} {highlightedDay} />
    </div>
    <MainMessage message={message3} />
    <MainMessage message={message4} />
    <MainMessage message={message5} />
    <MainMessage message={message6} />
    <MainMessage message={message7} />
    <AnimationFrame {isHeartMode}></AnimationFrame>
  </main>
  