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
    let message1 = "로운이의 소중한 하루를 축하합니다! 🎂";
    let message2 = "사랑하는 삼촌, 이모가";
    let message3 = "한국오면 맛있는거 먹으러가자~~~";

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
    <div class="heart-icon" on:click={toggleHeartMode}>
    ❤️
    </div>
    <MainMessage message={message1} />
    <MainMessage message={message2} />
    <div class="calendar-container">
      <Calendar {month} {highlightedDay} />
    </div>
    <MainMessage message={message3} />
    <AnimationFrame {isHeartMode}></AnimationFrame>
  </main>
  