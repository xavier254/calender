<?php
function showCurrentMonth($current_Month, $year)
{
$date = mktime(12, 0, 0, $current_Month, 1, $year);
$numberOfDays =cal_days_in_month(CAL_GREGORIAN,$current_Month, $year);
$offset = date("w", $date);
$row_number = 1;
// time to draw the month header
echo "<table style='color:blue; border:1px solid blue; width:500px; height:300px;'><br/>";
echo "<tr><td>Sun</td><td>Mon</td><td>Tue</td><td>Wed</td><td>Thu</td><td>Fri</td><td>Sat</td></tr> <tr>";
// this will print the additional td record in case the month is not starting with the Sunday.
for($i = 1; $i <= $offset; $i++)
{
echo "<td></td>";
}
//  this will print the number of days.
for($day = 1; $day <= $numberOfDays; $day++)
{
if( ($day + $offset - 1) % 7 == 0 && $day != 1)
{
echo "</tr> <tr>";
$row_number++;
}
echo "<td>" . $day . "</td>";
}
while( ($day + $offset) <= $row_number * 7)
{
echo "<td></td>";
$day++;
}
echo "</tr></table>";
}
?>
<html>
<head>
<title>Calendar of the current month (july 2022)</title>
</head>
<body>
<p>Calendar of the july 2022</p>
<?php
// Dec 2019 in PHP
showCurrentMonth(07, 2022);
?>
</body>
</html>