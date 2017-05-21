# HoneyResult

After installing a honeypot on the network and running for 12 hours, it has received 27,936 incoming attempts.

With the ip obtained I generated the script to analyze them

```php
<?php

	function analize($file){
		$token ="add token here";
		$handle = fopen($file, "r");
		if ($handle) {
		    while (($line = fgets($handle)) !== false) {
		        //echo "$line";

		        $curl = curl_init();
				curl_setopt_array($curl, array(
		    		CURLOPT_RETURNTRANSFER => 1,
		    		CURLOPT_URL => "http://ipinfo.io/$line/json?token=$token",
				));
				$result = curl_exec($curl);

				if (curl_errno($curl)){
	   				echo "Ha ocurrido un error con curl", PHP_EOL;
				}else{
					//echo $result;
					$json = $result;
					$json = json_decode($json, true);
					echo $json['ip'],";";
					echo $json['city'],";";
					echo $json['region'],";";
					echo $json['country'],";";
					echo $json['loc'],PHP_EOL;;

				}


				curl_close($curl);



		    }

		    fclose($handle);
		    echo PHP_EOL;
		} else {
	    	echo "Error al obtener el manejador", PHP_EOL;
		}
	}




	if(isset($argv[1])){
		analize($argv[1]);
	}else{
		echo "Debes aniadir el fichero a leer", PHP_EOL;
	}


?>
 ```

Run a random sample of 1000 results, redirecting the output of the script and processing each of the json we obtained the following map:

![Mapa de ataque](img/mapimage.png)

The map can be visited in this [link](https://drive.google.com/open?id=1x3u8aQ7zDJLjcv6KsoDhqRmmMNs&usp=sharing)

* [Table of  1000 ip](tabla.md)
* [All ips](ip.md)
