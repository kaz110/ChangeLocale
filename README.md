#WindowsのSystemLocaleをja-JPに変更するPowerShell用サンプルscript
#事前に下記設定をしておく必要あり。
#Set-ExecutionPolicy RemoteSigned
#============
$loc = Get-WinSystemLocale
echo $loc	
if ($loc -ne "ja-JP")
{
	echo "ReBoot"
	Copy-Item EUDC.TTE D:\Windows\Fonts\.
	Set-WinSystemLocale ja-JP
	Restart-Computer
} else {
	if (Test-Path "D:\Windows\Fonts\EUDC.TTE")
	{
		echo "OK"
	} 
	else 
	{
		echo "EUDC Copy"
		Copy-Item EUDC.TTE D:\Windows\Fonts\.
	}
}
