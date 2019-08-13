<template>
  <div>
    <div class="card">
      <h3 class="card-header" id="monthAndYear"></h3>
      <div>
        <h1 id="showDate">
          <!-- {{myDate}} -->
        </h1>
      </div>
      <thead>
        <tr id="weekHeaderID">
          <th class="weekHeader">Sunday</th>
          <th class="weekHeader">Monday</th>
          <th class="weekHeader">Tuesday</th>
          <th class="weekHeader">Wednesday</th>
          <th class="weekHeader">Thursday</th>
          <th class="weekHeader">Friday</th>
          <th class="weekHeader">Saturday</th>
        </tr>
      </thead>
      <tbody>
        <tr id="week1">
          <td class="Sun1"></td>
          <td class="Mon1"></td>
          <td class="Tue1"></td>
          <td class="Wed1"></td>
          <td class="Thu1"></td>
          <td class="Fri1"></td>
          <td class="Sat1"></td>
        </tr>
        <tr id="week2">
          <td class="Sun2"></td>
          <td class="Mon2"></td>
          <td class="Tue2"></td>
          <td class="Wed2"></td>
          <td class="Thu2"></td>
          <td class="Fri2"></td>
          <td class="Sat2"></td>
        </tr>
        <tr id="week3">
          <td class="Sun3"></td>
          <td class="Mon3"></td>
          <td class="Tue3"></td>
          <td class="Wed3"></td>
          <td class="Thu3"></td>
          <td class="Fri3"></td>
          <td class="Sat3"></td>
        </tr>
        <tr id="week4">
          <td class="Sun4"></td>
          <td class="Mon4"></td>
          <td class="Tue4"></td>
          <td class="Wed4"></td>
          <td class="Thu4"></td>
          <td class="Fri4"></td>
          <td class="Sat4"></td>
        </tr>
        <tr id="week5">
          <td class="Sun5"></td>
          <td class="Mon5"></td>
          <td class="Tue5"></td>
          <td class="Wed5"></td>
          <td class="Thu5"></td>
          <td class="Fri5"></td>
          <td class="Sat5"></td>
        </tr>
        <tr id="week6">
          <td class="Sun6"></td>
          <td class="Mon6"></td>
          <td class="Tue6"></td>
          <td class="Wed6"></td>
          <td class="Thu6"></td>
          <td class="Fri6"></td>
          <td class="Sat6"></td>
        </tr>
      </tbody>
    </div>
  </div>
</template>

<script>

export default {
  name: "Calendar",
  methods: {
    placeDatesOnCalendar (numDaysInMonth, startingDay) {
      var dayOfWeek = ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'];
      var weekIncrementer = 1;
      const daysInAWeek = 7;
      
      var thisWeek;
      var target;
      
      var dayIndex = numDaysInMonth%numDaysInMonth;
      
      console.log(new Date().getDate());

      for (dayIndex; dayIndex < numDaysInMonth; dayIndex++) {
        var currentWeek = (startingDay+dayIndex)%daysInAWeek;

        if ((currentWeek) == 0) {
          weekIncrementer++;
        }
        if (dayIndex+1 == (new Date().getDate())) {
          console.log("check for Current Day")

          thisWeek = document.getElementById("week"+weekIncrementer);
          target = thisWeek.getElementsByClassName(dayOfWeek[currentWeek]+weekIncrementer)[0];
          target.textContent = dayIndex+1;
          target = target.setAttribute(
            "style", "color: white; background: blue; font-weight bold"
          );
          // target = target.style.background  = 'blue';
          
          //(dayIndex+1);
        } else {
          console.log("just another Day")
          thisWeek = document.getElementById("week"+weekIncrementer);
          target = thisWeek.getElementsByClassName(dayOfWeek[currentWeek]+weekIncrementer)[0];

          target.textContent = dayIndex+1;
        }
      }
    },
    getFirstWeekDay(startingDay, numDaysInMonth) {
      // start in week one.
      var weekOne = document.getElementById("week1");

      switch(startingDay) {
        case 0:
          this.placeDatesOnCalendar(numDaysInMonth, startingDay);
          break;
        case 1:
          this.placeDatesOnCalendar(numDaysInMonth, startingDay);
          break;
        case 2:
          this.placeDatesOnCalendar(numDaysInMonth, startingDay);
          break;
        case 3:
          this.placeDatesOnCalendar(numDaysInMonth, startingDay);
          break;
        case 4:
          this.placeDatesOnCalendar(numDaysInMonth, startingDay);
          break;
        case 5:
          this.placeDatesOnCalendar(numDaysInMonth, startingDay);
          break;
        case 6:
          this.placeDatesOnCalendar(numDaysInMonth);
          break;
        default:
          console.log("Error undefined:" + startingDay);
          break;
      }
    }
  },
  mounted() {
    var date = new Date();
    const weeksInCalendar = 6;
    var months = ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"];
    var weekday = ["Sunday", "Monday", "Tueday", "Wednesday", "Thursday", "Friday", "Saturday"];

    function daysInMonth( month, year ) {
      return new Date(year, month, 0).getDate();
    }

    var startingDay = new Date(date.getFullYear() + "-" + (date.getMonth() + 1)).getDay();
    var currentDayOfWeek = date.getDay();
    var numDaysInMonth = daysInMonth(date.getMonth(), date.getFullYear())
    this.getFirstWeekDay(startingDay, numDaysInMonth);

    // console.log(new Date().toISOString().slice(0,10));
  }
}

</script>

<style>
table, th, td {
  border: 1px solid black;
}
th, td {
  padding: 30px;
  
  margin: 20px;
}
</style>