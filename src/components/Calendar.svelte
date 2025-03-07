<script>
    import { onMount } from "svelte";
  
    export let month = new Date().getMonth(); // 기본값: 현재 월
    export let year = new Date().getFullYear(); // 기본값: 현재 년도
    export let highlightedDay = new Date().getDate(); // 기본값: 오늘 날짜
  
    let days = [];
    let firstDayOfMonth = new Date(year, month, 1).getDay(); // 월의 첫 번째 날의 요일
    let totalDaysInMonth = new Date(year, month + 1, 0).getDate(); // 해당 월의 총 일수
    let calendarDays = [];
  
    const getDaysInMonth = (year, month) => {
      let daysArray = [];
      let currentDay = 1;
      
      // 먼저, 첫 번째 요일까지 빈 칸을 채움 (일요일부터 시작)
      for (let i = 0; i < firstDayOfMonth; i++) {
        daysArray.push(null); // 빈 칸
      }
  
      // 날짜를 추가
      while (currentDay <= totalDaysInMonth) {
        daysArray.push(currentDay);
        currentDay++;
      }
  
      // 7일씩 그룹화하여 반환 (일요일부터 토요일까지)
      let weeks = [];
      for (let i = 0; i < daysArray.length; i += 7) {
        weeks.push(daysArray.slice(i, i + 7));
      }
  
      return weeks;
    };
  
    onMount(() => {
      calendarDays = getDaysInMonth(year, month);
    });
  </script>
  
  <style>
    .calendar {
      display: flex;
      flex-direction: column;
      align-items: center;
      background: white;
      padding: 10px;
      border-radius: 12px;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
      width: 90%;
      max-width: 320px;
    }
  
    .month {
      font-size: 1.2rem;
      font-weight: bold;
      margin-bottom: 10px;
    }
  
    .days {
      display: grid;
      grid-template-columns: repeat(7, 1fr);
      gap: 5px;
      width: 100%;
    }
  
    .day {
      width: 40px;
      height: 40px;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 6px;
      font-size: 0.9rem;
      cursor: pointer;
    }
  
    .highlighted {
      background: #ffcc00;
      font-weight: bold;
    }
  
    .day-name {
      font-size: 1rem;
      font-weight: bold;
      text-align: center;
      padding: 5px;
    }
  </style>
  
  <div class="calendar">
    <div class="month">{year}년 {month + 1}월</div>
  
    <!-- 요일 이름 표시 -->
    <div class="days">
      <div class="day-name">일</div>
      <div class="day-name">월</div>
      <div class="day-name">화</div>
      <div class="day-name">수</div>
      <div class="day-name">목</div>
      <div class="day-name">금</div>
      <div class="day-name">토</div>
    </div>
  
    <!-- 날짜 표시 -->
    {#each calendarDays as week}
      <div class="days">
        {#each week as day}
          <div class="day {day === highlightedDay ? 'highlighted' : ''}">
            {day}
          </div>
        {/each}
      </div>
    {/each}
  </div>
  