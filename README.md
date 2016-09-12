<html>

<head>
	<title>The jQuery Example</title>
	<script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/2.1.3/jquery.min.js"></script>
	<script type="text/javascript" language="javascript">
		$(document).ready(function () {
			$("#driver").click(function () {
				$.ajax({
					method: "GET"
					, url: 'pp.json'
					, context: " document.body"
					, Accept: "application/json"
					, contentType: "application/json"
					, dataType: "json"
					, beforeSend: function () {
						$("#stage").html("<img calss='imgsixe' alt='Please wait...generating payment' src='http://www.downgraf.com/wp-content/uploads/2014/09/01-progress.gif' />");
					}
					, success: (function (data) {
						setTimeout(function () {
							/*	var data = JSON.parse(dat);*/
							$("#stage").html("<p> AccountID: " + data.AccountID + "</p>");
							$("#stage").append("<p>Year : " + data.Year + "</p>");
							$("#stage").append("<p> Make: " + data.Make + "</p>");
						}, 2000)
					})
				})

				function err() {
					debugger;
				}

				function hidebtn() {
					$("#driver").click(function () {
						$("#driver").hide();
					});
				}
			});
		});
	</script>
	<style>
		.cont {
			width: 20%;
			margin: auto;
			height: 150px;
			margin-top: 100px;
			padding: 2% 0% 0% 10%;
		}
		
		img {
			width: 47%;
			margin-left: -25px;
		}
	</style>
</head>

<body>
	<div class="cont">
		<div id="stage"> </div>
		<input type="button" id="driver" value="Load Data" /> </body>
</div>

</html>
