<script>
    import Header from '../components/Header.svelte';
    import MainImage from '../components/MainImage.svelte';
    import MainMessage from '../components/MainMessage.svelte';
    import Calendar from '../components/Calendar.svelte';
  
    let title = "🎉 Happy Birthday!";
    let imageUrl = "/birthday.jpeg";
    let message = "로운이의 소중한 하루를 축하합니다! 🎂";
  
    // 캘린더에 사용할 값
    let month = 2; // 3월
    let highlightedDay = 8; // 강조할 날짜 (예: 8일)
  </script>
  
  <style>
    main {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      height: 100vh;
      padding: 20px;
      background-color: #f8f9fa;
    }
  
    .calendar-container {
      margin-top: 20px;
    }
  </style>
  
  <main>
    <Header {title} />
    <MainImage {imageUrl} />
    <MainMessage {message} />
    <div class="calendar-container">
      <Calendar {month} {highlightedDay} />
    </div>
  </main>
  