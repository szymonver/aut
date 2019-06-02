# aut
Logonscript:
$CompName = get-content ENV:ComputerName
$UserName = get-content ENV:UserName
$Date = get-date -Format "dd-MM-yyyy HH:mm"
$FileName = get-date -Format yyyyMM
$IPAddress = Get-NetIPAddress -IPAddress 10.0.6.*|Select-Object -ExpandProperty IPaddress
$Text = "Logon: " + $UserName + " " + $CompName + " " + $Date + " " + $IPAddress
$Text|Out-File -Append -FilePath C:\USERS\ll-72960\Documents\$Filename.txt

4.1
New-ADGroup -GroupScope Global -Name Sales -Path "ou=Sint-Niklaas, dc=MediaTech, dc=lan"
Move-ADObject -TargetPath "Group=Sales, ou=Sint-Niklaas, dc=MediaTech, dc=lan"
Set-ADUser -Identity BEP -Department Sales
Add-ADGroupMember -Identity IT -Members BEP

4.3
$set1 = (Get-Date).AddDays(-10)
$set2 = (Get-Date).AddDays(-20)
$set3 = (Get-Date).AddDays(-30)
$set4 = (Get-Date).AddDays(-40)

#$dagen = Write-Host "geef het aantal dagen in"

Get-Item C:\data1\file_?.txt | foreach-object {$_.Creationtime = $set1}
Get-Item C:\data1\file_1?.txt | foreach-object {$_.Creationtime = $set2}
Get-Item C:\data1\file_2?.txt | foreach-object {$_.Creationtime = $set3}
Get-Item C:\data1\file_3?.txt | foreach-object {$_.Creationtime = $set4}

$days = (Get-Date).AddDays(-20)
Get-ChildItem -Path C:\data1 -Recurse -Force | where-object {!$_.PSIscontainer -and $_.CreationTime -lt $days} | Remove-Item

$tdc='C:\data1'
$a = Get-ChildItem $tdc -recurse | Where-Object {$_.PSIsContainer -eq $True}
$a | Where-Object {$_.GetFiles().Count -eq 0} | Remove-Item

7.3
New-ADGroup -GroupScope Global -Name Sales -Path "ou=Sint-Niklaas, dc=MediaTech, dc=lan"
Move-ADObject -TargetPath "Group=Sales, ou=Sint-Niklaas, dc=MediaTech, dc=lan"
Set-ADUser -Identity BEP -Department Sales
Add-ADGroupMember -Identity IT -Members BEP

7.2
New-ADOrganizationalUnit -Name Sint-Niklaas
New-ADGroup -Name IT -Path "ou=Sint-Niklaas, DC=mediatech, DC=lan"
Add-ADGroupMember -Identity IT-Members bep

7.1
Set-ADUser -Identity ll-72960 -Company Mediatech -Department IT -EmailAddress ll-72960@broeders.be
Get-ADuser -Identity ll-72960 -Properties *|format-table emailaddress,company,department


