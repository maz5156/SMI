<!DOCTYPE html>
<html>
<head>
<!-- Add in table format within here for style-->
</head>
<body>

<?php
$q = intval($_GET['q']);

$con = mysqli_connect('localhost','root','Ist440','SMI');
if (!$con) {
    die('Could not connect: ' . mysqli_error($con));
}

mysqli_select_db($con,"ajax_demo");
$sql="SELECT * FROM `Line ".$q."`";
$result = mysqli_query($con,$sql);

echo "<table>
<tr>
<th>Supplier</th>
<th>Quantity</th>
<th>Pack/Type</th>
<th>Bag</th>
<th>Color</th>
<th>SKU Number</th>
<th>Block/SKID</th>
<th>Customer</th>
<th>Goal (BPM/BPH)</th>
<th>Actual BPM</th>
<th>Downtime and Reason</th>
<th>Actual BPM</th>
<th>Start</th>
<th>Stop</th>
<th>Crew Number</th>
</tr>";
while($row = mysqli_fetch_array($result)) {
    echo "<tr>";
    echo "<td>" . $row['Supplier'] . "</td>";
    echo "<td>" . $row['Quantity'] . "</td>";
	echo "<td>" . $row['Pack/Type'] . "</td>";
	echo "<td>" . $row['Bag'] . "</td>";
	echo "<td>" . $row['Color'] . "</td>";
	echo "<td>" . $row['SKU Number'] . "</td>";
	echo "<td>" . $row['Block/SKID'] . "</td>";
	echo "<td>" . $row['Customer'] . "</td>";
	echo "<td>" . $row['Goal (BPM/BPH)'] . "</td>";
	echo "<td>" . $row['Actual BPM'] . "</td>";
	echo "<td>" . $row['Downtime and Reason'] . "</td>";
	echo "<td>" . $row['Start'] . "</td>";
	echo "<td>" . $row['Stop'] . "</td>";
	echo "<td>" . $row['Crew Number'] . "</td>";
    echo "</tr>";
}
echo "</table>";
mysqli_close($con);
?>
</body>
</html>