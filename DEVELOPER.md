#### Signing the PowerShell Scripts

~~~powershell
$certPfx = "$env:CHOCOLATEY_OFFICIAL_CERT"
$certPassword = Get-Content "$env:CHOCOLATEY_OFFICIAL_CERT_PASSWORD"
$timeStampServer = "http://timestamp.digicert.com"
$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2($certPfx, $certPassword)

Set-AuthenticodeSignature -Filepath ".\chocolatey\Website\Install.ps1" -Cert $cert -TimeStampServer $timeStampServer -IncludeChain NotRoot -HashAlgorithm SHA256
Set-AuthenticodeSignature -Filepath ".\chocolatey\Website\Install.Versioned.ps1" -Cert $cert -TimeStampServer $timeStampServer -IncludeChain NotRoot -HashAlgorithm SHA256
Set-AuthenticodeSignature -Filepath ".\chocolatey\Website\InstallAbsoluteLatest.ps1" -Cert $cert -TimeStampServer $timeStampServer -IncludeChain NotRoot -HashAlgorithm SHA256
Set-AuthenticodeSignature -Filepath ".\chocolatey\Website\Install-LastPoshClient.ps1" -Cert $cert -TimeStampServer $timeStampServer -IncludeChain NotRoot -HashAlgorithm SHA256
Set-AuthenticodeSignature -Filepath ".\chocolatey\Website\Import-QuickDeployCertificate.ps1" -Cert $cert -TimeStampServer $timeStampServer -IncludeChain NotRoot -HashAlgorithm SHA256
~~~

