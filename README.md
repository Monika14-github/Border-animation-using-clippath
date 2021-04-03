# Border-animation-using-clippath
....html.....
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width">
    <title>repl.it</title>
    <link href="style.css" rel="stylesheet" type="text/css" />
  </head>
  <body>
    <script src="script.js"></script>
    <div class="box"></div>
  </body>
</html>
....css.....
html, body{
	width: 100%; height: 100%;
	background-color: #DDFFF7;
	z-index: 1;
	position: relative;
	overflow: hidden;
	
}

body{
	display: flex;
	flex-direction: row;
	justify-content: center;
	align-items:center;
	color:#fff;
}
.box{
	width: 300px; height: 200px;
	background-color: #DDFFF7;
	position: relative;
	box-shadow: 10px 10px 42px 0 rgba(0,0,0,0.75);
}
.box:after, .box:before{
	mix-blend-mode:multiply;
	filter:none;
	z-index: -1;
	content:'';
	width:calc(100% + (50px * 2));
	height:calc(100% + (50px * 2));
	position: absolute;
	display: block;
	animation: border 10s ease-in-out infinite;
	transform:translateX(-50px) translateY(-50px);
}
@keyframes border {
  0%, 100% {
    -webkit-clip-path: polygon(0 0, calc(100% - (33.3333333333px)) calc(0% + (33.3333333333px)), 100% 100%, calc(0% + (33.3333333333px)) calc(100% - (33.3333333333px)));
            clip-path: polygon(0 0, calc(100% - (33.3333333333px)) calc(0% + (33.3333333333px)), 100% 100%, calc(0% + (33.3333333333px)) calc(100% - (33.3333333333px)));
  }
  50% {
    -webkit-clip-path: polygon(calc(0% + (33.3333333333px)) calc(0% + (33.3333333333px)), 100% 0, calc(100% - (33.3333333333px)) calc(100% - (33.3333333333px)), 0 100%);
            clip-path: polygon(calc(0% + (33.3333333333px)) calc(0% + (33.3333333333px)), 100% 0, calc(100% - (33.3333333333px)) calc(100% - (33.3333333333px)), 0 100%);
  }
}

.box:after{
	animation-delay: -5s;
	background-color: #93e1d8;
	clip-path: polygon(0 0, calc(100% - (33.3333333333px)) calc(0% + (33.3333333333px)), 100% 100%, calc(0% + (33.3333333333px)) calc(100% - (33.3333333333px)));
}
.box:before {
	background-color: #AA4465;
	  clip-path: polygon(calc(0% + (33.3333333333px)) calc(0% + (33.3333333333px)), 100% 0, calc(100% - (33.3333333333px)) calc(100% - (33.3333333333px)), 0 100%);
}

.box:hover:after{
	animation-delay: -0.1s;
}
.box:hover:before, .box:hover:after {

          animation-duration: 0.2s;
}
