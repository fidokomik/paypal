<?php
error_reporting(E_ERROR);
global $database,$step,$castka,$volba,$kraje,$jmeno,$adresa,$ico,$email,$kraj,$st,$amt,$tx,$sig,$auth_token,$business,$returnurl,$cancelurl,$potvrzeni,$paypallink,$paypalurl,$codedmail,$cpsmail;
$test=0; ## pro testovani nastavit na 1, jinak 0

$kraje=array("Celá ČR (preferováno)","Jihočeský kraj","Jihomoravský kraj",
	"Karlovarský kraj","Kraj Vysočina","Královehradecký kraj",
	"Liberecký kraj","Moravskoslezský kraj","Olomoucký kraj",
	"Pardubický kraj","Plzeňský kraj","Praha",
	"Středočeský kraj","Ústecký kraj","Zlínský kraj");
$tx=$st=$sig='';
if($test==1)
	{
	# tato identita je pro testovani na sandboxu
	$auth_token='YyLhT1SZXotjifaCLp1s1q3giBH6ZfEq8CCvC8sT11no49LAvSTOEmw8HJe';
#	$business='paypaluk&#64;practisoft.cz';
	$business='3LNLSKAGDS4BA';
	$returnurl='http://www.pirati.cz/pages/podporte-nas/financni-dary/paypal.php';
	$cancelurl='http://www.pirati.cz';
	$paypalurl='https://www.sandbox.paypal.com/cgi-bin/webscr';
	$cpsmail='petr@practisoft.cz';
	$paypalweb='www.sandbox.paypal.com';
	}
else
	{
	## tato identita je pro CPS
	$auth_token='O8JMc8i-bevvMxVPEtTp4vRo3nGrFghh_xEi5xp1hNpK2xUgfXmE6W5MtcO';
	$business='C6X6RSM3GGEH6';
	$returnurl='http://www.pirati.cz/pages/podporte-nas/financni-dary/paypal.php';
	$cancelurl='http://www.pirati.cz';
	$paypalurl='https://www.paypal.com/cgi-bin/webscr';
	$cpsmail='dary@ceskapiratskastrana.cz';
	$paypalweb='www.paypal.com';
	}
if(isset($_POST["step"]))
	{
	$step=$_POST["step"] * 1;
	}
elseif(isset($_GET["step"]))
	{
	$step=$_GET["step"] * 1;
	}
elseif(isset($_GET["tx"]) && isset($_GET["st"]) && isset($_GET["amt"]) && isset($_GET["sig"]))
	{
	$step=3;
	$tx=$_GET["tx"];
	$st=$_GET["st"];
	$sig=$_GET["sig"];
	$castka=$_GET["amt"];
	}
else
	{
	$step=1;
	}
$volba=(isset($_POST["volba"]) ? $_POST["volba"] : 1);
$jmeno=preg_replace('/\s+/',' ',urldecode(trim($_POST["jmeno"])));
$adresa=preg_replace('/\s+/',' ',urldecode(trim($_POST["adresa"])));
$ico=trim($_POST["ico"]); # RC nebo ICO
$email=preg_replace('/\s+/','',urldecode(trim($_POST["email"])));
$email=preg_replace('/\s*\(zavináč\)\s*/','@',$email);
$email=preg_replace('/\s*\(tečka\)\s*/','.',$email);
$codedmail=preg_replace('/\@/','&#64;',$email);
$codedmail=preg_replace('/\./','&#46;',$codedmail);
$kraj=(isset($_POST["kraj"]) ? $_POST["kraj"] : $_GET["kraj"]) * 1;
$potvrzeni=$_POST["potvrzeni"];
?>

<script type="text/javascript">
function setit(what)
{
c1=document.getElementById('c1');
c2=document.getElementById('c2');
if(what==1)
	{
	c2.disabled=true;
	c1.disabled=false;
	c1.focus();
	}
else
	{
	c1.disabled=true;
	c2.disabled=false;
	c2.focus();
	}
}
</script>
<style type="text/css">
.paypalred {
	color: red;
	}
table.paypal {
	margin: 0;
	padding: 0;
	border: 1px solid;
	border-collapse: collapse;
	}
table.paypal td {
	margin: 0;
	padding: 0.5em;
	vertical-align: top;
	border-top: none;
	border-bottom: none;
	border-left: none;
	border-right: none;
	border-collapse: collapse;
	}
table.paypal th {
	margin: 0;
	padding: 0.5em;
	vertical-align: top;
	border-top: 1px solid;
	border-bottom: 1px solid;
	border-left: none;
	border-right: none;
	border-collapse: collapse;
	}
select.paypal {
	font-family: "Courier New", Courier, monospace;
	}
table.paypal1 {
	margin: 0;
	padding: 0;
	border: none;
	}
table.paypal1 td {
	margin: 0;
	padding: 0;
	border: none;
	}
form.paypal {
	width: 100%;
	}
</style>

<?php
if($step==3)
	{
	$lines=explode("|",urldecode($_GET["cm"]));
	$potvrzeni=$lines[0]*1;
	$kraj=$lines[1]*1;
	$email=$lines[2];
	$ico=$lines[3];
	$jmeno=$lines[4];
	$adresa=$lines[5];
	$email=preg_replace('/\s*\(zavináč\)\s*/','@',$email);
	$email=preg_replace('/\s*\(tečka\)\s*/','.',$email);
	if($st==='Completed')
		{
		$req='cmd=_notify-synch' . "&tx=$tx&at=$auth_token";
		$header = "POST /cgi-bin/webscr HTTP/1.0\r\n";
		$header .= "Content-Type: application/x-www-form-urlencoded\r\n";
		$header .= "Content-Length: " . strlen($req) . "\r\n\r\n";
		$errno=0;
		$errstr='';
		$fp = fsockopen ($paypalweb, 80, $errno, $errstr, 30);
		if (!$fp)
			{
			## HTTP ERROR, nelze získat data o plátci. Co s tím?
			## ale stejně alespoň poděkujeme :-)
#			echo "<p>ERROR: $errno $errstr</p>";
			$err=0;
			$paypalquery="INSERT INTO `paypal` SET
				`datum`=NOW(),
				`castka`=$castka,
				`pro_kraj`=0x" . bin2hex($kraje[$kraj]) . ","
			.	"`potvrzeni`='" . ($potvrzeni==1 ? 'Ano' : 'Ne') . "',"
			.	"`email`=0x" . bin2hex($email) . ","
			.	"`jmeno`=0x" . bin2hex($jmeno) . ","
			.	"`ico_datum`=0x" . bin2hex($ico) . ","
			.	"`adresa`=0x" . bin2hex($adresa) . ","
			.	"`payment_status`=0x" . bin2hex($st) . ","
			.	"`txn_id`=0x" . bin2hex($tx);
			$db=$database->query("SET character_set_connection=utf8");
			$db=$database->query("SET character_set_client=utf8");
			$db=$database->query("SET character_set_results=utf8");
			$db=$database->query($paypalquery);
			if($database->is_error())
				{
				$err=1;
				$zprava="* POZOR! Z neznameho duvodu nebylo vlozeno do databaze *\n"
				.	"* error: " . $database->get_error() ." *\n";
				}
			else
				{
				$zprava='';
				}
			$zprava.="* Platba nebyla radne potvrzena *\n"
			.	"castka: $castka\n"
			.	"kraj: $kraje[$kraj]\n"
			.	"potvrzeni: ". ($potvrzeni==1 ? 'Ano' : 'Ne') . "\n"
			.	"darce: $jmeno\n"
			.	"adresa: $adresa\n"
			.	"ICO/datum: $ico\n"
			.	"email: $email\n"
			.	"txn_id: $tx\n"
			.	"payment_status: $st\n"
			.	str_repeat('-',40) . "\n\n";
			mail($cpsmail,"Dar PayPal",$zprava,
					"From: \"$email\" <$email>\n"
				.	"Reply-To: \"$email\" <$email>\n"
				.	"Mime-Version: 1.0\n"
				.	"Content-Type: text/plain; charset=UTF-8\n"
				.	"Content-Transfer-Encoding: 8bit\n"
				.	"X-Mailer: Web CPS\n");
			echo	"<h1 class='title'><span>Poděkování za dar</span></h1>",
				"<p>Děkujeme za Váš dar <b>$castka Kč</b>";
			if($kraj != 0)
				{
				echo " pro $kraje[$kraj]";
				}
			echo ".";
			if(strtolower($potvrzeni)==='on' && $castka >= 1000)
				{
				echo "Vystavíme Vám <b>Potvrzení o daru</b> a zašleme na Vámi uvedenou adresu.";
				}
			echo "</p>\n";
			}
		else
			{
			fputs ($fp, $header . $req);
			# read the body data 
			$res = '';
			$headerdone = false;
			while (!feof($fp))
				{
				$line = fgets ($fp, 1024);
				if (strcmp($line, "\r\n") == 0)
					{
					# read the header
					$headerdone = true;
					}
				elseif ($headerdone)
					{
					# header has been read. now read the contents
					$res .= $line;
					}
				}
			# parse the data
			$lines = explode("\n", $res);
			$ppdata = array();
			if (strcmp($lines[0], "SUCCESS") == 0)
				{
				for ($i=1; $i < count($lines); $i++)
					{
					list($key,$val) = explode("=", $lines[$i]);
					$ppdata[urldecode($key)] = preg_replace('/\+/',' ',urldecode($val));
					}
				$lines=explode("|",urldecode($ppdata["custom"]));
				$potvrzeni=$lines[0]*1;
				$kraj=$lines[1]*1;
				$email=$lines[2];
				$ico=$lines[3];
				$jmeno=$lines[4];
				$adresa=$lines[5];
				$email=preg_replace('/\s*\(zavináč\)\s*/','@',$email);
				$email=preg_replace('/\s*\(tečka\)\s*/','.',$email);
				$err=0;
				$paypalquery="INSERT INTO `paypal` SET
					`datum`=NOW(),
					`castka`=$castka,
					`pro_kraj`=0x" . bin2hex($kraje[$kraj]) . ","
				.	"`potvrzeni`='" . ($potvrzeni==1 ? 'Ano' : 'Ne') . "',"
				.	"`email`=0x" . bin2hex($email) . ","
				.	"`jmeno`=0x" . bin2hex($jmeno) . ","
				.	"`ico_datum`=0x" . bin2hex($ico) . ","
				.	"`adresa`=0x" . bin2hex($adresa) . ","
				.	"`address_status`=0x" . bin2hex($ppdata["address_status"]) . ","
				.	"`payer_status`=0x" . bin2hex($ppdata["payer_status"]) . ","
				.	"`last_name`=0x" . bin2hex($ppdata["last_name"]) . ","
				.	"`first_name`=0x" . bin2hex($ppdata["first_name"]) . ","
				.	"`payer_email`=0x" . bin2hex($ppdata["payer_email"]) . ","
				.	"`address_name`=0x" . bin2hex($ppdata["address_name"]) . ","
				.	"`address_city`=0x" . bin2hex($ppdata["address_city"]) . ","
				.	"`address_zip`=0x" . bin2hex($ppdata["address_zip"]) . ","
				.	"`address_country`=0x" . bin2hex($ppdata["address_country"]) . ","
				.	"`address_country_code`=0x" . bin2hex($ppdata["address_country_code"]) . ","
				.	"`payer_id`=0x" . bin2hex($ppdata["payer_id"]) . ","
				.	"`payment_status`=0x" . bin2hex($ppdata["payment_status"]) . ","
				.	"`txn_id`=0x" . bin2hex($ppdata["txn_id"]);
				if(isset($ppdata["payer_business_name"]))
					{
					$paypalquery.=",`payer_business_name`=0x" . bin2hex($ppdata["payer_business_name"]);
					}
				$db=$database->query("SET character_set_connection=utf8");
				$db=$database->query("SET character_set_client=utf8");
				$db=$database->query("SET character_set_results=utf8");
				$db=$database->query($paypalquery);
				if($database->is_error())
					{
					$err=1;
					$zprava="* POZOR! Z neznameho duvodu nebylo vlozeno do databaze *\n"
					.	"* error: " . $database->get_error() ." *\n";
					}
				else
					{
					$zprava='';
					}
				$zprava.="castka: $castka\n"
				.	"kraj: $kraje[$kraj]\n"
				.	"potvrzeni: ". ($potvrzeni==1 ? 'Ano' : 'Ne') . "\n"
				.	"darce: $jmeno\n"
				.	"adresa: $adresa\n"
				.	"ICO/datum: $ico\n"
				.	"email: $email\n"
				.	str_repeat('-',40)
				.	"\npayment_status: " . $ppdata["payment_status"] . ($ppdata["payment_status"]==='Completed' ? '' : '!!!!') . "\n"
				.	"address_status: " . $ppdata["address_status"] . "\n"
				.	"payer_status: " . $ppdata["payer_status"] . "\n"
				.	"last_name: " . $ppdata["last_name"] . "\n"
				.	"first_name: " . $ppdata["first_name"] . "\n"
				.	"payer_email: " . $ppdata["payer_email"] . "\n"
				.	"payer_business_name: " . (isset($ppdata["payer_business_name"]) ? $ppdata["payer_business_name"] : '') . "\n"
				.	"address_name: " . $ppdata["address_name"] . "\n"
				.	"address_city: " . $ppdata["address_city"] . "\n"
				.	"address_zip: " . $ppdata["address_zip"] . "\n"
				.	"address_country: " . $ppdata["address_country"] . "\n"
				.	"address_country_code: " . $ppdata["address_country_code"] . "\n"
				.	"payer_id: " . $ppdata["payer_id"] . "\n"
				.	"payment_status: " . $ppdata["payment_status"] . "\n"
				.	"txn_id: " . $ppdata["txn_id"] . "\n"
				.	str_repeat('-',40) . "\n\n";
				mail($cpsmail,"Dar PayPal",$zprava,
						"From: \"$email\" <$email>\n"
					.	"Reply-To: \"$email\" <$email>\n"
					.	"Mime-Version: 1.0\n"
					.	"Content-Type: text/plain; charset=UTF-8\n"
					.	"Content-Transfer-Encoding: 8bit\n"
					.	"X-Mailer: Web CPS\n");
				echo	"<h1 class='title'><span>Poděkování za dar</span></h1>",
					"<p>Děkujeme za Váš dar <b>$castka Kč</b>";
				if($kraj != 0)
					{
					echo " pro $kraje[$kraj]";
					}
				echo ".";
				if(strtolower($potvrzeni)==='on' && $castka >= 1000)
					{
					echo "Vystavíme Vám <b>Potvrzení o daru</b> a zašleme na Vámi uvedenou adresu.";
					}
				echo "</p>\n";
				}
			elseif (strcmp ($lines[0], "FAIL") == 0)
				{
				# log for manual investigation
				$err=0;
				$paypalquery="INSERT INTO `paypal` SET
					`datum`=NOW(),
					`castka`=$castka,
					`pro_kraj`=0x" . bin2hex($kraje[$kraj]) . ","
				.	"`potvrzeni`='" . ($potvrzeni==1 ? 'Ano' : 'Ne') . "',"
				.	"`email`=0x" . bin2hex($email) . ","
				.	"`jmeno`=0x" . bin2hex($jmeno) . ","
				.	"`ico_datum`=0x" . bin2hex($ico) . ","
				.	"`adresa`=0x" . bin2hex($adresa) . ","
				.	"`payment_status`=0x" . bin2hex($st) . ","
				.	"`txn_id`=0x" . bin2hex($tx);
				$db=$database->query("SET character_set_connection=utf8");
				$db=$database->query("SET character_set_client=utf8");
				$db=$database->query("SET character_set_results=utf8");
				$db=$database->query($paypalquery);
				if($database->is_error())
					{
					$err=1;
					$zprava="* Platba nebyla radne potvrzena *\n"
					.	"* POZOR! Z neznameho duvodu nebylo vlozeno do databaze *\n"
					.	"* error: " . $database->get_error() ." *\n";
					}
				else
					{
					$zprava="* Platba nebyla radne potvrzena *\n";
					}
				$zprava.="castka: $castka\n"
				.	"txn_id: $tx\n"
				.	"payment_status: $st\n"
				.	str_repeat('-',40) . "\n\n";
				mail($cpsmail,"Dar PayPal",$zprava,
						"From: \"$email\" <$email>\n"
					.	"Reply-To: \"$email\" <$email>\n"
					.	"Mime-Version: 1.0\n"
					.	"Content-Type: text/plain; charset=UTF-8\n"
					.	"Content-Transfer-Encoding: 8bit\n"
					.	"X-Mailer: Web CPS\n");
				echo	"<h1 class='title'><span>Dar České pirátské straně</span></h1>",
					"<p>Děkujeme za Váš dar, ale nejsme si zcela jisti, že se platba zdařila.",
					"<br />Zkontrolujte to prosím ve Vašem PayPal účtu a dejte nám vědět.",
					"<br /><i>(Paypal status: <b>$st</b>)</i></p>";
				}
			}
		fclose ($fp);
		}
	else
		{
		echo	"<h1 class='title'><span>Dar České pirátské straně</span></h1>",
			"<p>Litujeme, ale platba se z nějakého důvodu nepovedla.",
			"<br /><i>(Paypal status: <b>$st</b>)</i></p>";
		}
	}
elseif($step==2)
	{
	echo "<h1 class=\"title\"><span>Finanční dar <img src=\"https://www.paypal.com/en_US/i/logo/PayPal_mark_37x23.gif\" title=\"PayPal\" alt=\"PayPal\" /></span></h1>\n";
	$err='';
	$castka=0;
	if($volba==1)
		{
		$castka=$_POST["castka1"] *1;
		}
	else
		{
		$castka=$_POST["castka2"] *1;
		}
	if($castka < 32 || $castka > 50000)
		{
		$err="<b>Darovaná částka nemůže být menší než <nobr>32 Kč,</nobr> ani větší než <nobr>50.000 Kč</nobr></b>";
		}
	elseif(empty($jmeno) > 0)
		{
		$err="Vyplňte prosím <b>'Jméno a příjmení nebo název firmy'</b>";
		}
	elseif(empty($adresa) > 0)
		{
		$err="Vyplňte prosím <b>'Adresa trvalého bydliště nebo sídlo firmy'</b>";
		}
	elseif(empty($ico) > 0)
		{
		$err="Vyplňte prosím <b>'Datum narození nebo IČO'</b>";
		}
	elseif(empty($email) > 0)
		{
		$err="Vyplňte prosím <b>'Emailová adresa'</b>";
		}
	if(strlen($err) > 0 || isset($_POST["back"]))
		{
		print_form1($err);
		}
	else
		{
		print_form2();
		}
	}
else
	{
	echo "<h1 class=\"title\"><span>Finanční dar <img src=\"https://www.paypal.com/en_US/i/logo/PayPal_mark_37x23.gif\" title=\"PayPal\" alt=\"PayPal\" /></span></h1>\n";
	print_form1('');
	}

function print_form1($e)
{
global $database,$step,$castka,$volba,$kraje,$jmeno,$adresa,$ico,$email,$kraj,$potvrzeni,$codedmail;
$a=array(32,64,128,256,512,1024,2048,4096,8192);
$codedmail=preg_replace('/\@/','&#64;',$email);
$codedmail=preg_replace('/\./','&#46;',$codedmail);
echo	"<div>",
	"<form class='paypal' action='paypal.php' method='post'>\n",
	"<input type='hidden' name='step' value='2' />\n",
	"<table style='margin: 0;padding: 0;border: 1px solid;border-collapse: collapse;'>\n";
if(strlen($e) > 0)
	{
	echo "<caption style='font-size: 120%'><span style='color: red'><b>CHYBA:</b> $e</span></caption>\n";
	}
echo	"<tr><td colspan='2'><h3>Vyberte částku z nabídky, nebo zapište jinou částku</h3></td></tr>\n",
	"<tr><td style='width: 5em'>",
	"<nobr><input type='radio' name='volba' value='1'";
if($volba < 2)
	{
	echo " checked='checked'";
	}
echo	" onclick='setit(1)' />Vybrat&nbsp;částku:</nobr></td>\n",
	"<td><select id='c1' class='paypal' name='castka1' size='",count($a),"'";
if($volba==2)
	{
	echo " disabled='disabled'";
	}
echo	">\n";
foreach ($a as $val)
	{
	echo "<option value='",$val,"'";
	if(($step==1 && $val==512) || ($step==2 && $val==$castka))
		{
		echo " selected='selected'";
		}
	echo ">",preg_replace('/\s/','&nbsp;',sprintf("%4d",$val))," Kč";
	if($val > 1000)
		{
		echo " (lze odečíst z daní)";
		}
	echo "</option>\n";
	}
echo	"</select></td></tr>\n",
	"<tr><td><nobr><input type='radio' name='volba' value='2'";
if($volba==2)
	{
	echo " checked='checked'";
	}
echo	" onclick='setit(2)' />Zapsat&nbsp;jinou&nbsp;částku:</nobr></td>\n",
	"<td><input id='c2' type='text' name='castka2' value='$castka' maxlength='5'";
if($volba < 2)
	{
	echo " disabled='disabled'";
	}
echo	" />&nbsp;Kč</td></tr>\n",
	"<tr><td colspan='2'>",
	"<input type='checkbox' name='potvrzeni'",
		((strtolower($potvrzeni)==='on' && $castka >= 1000) ? " checked='checked'" : ''),
		" />Žádám o vystavení <b>Potvrzení o daru</b> pro odečet z daní</td></tr>\n",
	"<tr><td style='border-top: 1px solid' colspan='2'><h2>Indentifikace dárce</h2>",
	"<span style='font-weight: normal'><i>",
	"Nebudou-li následující údaje poskytnuty, budeme nuceni platbu dle zákona vrátit,",
	" případně odvést na účet státu, nebude-li vrácení možné. Identita dárce a pravost",
	" údajů se v případě darů do <nobr>50.000,- Kč</nobr> ročně nezkoumá.</i></span>",
	"<br />&nbsp;<table class='paypal1'><tr><td>Jméno a příjmení nebo název firmy<span style='color: red'>*</span>:</td>",
	"<td><input type='text' name='jmeno' id='jmeno' value='$jmeno' size='50' maxlength='100' /></td></tr>\n",
	"<tr><td>Adresa trvalého bydliště nebo sídlo firmy<span style='color: red'>*</span>:</td>",
	"<td><input type='text' name='adresa' id='adresa' value='$adresa' size='50' maxlength='100' /></td></tr>\n",
	"<tr><td>Datum narození nebo IČO<span style='color: red'>*</span>:</td>",
	"<td><input type='text' name='ico' id='ico' value='$ico' size='10' maxlength='10' /></td></tr>\n",
	"<tr><td>Emailová adresa<span style='color: red'>*</span>:</td>",
	"<td><input type='text' name='email' id='email' value='$codedmail' size='50' maxlength='100' /></td></tr>\n",
	"<tr><td>Kterému kraji chcete dar poskytnout:</td>",
	"<td><select name='kraj' id='kraj' size='1' class='paypal'>\n";
$c=0;
foreach ($kraje as $val)
	{
	echo "<option value='$c'";
	if(($step==1 && $c==0) || ($step==2 && $c==$kraj))
		{
		echo " selected='selected'";
		}
	echo ">$val</option>\n";
	$c++;
	}
echo	"</select></td></tr>\n",
	"</table>\n",
	"</td></tr>\n",
	"<tr><td colspan='2'>ČPS se zavazuje použít poskytnuté osobní údaje jen pro potřeby kontaktu s dárcem a pro účely evidence dle zákona 494/1991 Sb. o sdružování v politických stranách a v politických hnutích.</td></tr>\n",
	"<tr><th colspan='2'><input type='submit' name='ok' value='Pokračovat' /></th></tr>\n",
	"</table>\n</form></div>\n";
}

function print_form2()
{
global $database,$step,$castka,$volba,$kraje,$jmeno,$adresa,$ico,$email,$kraj,$business,$returnurl,$cancelurl,$potvrzeni,$codedmail,$paypalurl;
$cmail=preg_replace('/\@/','%40',$email);
$cmail=preg_replace('/\./','%2e',$cmail);
echo	"<div><form class='paypal' action='$paypalurl' method='post'>\n",
	"<input type='hidden' name='cmd' value='_donations' />\n",
	"<input type='hidden' name='business' value='$business' />\n",
	"<input type='hidden' name='lc' value='CZ' />\n",
	"<input type='hidden' name='amount' value='$castka' />\n",
	"<input type='hidden' name='currency_code' value='CZK' />\n",
	"<input type='hidden' name='charset' value='utf-8' />\n", 
	"<input type='hidden' name='item_name' value='Dar České pirátské straně";
if($kraj > 0)
	{
	echo ", ",$kraje[$kraj];
	}
echo	"' />\n",
	"<input type='hidden' name='no_shipping' value='1' />\n",
	"<input type='hidden' name='no_note' value='1' />\n",
	"<input type='hidden' name='return' value='$returnurl' />\n",
	"<input type='hidden' name='cancel_return' value='$cancelurl' />\n",
	"<input type='hidden' name='rm' value='1' />\n",
	"<input type='hidden' name='cbt' value='Pokračovat' />\n",
	"<input type='hidden' name='image_url' value='http://www.ceskapiratskastrana.cz/media/grafika/cpslogohp.png' />\n",
	"<input type='hidden' name='custom' value='",
		(($castka >= 1000 && strtolower($potvrzeni)==='on') ? 1 : 0),
		"|$kraj|$cmail|$ico|$jmeno|$adresa' />\n",
	"<table style='width: 100%'>\n",
	"<tr><td colspan='2'>Zkontrolujte prosím všechny údaje a pokud souhlasí, klikněte na tlačítko \"Pokračovat\".",
	"<br />Chcete-li údaje opravit, klikněte na tlačítko \"Opravit údaje\".<br />&nbsp;<hr></td></tr>\n",
	"<tr><td style='width: 5em'>Částka:</td>\n<td><b>$castka Kč</b></td></tr>\n",
	"<tr><td>Jméno&nbsp;a&nbsp;příjmení&nbsp;nebo&nbsp;název&nbsp;firmy:</td>\n<td><b>$jmeno</b></td></tr>\n",
	"<tr><td>Adresa&nbsp;trvalého&nbsp;bydliště&nbsp;nebo&nbsp;sídlo&nbsp;firmy:</td>\n<td><b>$adresa</b></td></tr>\n",
	"<tr><td>Datum&nbsp;narození&nbsp;nebo&nbsp;IČO:</td>\n<td><b>$ico</b></td></tr>\n",
	"<tr><td>Emailová&nbsp;adresa:</td>\n<td><b>$codedmail</b></td></tr>\n",
	"<tr><td>Kterému&nbsp;kraji&nbsp;chcete&nbsp;dar&nbsp;poskytnout:</td>\n<td><b>$kraje[$kraj]</b></td></tr>\n";
if($castka >= 1000 && strtolower($potvrzeni)==='on')
	{
	echo	"<tr><td colspan='2'>Žádám o vystavení <b>Potvrzení o daru</b> pro odečet z daní</td></tr>";
	}
elseif($castka < 1000 && strtolower($potvrzeni)==='on')
	{
	echo	"<tr><td colspan='2'><span style='color: red'><b>Potvrzení o daru</b> pro odečet z daní nelze vystavit pro dar menší než 1000 Kč.</span></td></tr>";
	}
else
	{
	echo	"<tr><td colspan='2'>Nežádám o vystavení <b>Potvrzení o daru</b> pro odečet z daní</td></tr>";
	}
echo	"<tr><th colspan='2'><hr>",
	"<input type='submit' name='ok' value='Pokračovat' /></th></tr>",
	"</table>\n</form>\n",
	"<form class='paypal' action='paypal.php' method='post'>\n",
	"<input type='hidden' name='step' value='2' />\n",
	"<input type='hidden' name='volba' value='$volba' />\n",
	"<input type='hidden' name='castka",$volba,"' value='$castka' />\n",
	"<input type='hidden' name='jmeno' value='$jmeno' />\n",
	"<input type='hidden' name='adresa' value='$adresa' />\n",
	"<input type='hidden' name='ico' value='$ico' />\n",
	"<input type='hidden' name='email' value='$codedmail' />\n",
	"<input type='hidden' name='kraj' value='$kraj' />\n",
	"<input type='hidden' name='potvrzeni' value='$potvrzeni' />\n",
	"<table width='100%'><tr><th>",
	"<input type='submit' name='back' value='Opravit údaje' /></th></tr></table></form>\n</div>\n";
}
?>
