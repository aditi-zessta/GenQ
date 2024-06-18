Fitness Tracker
Description: Build a fitness tracker app to log workouts and monitor progress. Skills Tested: Data handling, DOM manipulation, event handling. Features:

Log different types of workouts (e.g., running, cycling, weightlifting).
Track duration, distance, and calories burned.
Display progress over time with charts.
Set and track fitness goals. """
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fitness Tracker</title>
</head>
<body>
    <h1>Fitness Tracker</h1>
    <form id="workoutForm">
        <label for="type">Workout Type:</label>
        <select id="type" name="type">
            <option value="running">Running</option>
            <option value="cycling">Cycling</option>
            <option value="weightlifting">Weightlifting</option>
        </select>
        <br>
        <label for="duration">Duration (minutes):</label>
        <input type="number" id="duration" name="duration">
        <br>
        <label for="distance">Distance (km):</label>
        <input type="number" id="distance" name="distance">
        <br>
        <label for="calories">Calories Burned:</label>
        <input type="number" id="calories" name="calories">
        <br>
        <button type="submit">Log Workout</button>
    </form>
    <div id="progress">
        <h2>Progress</h2>
        <ul id="workoutList"></ul>
    </div>
    <script>
        document.getElementById('workoutForm').addEventListener('submit', function(e) {
            e.preventDefault();


            const type = document.getElementById('type').value;
            const duration = parseInt(document.getElementById('duration').value);
            const distance = parseFloat(document.getElementById('distance').value);
            const calories = parseInt(document.getElementById('calories').value);


            const workoutList = document.getElementById('workoutList');
            const listItem = document.createElement('li');
            listItem.textContent = `Type: ${type}, Duration: ${duration} mins, Distance: ${distance} km, Calories: ${calories}`;


            workoutList.appendChild(listItem);


            document.getElementById('workoutForm').reset();
        });


        // Mistake: Incorrectly named function for chart display (should be displayChart)
        function displayCharts() {
            // TODO: Implement chart display logic
        }


        // Mistake: Missing declaration for goal variable
        goal = 1000;  // Calories goal


        function checkGoal() {
            let totalCalories = 0;
            document.querySelectorAll('#workoutList li').forEach(item => {
                const calories = parseInt(item.textContent.split('Calories: ')[1]);
                totalCalories += calories;
            });


            if (totalCalories >= goal) {
                alert('Congratulations! You have reached your goal!');
            }
        }


        // Mistake: Incorrect event type (should be 'change')
        document.getElementById('workoutList').addEventListener('click', checkGoal);
    </script>
</body>
</html>