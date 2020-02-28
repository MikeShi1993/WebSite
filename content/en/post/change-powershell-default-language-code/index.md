---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Change Powershell default language code"
subtitle: ""
summary: ""
authors: []
tags: []
categories: []
date: 2020-02-27T22:16:10-05:00
lastmod: 2020-02-27T22:16:10-05:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---
##### How to create a profile

To create a profile for the current user in the current PowerShell host application, use the following command:

``` powershell
if (!(Test-Path -Path $PROFILE)) {
  New-Item -ItemType File -Path $PROFILE -Force
}
```

Then `notepad $PROFILE` to modify the profile file. Add the following line:

``` powershell
chcp 936
```

##### Create your code signing certificate

``` powershell
New-SelfSignedCertificate -CertStoreLocation cert:\currentuser\my `
-Subject "CN=Local Code Signing" `
-KeyAlgorithm RSA `
-KeyLength 2048 `
-Provider "Microsoft Enhanced RSA and AES Cryptographic Provider" `
-KeyExportPolicy Exportable `
-KeyUsage DigitalSignature `
-Type CodeSigningCert
```

##### Open the Certificate Manager for Current User

From the same Powershell prompt, run:

``` powershell
certmgr /s my
```

##### Copy the new certificate to the appropriate cert stores

Expand the "Personal" folder, select Certificates. Right click the new **Local Code Signing** certificate, and Copy.

Paste into **Trusted Root Certification Authorities** and into **Trusted Publishers** stores.

##### Sign your Powershell script with the new cert

From a Powershell prompt, run these two commands:

``` powershell
$cert = @(Get-ChildItem cert:\CurrentUser\My -CodeSigning)[0]
Set-AuthenticodeSignature $PROFILE $cert
```

The above instructions is obtained from Microsoft Documentation About [Signing](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_signing?view=powershell-7) and [Profiles](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-7) and from [SpiceWorks](https://community.spiceworks.com/how_to/153255-windows-10-signing-a-powershell-script-with-a-self-signed-certificate).
