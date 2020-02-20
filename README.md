
<!--
                                             '                         
 -->
<html>
<head>
<title>QuirkBot</title>
<style>

		body {
			margin: 0;
			font-family: 'Open Sans', sans-serif;
			position: absolute;
			width: 100vw;
			height: 100vh;
			overflow: hidden;
			display: table;
		}

		#activity {
			display: table-cell;
			text-align: center;
			vertical-align: middle;
		}

		#activity:before {
			content: '';
			position: absolute;
			top: 0;
			left: 0;
			width: 100vw;
			height: 18vh;
			background: rgba(0,173,239,0.5);
		}
		#activity:after {
			content: '';
			position: absolute;
			bottom: 0;
			left: 0;
			width: 100vw;
			height: 18vh;
			background: rgba(235,0,138, 0.5);
		}

		#result {
			text-transform: uppercase;
		}

		.tryagain {
		background-attachment: scroll;
		background-clip: border-box;
		background-color: rgb(127, 206, 119);
		background-image: none;
		background-origin: padding-box;
		background-size: auto;
		border-bottom-left-radius: 16px;
		border-bottom-right-radius: 16px;
		border-top-left-radius: 16px;
		border-top-right-radius: 16px;
		box-sizing: border-box;
		color: rgb(255, 255, 255);
		cursor: pointer;
		display: inline-block;
		font-family: 'Open Sans', sans-serif;
		font-size: 32px;
		font-stretch: normal;
		font-style: normal;
		font-variant: normal;
		font-weight: normal;
		height: 93px;
		line-height: normal;
		margin-bottom: 8px;
		margin-left: 9.28px;
		margin-right: 9.28px;
		margin-top: 8px;
		min-height: 0px;
		min-width: 208px;
		outline-width: 0px;
		padding-bottom: 24px;
		padding-left: 24px;
		padding-right: 24px;
		padding-top: 24px;
		position: relative;
		text-align: center;
		text-transform: none;
		transition-delay: 0s;
		transition-duration: 0.28s;
		transition-property: box-shadow;
		transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
		width: 351.594px;
		z-index: 0;
		-webkit-user-select: none;
		}

		a:link, a:hover, a:visited, a:active {
			text-decoration: none;
		}
.hits {
  font-size: 2em;
  font-weight: bolder;
}
</style>
</head>
<body>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
<script src="https://raw.githubusercontent.com/carhartl/jquery-cookie/master/src/jquery.cookie.js"></script>

<div id="activity">
			<img src="http://code.quirkbot.com/assets/images/logo/white-outline.svg" width="30%" alt="">
  <h1 id="counter">You have hit the spacebar <span class="hits">0</span> times.</h1>
  <a href="#" onclick="resetHits()" class="tryagain">RESTART</a>
		</div>
<script>
var hits = getCookie('hits');
var hitElement = document.querySelector( '.hits' );
document.body.onkeyup = function(e) {
  if( e.keyCode == 32 ) {
    addHit();
  }
}

var addHit = function() {
  hits++;
  setCookie('hits', hits, '365');
  renderHits();
}

var renderHits = function() {
  hitElement.innerHTML = hits;
}

var resetHits = function() {
    var answer = confirm('Are you sure you would like to do this?');
    if (answer) {
        hits = 0;
        setCookie('hits', 0, 365);
        renderHits();
    }
}

function setCookie(name,value,days) {
    var expires = "";
    if (days) {
        var date = new Date();
        date.setTime(date.getTime() + (days*24*60*60*1000));
        expires = "; expires=" + date.toUTCString();
    }
    document.cookie = name + "=" + (value || "")  + expires + "; path=/";
}
function getCookie(name) {
    var nameEQ = name + "=";
    var ca = document.cookie.split(';');
    for(var i=0;i < ca.length;i++) {
        var c = ca[i];
        while (c.charAt(0)==' ') c = c.substring(1,c.length);
        if (c.indexOf(nameEQ) == 0) return c.substring(nameEQ.length,c.length);
    }
    return null;
}

hitElement.innerHTML = getCookie('hits');

</script>
</body>
</html>
