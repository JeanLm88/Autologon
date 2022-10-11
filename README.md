# Autologon
Processo de auto login no windows, utilizando o script Power Shell do windows!
//Esse arquivo deverá ser executado via POWERSHELL, antes de executar você precisa dar permissão ao arquivo para funcioanar no seu SO
 //Código fonte:
 $ESCOLHA = Read-Host ("""SEJA BEM VINDO(A), O QUE DESEJA FAZER?
[0]DELETAR USER  [1] ADICIONAR LOGIN AUTOMÁTICO""")
[int] $DEL = 0
[int]$ADC = 1
if ([int]$ESCOLHA -match [int]$DEL){
    $RegistryPath = 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon'
    Set-ItemProperty $RegistryPath 'DefaultUserName' -Value "" -type String 
    Set-ItemProperty $RegistryPath 'DefaultPassWord' -Value "" -type String
    Write-Warning "USER DELETADO"
}else{
$Username = Read-Host 'Usuário'
$Pass = Read-Host "Senha do $Username "
$RegistryPath = 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon'
Set-ItemProperty $RegistryPath 'AutoAdminLogon' -Value "1" -Type String 
Set-ItemProperty $RegistryPath 'DefaultUserName' -Value "atmosfera.net\$Username" -type String 
Set-ItemProperty $RegistryPath 'DefaultPassWord' -Value "$Pass" -type String
Write-Warning "Auto-Login do $username configurado. Por favor reinicie o computador"
}
