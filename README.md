# 👻 Modulu tas-Sikurezza Ghost
**Għodda ta' Tisħiħ tas-Sikurezza tal-Windows u Azure Ibbażata fuq PowerShell**

> **Tisħiħ proattiv tas-sikurezza għall-endpoints tal-Windows u l-ambjenti ta' Azure.** Ghost jipprovdi funzjonijiet ta' tisħiħ ibbażati fuq PowerShell li jistgħu jgħinu biex inaqqsu l-vetturi ta' attakk komuni billi jneħħu s-servizzi u l-protokolli mhux meħtieġa.

## ⚠️ Twissijiet Importanti

**ITTESTJAR MEĦTIEĠ**: Dejjem ittestja l-Ghost fl-ambjenti mhux ta' produzzjoni l-ewwel. In-neħid tas-servizzi jista' jaffettwa l-funzjonijiet leġittimi tan-negozju.

**L-EBDA GARANZIJI**: Filwaqt li Ghost jimira lejn vetturi ta' attakk komuni, l-ebda għodda ta' sikurezza ma tista' tipprevjeni l-attakki kollha. Dan huwa komponent wieħed f'strateġija komprensiva ta' sikurezza.

**IMPATT OPERAZZJONALI**: Xi funzjonijiet jistgħu jaffettwaw il-funzjonalità tas-sistema. Irreveddi kull setting b'attenzjoni qabel id-dispożizzjoni.

**VALUTAZZJONI PROFESSJONALI**: Għall-ambjenti ta' produzzjoni, ikkonsulta ma' esperti tas-sikurezza biex tiżgura li s-settings huma allinjati mal-ħtiġijiet tal-organizzazzjoni tiegħek.

## 📊 Il-Pajsaġġ tas-Sikurezza

Il-ħsara tar-ransomware laħqet **$57 biljun fl-2025**, bir-riċerka li turi li ħafna attakki ta' suċċess jisfruttaw is-servizzi bażiċi tal-Windows u l-konfigurazjonijiet ħżiena. Il-vetturi ta' attakk komuni jinkludu:

- **90% tal-inċidenti tar-ransomware** jinvolvu l-isfruttament tar-RDP
- **Vulnerabbiltajiet SMBv1** ippermetew attakki bħal WannaCry u NotPetya
- **Makros tad-dokumenti** jibqgħu l-metodu primarju ta' konsenja tal-malware
- **Attakki bbażati fuq USB** jkomplu jimmiru lejn netwerks b'air-gap
- **Abbuż tal-PowerShell** żdied b'mod sinifikanti fis-snin reċenti

## 🛡️ Funzjonijiet tas-Sikurezza ta' Ghost

Ghost jipprovdi **16 funzjoni ta' tisħiħ tal-Windows** flimkien ma **integrazzjoni tas-sikurezza ta' Azure**:

### Tisħiħ tal-Endpoint tal-Windows

| Funzjoni | Skop | Konsiderazzjonijiet |
|----------|---------|----------------|
| `Set-RDP` | Jimmaniġġja l-aċċess għar-Remote Desktop | Jista' jaffettwa l-amministrazzjoni remota |
| `Set-SMBv1` | Jikkontrolla l-protokoll SMB antik | Meħtieġ għal sistemi antiki ħafna |
| `Set-AutoRun` | Jikkontrolla l-AutoPlay/AutoRun | Jista' jaffettwa l-konvenjenza tal-utent |
| `Set-USBStorage` | Jillimita l-apparat tal-ħżin USB | Jista' jaffettwa l-użu leġittimu tal-USB |
| `Set-Macros` | Jikkontrolla l-eżekuzzjoni tal-makros tal-Office | Jista' jaffettwa d-dokumenti b'makros attivati |
| `Set-PSRemoting` | Jimmaniġġja l-PowerShell remoting | Jista' jaffettwa l-ġestjoni remota |
| `Set-WinRM` | Jikkontrolla l-Windows Remote Management | Jista' jaffettwa l-amministrazzjoni remota |
| `Set-LLMNR` | Jimmaniġġja l-protokoll ta' riżoluzzjoni tal-ismijiet | Normalment sigur biex jitneħħa |
| `Set-NetBIOS` | Jikkontrolla n-NetBIOS fuq TCP/IP | Jista' jaffettwa l-applikazzjonijiet antiki |
| `Set-AdminShares` | Jimmaniġġja l-ishma amministrattivi | Jista' jaffettwa l-aċċess remot għall-fajls |
| `Set-Telemetry` | Jikkontrolla l-ġbir tad-dejta | Jista' jaffettwa l-kapaċitajiet dijanjostiċi |
| `Set-GuestAccount` | Jimmaniġġja l-Kont tal-Mistieden | Normalment sigur biex jitneħħa |
| `Set-ICMP` | Jikkontrolla r-risposti tal-ping | Jista' jaffettwa d-dijanjostiċi tan-netwerk |
| `Set-RemoteAssistance` | Jimmaniġġja r-Remote Assistance | Jista' jaffettwa l-operazzjonijiet tal-help desk |
| `Set-NetworkDiscovery` | Jikkontrolla l-iskopertura tan-netwerk | Jista' jaffettwa l-browsing tan-netwerk |
| `Set-Firewall` | Jimmaniġġja l-Windows Firewall | Kritiku għas-sikurezza tan-netwerk |

### Sikurezza tal-Cloud ta' Azure

| Funzjoni | Skop | Rekwiżiti |
|----------|---------|--------------|
| `Set-AzureSecurityDefaults` | Jippermetti s-sikurezza bażika ta' Azure AD | Permessi ta' Microsoft Graph |
| `Set-AzureConditionalAccess` | Jikkonfigura l-politiki ta' aċċess | Liċenzjar ta' Azure AD P1/P2 |
| `Set-AzurePrivilegedUsers` | Awdita l-kontijiet privileġġjati | Permessi ta' Global Admin |

### Għażliet ta' Dispożizzjoni tal-Intrapriża

| Metodu | Każ ta' Użu | Rekwiżiti |
|--------|----------|--------------|
| **Eżekuzzjoni Diretta** | Ittestjar, ambjenti żgħar | Drittijiet ta' admin lokali |
| **Group Policy** | Ambjenti tad-dominju | Admin tad-dominju, ġestjoni GP |
| **Microsoft Intune** | Apparat immaniġġjati mill-cloud | Liċenzjar ta' Intune, Graph API |

## 🚀 Bidu Mgħaġġel

### Valutazzjoni tas-Sikurezza
```powershell
# Itella' l-modulu Ghost
Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1' -OutFile .\Ghost.ps1
Get-Content .\Ghost.ps1
. .\Ghost.ps1

# Iċċekkja l-postura tas-sikurezza attwali
Get-Ghost
```

### Tisħiħ Bażiku (Ittestja l-Ewwel)
```powershell
# Tisħiħ essenzjali - ittestja fl-ambjent tal-laboratorju l-ewwel
Set-Ghost -SMBv1 -AutoRun -Macros

# Irreveddi l-bidliet
Get-Ghost
```

### Dispożizzjoni tal-Intrapriża
```powershell
# Dispożizzjoni tal-Group Policy (ambjenti tad-dominju)
Set-Ghost -SMBv1 -AutoRun -GroupPolicy

# Dispożizzjoni ta' Intune (apparat immaniġġjati mill-cloud)
Set-Ghost -SMBv1 -RDP -USBStorage -Intune
```

## 📋 Metodi ta' Installazzjoni

### Għażla 1: Tniżżil Dirett (Ittestjar)
```powershell
Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1' -OutFile .\Ghost.ps1
Get-Content .\Ghost.ps1
. .\Ghost.ps1
```

### Għażla 2: Installazzjoni tal-Modulu
```powershell
# Installa mill-PowerShell Gallery (meta disponibbli)
Install-Module Ghost -Scope CurrentUser
Import-Module Ghost
```

### Għażla 3: Dispożizzjoni tal-Intrapriža
```powershell
# Ikkopja għal lok tan-netwerk għad-dispożizzjoni tal-Group Policy
# Ikkonfigura l-iskripts tal-PowerShell ta' Intune għad-dispożizzjoni tal-cloud
```

## 💼 Eżempji ta' Każijiet ta' Użu

### Negozju Żgħir
```powershell
# Protezzjoni bażika b'impatt minimu
Set-Ghost -SMBv1 -AutoRun -Macros -ICMP
```

### Ambjent tal-Healthcare
```powershell
# Tisħiħ iffokalizzat fuq HIPAA
Set-Ghost -SMBv1 -RDP -USBStorage -AdminShares -Telemetry
```

### Servizzi Finanzjarji
```powershell
# Konfigurazzjoni ta' sikurezza għolja
Set-Ghost -RDP -SMBv1 -AutoRun -USBStorage -Macros -PSRemoting -AdminShares
```

### Organizzazzjoni Cloud-First
```powershell
# Dispożizzjoni mmaniġġjata minn Intune
Connect-IntuneGhost -Interactive
Set-Ghost -SMBv1 -RDP -AutoRun -Macros -Intune
```

## 🔍 Dettalji tal-Funzjonijiet

### Funzjonijiet ta' Tisħiħ Ewlenin

#### Servizzi tan-Netwerk
- **RDP**: Jimblokka l-aċċess għad-desktop remot jew randomizza l-port
- **SMBv1**: Jneħħi l-protokoll antik ta' qsim tal-fajls
- **ICMP**: Jipprevjeni r-risposti tal-ping għar-reconnaissance
- **LLMNR/NetBIOS**: Jimblokka l-protokolli antiċi ta' riżoluzzjoni tal-ismijiet

#### Sikurezza tal-Applikazzjonijiet
- **Makros**: Jneħħi l-eżekuzzjoni tal-makros fl-applikazzjonijiet tal-Office
- **AutoRun**: Jipprevjeni l-eżekuzzjoni awtomatika mill-midja li jinħassu

#### Ġestjoni Remota
- **PSRemoting**: Jneħħi s-sessjonijiet remoti tal-PowerShell
- **WinRM**: Iwaqqaf il-Windows Remote Management
- **Remote Assistance**: Jimblokka l-konnessjonijiet ta' assistenza remota

#### Kontroll tal-Aċċess
- **Admin Shares**: Jneħħi l-ishma C$, ADMIN$
- **Guest Account**: Jneħħi l-aċċess tal-Kont tal-Mistieden
- **USB Storage**: Jillimita l-użu tal-apparat USB

### Integrazzjoni ta' Azure
```powershell
# Ikkonnettja mat-tenant ta' Azure
Connect-AzureGhost -Interactive

# Ippermetti d-defaults tas-sikurezza
Set-AzureSecurityDefaults -Enable

# Ikkonfigura l-aċċess kondizzjonali
Set-AzureConditionalAccess -BlockLegacyAuth -RequireMFA

# Awdita l-utenti privileġġjati
Set-AzurePrivilegedUsers -AuditOnly
```

### Integrazzjoni ta' Intune (Ġdid f'v2)
```powershell
# Ikkonnettja ma' Intune
Connect-IntuneGhost -Interactive

# Iddisjinja permezz tal-politiki ta' Intune
Set-IntuneGhost -Settings @{
    RDP = $true
    SMBv1 = $true
    USBStorage = $true
    Macros = $true
}
```

## ⚠️ Konsiderazzjonijiet Importanti

### Rekwiżiti tal-Ittestjar
- **Ambjent tal-Laboratorju**: L-ewwel ittestja s-settings kollha f'ambjent iżolat
- **Dispożizzjoni Gradwali**: Iddisjinja gradwalment biex tidentifika l-kwistjonijiet
- **Pjan ta' Rollback**: Iżgura li tista' tirrevoka l-bidliet jekk meħtieġ
- **Dokumentazzjoni**: Irrekordja liema settings jaħdmu għall-ambjent tiegħek

### Impatt Potenzjali
- **Produttività tal-Utenti**: Xi settings jistgħu jaffettwaw il-workflows ta' kuljum
- **Applikazzjonijiet Antiki**: Sistemi eqdem jistgħu jeħtieġu protokolli speċifiċi
- **Aċċess Remot**: Ikkunsidra l-impatt fuq l-amministrazzjoni remota leġittima
- **Proċessi tan-Negozju**: Ivverifika li s-settings ma jkisrux funzjonijiet kritiċi

### Limitazzjonijiet tas-Sikurezza
- **Difiża fil-Fond**: Ghost huwa saff wieħed ta' sikurezza, mhux soluzzjoni kompleta
- **Ġestjoni Kontinwa**: Is-sikurezza teħtieġ monitoraġġ u aġġornamenti kontinwi
- **Taħriġ tal-Utenti**: Il-kontroll tekniku għandu jiġi mqabbad ma' konsapevolezza tas-sikurezza
- **Evoluzzjoni tat-Theddid**: Metodi ġodda ta' attakk jistgħu jaqbżu l-protezzjonijiet attwali

## 🎯 Eżempji ta' Skenarji ta' Attakk

Filwaqt li Ghost jimira lejn vetturi ta' attakk komuni, il-prevenzjoni speċifika tiddependi fuq l-implimentazzjoni u l-ittestjar korrett:

### Attakki ta' Stil WannaCry
- **Mitigazzjoni**: `Set-Ghost -SMBv1` jneħħi l-protokoll vulnerabbli
- **Konsiderazzjonijiet**: Iżgura li l-ebda sistema antika ma teħtieġ SMBv1

### Ransomware Bbażat fuq RDP
- **Mitigazzjoni**: `Set-Ghost -RDP` jimblokka l-aċċess għad-desktop remot
- **Konsiderazzjonijiet**: Jista' jeħtieġ metodi alternattivi ta' aċċess remot

### Malware Bbażat fuq Dokumenti
- **Mitigazzjoni**: `Set-Ghost -Macros` jneħħi l-eżekuzzjoni tal-makros
- **Konsiderazzjonijiet**: Jista' jaffettwa d-dokumenti leġittimi b'makros attivati

### Theddidiet Konsenjati permezz ta' USB
- **Mitigazzjoni**: `Set-Ghost -USBStorage -AutoRun` jillimita l-funzjonalità tal-USB
- **Konsiderazzjonijiet**: Jista' jaffettwa l-użu leġittimu tal-apparat USB

## 🏢 Karatteristiċi tal-Intrapriża

### Appoġġ tal-Group Policy
```powershell
# Applika s-settings permezz tar-reġistru tal-Group Policy
Set-Ghost -SMBv1 -RDP -AutoRun -GroupPolicy

# Is-settings japplikaw mad-dominju kollu wara r-rifresh tal-GP
gpupdate /force
```

### Integrazzjoni ta' Microsoft Intune
```powershell
# Oħloq politiki ta' Intune għas-settings ta' Ghost
Set-IntuneGhost -Settings $GhostSettings -Interactive

# Il-politiki jiddisjinjaw għall-apparat immaniġġjati awtomatikament
```

### Rappurtar tal-Konformità
```powershell
# Iġġenera rapport ta' valutazzjoni tas-sikurezza
Get-Ghost | Export-Csv -Path "SecurityAudit-$(Get-Date -Format 'yyyy-MM-dd').csv"

# Rapport tal-postura tas-sikurezza ta' Azure
Get-AzureGhost | Out-File "AzureSecurityReport.txt"
```

## 📚 Aħjar Prattiki

### Qabel id-Dispożizzjoni
1. **Iddokumenta l-Istat Attwali**: Mexxi `Get-Ghost` qabel il-bidliet
2. **Ittestja B'Attenzjoni**: Ivvalida f'ambjent mhux ta' produzzjoni
3. **Ippjana r-Rollback**: Kun af kif tirrevoka kull setting
4. **Reviżjoni tal-Stakeholders**: Iżgura li l-unitajiet tan-negozju japprovaw il-bidliet

### Matul id-Dispożizzjoni
1. **Approċċ Gradwali**: L-ewwel iddisjinja għal gruppi ta' pilota
2. **Immonitorja l-Impatt**: Ara għal ilmenti tal-utenti jew kwistjonijiet tas-sistema
3. **Iddokumenta l-Kwistjonijiet**: Irrekordja kwalunkwe problema għal referenza futura
4. **Ikkomunika l-Bidliet**: Għarraf lill-utenti dwar it-titjib tas-sikurezza

### Wara d-Dispożizzjoni
1. **Valutazzjoni Regolari**: Perjodikament mexxi `Get-Ghost` biex tivverifika s-settings
2. **Aġġorna d-Dokumentazzjoni**: Żomm il-konfigurazzjonijiet tas-sikurezza kurrenti
3. **Irrevedi l-Effettività**: Immonitorja għal inċidenti tas-sikurezza
4. **Titjib Kontinwu**: Aġġusta s-settings abbażi tal-pajsaġġ tat-theddid

## 🔧 Troubleshooting

### Problemi Komuni
- **Żbalji tal-Permessi**: Iżgura sessjoni PowerShell elevata
- **Dipendenzi tas-Servizzi**: Xi servizzi jistgħu jkollhom dipendenzi
- **Kompatibbiltà tal-Applikazzjonijiet**: Ittestja mal-applikazzjonijiet tan-negozju
- **Konnettività tan-Netwerk**: Ivverifika li l-aċċess remot għadu jaħdem

### Għażliet ta' Rkupru
```powershell
# Erġa' ppermetti servizzi speċifiċi jekk meħtieġ
Set-RDP -Enable
Set-SMBv1 -Enable
Set-AutoRun -Enable
Set-Macros -Enable
```

## 👨‍💻 Dwar l-Awtur

**Jim Tyler** - Microsoft MVP għal PowerShell
- **YouTube**: [@PowerShellEngineer](https://youtube.com/@PowerShell Engineer) (10,000+ abbonati)
- **Newsletter**: [PowerShell.News](https://powershell.news) - Intelligence tas-sikurezza ta' kull ġimgħa
- **Awtur**: "PowerShell for Systems Engineers"
- **Esperjenza**: Deċennji ta' awtomazzjoni tal-PowerShell u sikurezza tal-Windows

## 📄 Liċenzja u Disclaimer

### Liċenzja MIT
Ghost huwa pprovdut taħt il-Liċenzja MIT għall-użu, modifikazzjoni u distribuzzjoni b'xejn.

### Disclaimer tas-Sikurezza
- **L-Ebda Garanzija**: Ghost huwa pprovdut "kif inhu" mingħajr garanzija ta' kwalunkwe tip
- **Ittestjar Meħtieġ**: Dejjem ittestja f'ambjenti mhux ta' produzzjoni l-ewwel
- **Gwida Professjonali**: Ikkonsulta ma' professjonisti tas-sikurezza għad-dispożizzjonijiet ta' produzzjoni
- **Impatt Operazzjonali**: L-awturi m'humiex responsabbli għal kwalunkwe tħassib operazzjonali
- **Sikurezza Komprensiva**: Ghost huwa komponent wieħed f'strateġija kompleta tas-sikurezza

### Appoġġ
- **GitHub Issues**: [Irrapporta bugs jew itlob karatteristiċi](https://github.com/jimrtyler/Ghost/issues)
- **Dokumentazzjoni**: Uża `Get-Help <function> -Full` għal għajnuna dettaljata
- **Komunità**: PowerShell u forums tal-komunità tas-sikurezza

---

**🔒 Saħħaħ il-postura tas-sikurezza tiegħek b'Ghost - imma dejjem ittestja l-ewwel.**

```powershell
# Ibda b'valutazzjoni, mhux suppożizzjonijiet
Get-Ghost
```

**⭐ Agħti stilla lil dan ir-repository jekk Ghost jgħinek ittejjeb il-postura tas-sikurezza tiegħek!**