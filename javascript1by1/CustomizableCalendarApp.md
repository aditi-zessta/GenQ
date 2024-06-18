26. Customizable Calendar App
Description: Create a customizable calendar where users can add, edit, and delete events. Skills Tested: DOM manipulation, date handling, event handling. Features:

Display a monthly view with days and dates.
Allow users to add events with titles, descriptions, and times.
Edit and delete events.
Highlight days with events. """
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Customizable Calendar App</title>
    <style>
        .calendar {
            display: grid;
            grid-template-columns: repeat(7, 1fr);
        }
        .day {
            border: 1px solid #ddd;
            padding: 10px;
        }
        .event {
            background-color: yellow;
            margin-top: 5px;
        }
    </style>
</head>
<body>
    <h1>Customizable Calendar App</h1>
    <div class="calendar" id="calendar"></div>


    <script>
        const calendar = document.getElementById('calendar');


        function createCalendar(year, month) {
            calendar.innerHTML = '';
            const date = new Date(year, month, 1);
            const daysInMonth = new Date(year, month + 1, 0).getDate();


            for (let i = 1; i <= daysInMonth; i++) {
                const day = document.createElement('div');
                day.className = 'day';
                day.innerHTML = i;


                day.addEventListener('click', () => addEvent(day));
                calendar.appendChild(day);
            }
        }


        function addEvent(dayElement) {
            const title = prompt('Enter event title:');
            const description = prompt('Enter event description:');
            const time = prompt('Enter event time:');


            if (title && description && time) {
                const event = document.createElement('div');
                event.className = 'event';
                event.innerHTML = `<strong>${title}</strong><br>${description}<br>${time}`;


                event.addEventListener('click', (e) => {
                    e.stopPropagation();
                    editEvent(event);
                });


                dayElement.appendChild(event);
            }
        }


        function editEvent(eventElement) {
            const newTitle = prompt('Edit event title:', eventElement.querySelector('strong').innerText);
            const newDescription = prompt('Edit event description:', eventElement.childNodes[2].nodeValue);
            const newTime = prompt('Edit event time:', eventElement.childNodes[4].nodeValue);


            if (newTitle && newDescription && newTime) {
                eventElement.innerHTML = `<strong>${newTitle}</strong><br>${newDescription}<br>${newTime}`;
            }


            const deleteEvent = confirm('Do you want to delete this event?');
            if (deleteEvent) {
                eventElement.remove();
            }
        }


        // Intentional mistakes:
        // 1. Wrong month in createCalendar (month + 1).
        // 2. Incorrect node references in editEvent (childNodes[2], childNodes[4]).
        // 3. Missing event highlight functionality.


        createCalendar(2023, 9); // October 2023
    </script>
</body>
</html>