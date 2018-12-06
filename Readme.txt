PHP MJPEG(php mjpg) [PHP 即時影像監控 模擬 / PHP 動態提片切換]

資料來源:https://github.com/donatj/mjpeg-php
http://blog.changyy.org/2009/11/php-motion-jpeg-mjpegmjpg-http-streaming.html


index.html:
	<img src="mjpeg.php">

mjpeg.php

	<?php
	//https://github.com/donatj/mjpeg-php
	//http://blog.changyy.org/2009/11/php-motion-jpeg-mjpegmjpg-http-streaming.html

	// Used to separate multipart
	$boundary = 'jashliao';
	$delay = 1;

	// We start with the standard headers. PHP allows us this much
	header("Cache-Control: no-cache");
	header("Cache-Control: private");
	header("Pragma: no-cache");
	header("Content-type: multipart/x-mixed-replace; boundary=$boundary");

	// Set this so PHP doesn't timeout during a long stream
	set_time_limit(0);

	while(true) {
		for( $i=1 ; $i<= 12 ; $i++ )
		{
				echo 'Content-Type: image/jpeg'."\n\n";

				echo file_get_contents( "./images/$i.jpg" );

				echo "\n--$boundary\n" ;

				flush();
				sleep( $delay );
		}
	}