# TP1 : Plip plap votre OS

## I. Ressources de l'OS
Toutes les étapes sont à faire depuis le terminal.

### 1. Programme, service, processus
Un programme est une suite d'instructions à exécuter pour le processeur.
Un processus est un programme en cours d'exécution.
Un service est un processus lancé par l'OS.

🌞 **Lister tous les processus en cours d'exécution sur votre machine**

- on doit voir apparaître
  - le nom de chaque processus
  - son identifiant unique (un nombre entier)
```
  REPONSE : 
        Get-Process
```        
```
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    141       9     2036       8276              7952   0 AggregatorHost
    155       9     1608       6752              5460   0 AISControlService
    632      25    16680      33192       0,98   7212   1 ApplicationFrameHost
    176      11     2024       8484       0,06   6296   1 AppVShNotify
   1513      14    12104      18088      44,98  17920   0 audiodg
    206      12     3820      15000       0,05   9516   1 backgroundTaskHost
    311      33    17948       1796       0,11  10324   1 backgroundTaskHost
    674      43    16732       1620       0,19  19144   1 backgroundTaskHost
    229      19    12744      28588       0,06   5500   1 chrome
    452      38   113972     156592      41,36   7164   1 chrome
    212      14     9712      18672       0,19   9868   1 chrome
   1821      46   274280     182472     162,98   9976   1 chrome
    316      23    32520      65492       0,17  10228   1 chrome
    578      27    40520      38652       0,11  17108   1 chrome
    276      24    28416      56352       0,11  17636   1 chrome
    444      35   105372     179420      18,03  17852   1 chrome
    402      32    75592     121732       2,58  18192   1 chrome
   1993     125   129176     207356      50,48  18688   1 chrome
    246      16    11896      18972       0,08  21024   1 chrome
    253      12     7068       9864       0,05  21928   1 chrome
    388      26    23188      48824       5,06  22964   1 chrome
    404      33    51348      93576       4,94  23376   1 chrome
    193      17    27896      83180       0,14   2900   1 Code
   1067      56   101248      98652      11,31   6264   1 Code
    294      23    99764      92200       1,11   7044   1 Code
    247      13    14656      29540       0,03  12532   1 Code
    796      28   215984     205632      84,08  13732   1 Code
    545      46   296256     294692     122,50  15020   1 Code
    242      22    74344      75172       2,25  19012   1 Code
    319      19    16816      41660       0,44  21368   1 Code
    346      31   326824     256708       3,64  25440   1 Code
    190      12     7484       8604       0,13   2584   1 CodeSetup-stable-65edc4939843c90c34d61f4ce11704f09d3e5cb6
    326      23    24168      21908       6,31   5784   1 CodeSetup-stable-65edc4939843c90c34d61f4ce11704f09d3e5cb6.tmp
    144       9     1436       8132       0,00  19944   1 conhost
    884      86    25800      69920      25,53  10084   1 CrossDeviceService
    646      30     2712       5272              1260   0 csrss
    696      34     3284       6224              1380   1 csrss
    695      21    10640      25740      18,13  12704   1 ctfmon
    115       7     1076       5264             11640   0 dasHost
    408      23    10940      33744       0,25  10668   1 DataExchangeHost
    285      16    13900      77964       3,77  14768   1 Discord
   1613     124   588980     471848   1 543,88  15208   1 Discord
   1439      62   123288     138692      97,67  15708   1 Discord
    228      13    11748      33184       0,05  16100   1 Discord
    383      21    18536      55084      14,22  16192   1 Discord
   1934      37   395528     260408     459,48  16252   1 Discord
    135      10     2032       7952       0,00  20992   1 DismHost
    159       9     1992       8988       0,03   8008   1 dllhost
    899      25     8580      17116       6,80  11612   1 dllhost
    179      10     2496      10300       0,25  19328   1 dllhost
    157       9     1796       7736       0,00  23888   1 dllhost
   2567      96   333792     149664              2396   1 dwm
  13517     415   716324     375240     116,03   9140   1 explorer
    189      13    19160      11384       1,22  12252   1 FnHotkeyCapsLKNumLK
    481      26    36032      24368       6,39   5564   1 FnHotkeyUtility
     42       7     1600       3328              1624   0 fontdrvhost
     42      11     7692       8512              1940   1 fontdrvhost
      0       0       60          8                 0   0 Idle
    415      37    40004      28072              5624   0 IntelAudioService
    149       8     1448       5412              2056   0 IntelCpHDCPSvc
    180      11     2088       8656      12,45   8716   1 ipf_helper
    146       9     2180       6164              5668   0 ipf_uf
    138      12     1656       5504              5532   0 ipfsvc
    147       9     1332       6336              5660   0 jhi_service
   1032      46    32748      43412              5572   0 Lenovo.Modern.ImController
    222      13    20512      10660              5540   0 LenovoUtilityService
    533      30    34068       2104             15200   1 LenovoVantage-(DeviceSettingsSystemAddin)
    821      51    46236       4240       2,38   8752   1 LenovoVantage-(GenericMessagingAddin)
   1105      39    40908      10016              8460   0 LenovoVantage-(LenovoGamingSystemAddin)
    645      46    50084       7300             15492   0 LenovoVantage-(VantageCoreAddin)
   3412      58   140036      56488             23440   0 LenovoVantageService
     61       5      684       3304              7600   0 Locator
    649      31    42576      62880       0,53  23016   1 LockApp
    201      15     3904      10104              5736   0 logi_lamparray_service
     61      11     1532       3260              1464   0 LsaIso
   1953      33    13272      27796              1480   0 lsass
      0       0     2032     833840              3280   0 Memory Compression
    483      27    27792       4568       1,09  16460   1 Microsoft.SharePoint
    403      21    24984      36332             17132   0 MoUsoCoreWorker
    476      18    16064      22224             10264   0 MpDefenderCoreService
   1042      35   171740       5888       0,89   1800   1 msedgewebview2
    679      53   156496        168       3,00   6024   1 msedgewebview2
    195      11     2544       8664       0,02   9640   1 msedgewebview2
    166      11     8920         16       0,08  15388   1 msedgewebview2
    209      14     7216        884       0,02  18196   1 msedgewebview2
   1236      50    35628       5432       1,00  20700   1 msedgewebview2
    336      20    11748       1876       0,30  22696   1 msedgewebview2
    943     249   391460     263996             19196   0 MsMpEng
    708      47    53552      34860       0,25  17572   1 Nahimic3
    802      35    45880      45188       0,80   9156   1 nahimicNotifSys
    777      27     9844      26524              5588   0 NahimicService
    322      17     4816       3500       2,83  10380   1 NahimicSvc32
   3200      28    59036       7236     126,94  10368   1 NahimicSvc64
    222      13     4136      11548              4520   0 NisSrv
    531      33    30640      28432              3080   0 NVDisplay.Container
   1326      33    41272      35916              3700   1 NVDisplay.Container
    743      27    49116      39188             22420   0 OfficeClickToRun
    408      24    33844      34300              5516   0 OneApp.IGCC.WinService
    299      15     3344      16844       0,06  14012   1 OpenConsole
   1095     112    80084     140300      18,03  12936   1 PhoneExperienceHost
    734      34    71444      91156       0,95   8408   1 powershell
    589      32    39208      49328       0,06   9728   1 PrintDialog
      0      16    10388      37352               268   0 Registry
    166      10     1788       8024       0,03   8876   1 RiotClientCrashHandler
    426      36   241136     124468      35,80   4464   1 RiotClientServices
    464      15     4988      11992              5632   0 RtkAudUService64
    436      16     5500      13872       0,16  13468   1 RtkAudUService64
    303      10     3060       7948              5728   0 RtkBtManServ
    558      23     6356      27456       0,94   1696   1 RuntimeBroker
    150      10     2176      10380       0,02   3688   1 RuntimeBroker
    446      27    11612      36328       5,20  10244   1 RuntimeBroker
    913      42    19668      58704       5,64  10484   1 RuntimeBroker
    163      11     2388      10516       0,03  14348   1 RuntimeBroker
    283      16     5400      17128       0,05  18344   1 RuntimeBroker
    155      10     2176      10780       0,02  20692   1 RuntimeBroker
    441      21     8924      27544       1,19  22440   1 RuntimeBroker
    612      28    12536      36784       1,50  23108   1 RuntimeBroker
    249      14     3612      18568       0,11  24616   1 RuntimeBroker
    188      10     2464       9736             24156   0 SearchFilterHost
   1834     163   269628     363456      35,36   9684   1 SearchHost
    803      24    24136      30012             15784   0 SearchIndexer
    366      14     2760      14828             20020   0 SearchProtocolHost
      0       0      184      50296               236   0 Secure System
    477      20     7596      16280             13412   0 SecurityHealthService
    195      11     2244      10140       0,06  13392   1 SecurityHealthSystray
    375      28    45140      10180       0,08   3292   1 SEGameTool
    832      13     6564       9244              1444   0 services
   1155      54    87260      81344       5,30  11160   1 ShellExperienceHost
    680      22     7464      33580      12,63   7628   1 sihost
     58       4     1132       1104               888   0 smss
    186       9     1744       7780              5476   0 SpitCamSrv
    460      24     6272      17964              5136   0 spoolsv
    991      47    97620      91956       8,11   8836   1 StartMenuExperienceHost
    262      14     3228       9460              1440   0 svchost
   1410      30    13140      31376              1600   0 svchost
   1637      23    10764      17872              1732   0 svchost
    269      10     2308       7932              1748   0 svchost
    330      14     3184       9312              1780   0 svchost
    110      14     1284       5152              2016   0 svchost
    425      13     3132       8028              2064   0 svchost
    132      13     1608       5532              2112   0 svchost
    164      35     7300       6768              2152   0 svchost
   1057      22     7276      15608              2260   0 svchost
    442      19     7168      16484              2600   0 svchost
    257      14     3972      12920              2684   0 svchost
    335      17     4144       9176              2708   0 svchost
    193      11     2360      10184              2760   0 svchost
    290      12     3504      14104              2940   0 svchost
    244       8     2008       5996              2948   0 svchost
    297      13     3672       9612              3008   0 svchost
    513      18    19952      14412              3136   0 svchost
    313      12    21928      21672              3168   0 svchost
    240      13     2768      10684              3196   0 svchost
    182      10     2028       7076              3204   0 svchost
    289       8     1240       5656              3212   0 svchost
    186      13     1924       7796              3316   0 svchost
    259      12     2592       8132              3384   0 svchost
    201      13     2356       9136              3392   0 svchost
    580      16     4832      13972              3504   0 svchost
    167       9     1532       6772              3592   0 svchost
    527      34    13060      21116              3624   0 svchost
   1046      19    14752      20204              3836   0 svchost
    122       8     1376       5968              3976   0 svchost
    340      30     4572      13896              4012   0 svchost
    459      16     5212      13628              4084   0 svchost
    238      12     2948       8212              4436   0 svchost
    463      13     2760       9836              4444   0 svchost
    170       9     1908       6884              4452   0 svchost
    198      10     2000       7688              4684   0 svchost
    513      36    13344      19448              4708   0 svchost
    550      28     8012      20480              4800   0 svchost
    245      18     2880      10796              4848   0 svchost
    134       9     1520       7184              5036   0 svchost
    185      11     1800       7712              5284   0 svchost
    142       9     1408       6800              5304   0 svchost
    445      31    10228      18188              5388   0 svchost
    654      33    24608      36368              5432   0 svchost
    390      26    35168      35636              5488   0 svchost
    136       8     1364       5708              5676   0 svchost
    369      22     2908      10372              5700   0 svchost
    187      11     2088       8352              5752   0 svchost
    413      20     4856      17344              5800   0 svchost
    155      10     1784       6760              5940   0 svchost
    218      12     3040       9424              6496   0 svchost
    208      12     2340       9312              6620   0 svchost
    123       8     1268       5620              7224   0 svchost
    486      19    11300      25052      36,38   7684   1 svchost
    111       8     1276       6024       0,02   7744   1 svchost
    263      14     4068      18148              7832   0 svchost
    377      18     4868      22836       1,59   8136   1 svchost
    690      27    10296      39660       8,08   8184   1 svchost
    222      16     2144       6952              8536   0 svchost
    427      25     5792      19900              8724   0 svchost
    243      17     3640      14740              9000   0 svchost
    285      12     2892       8308              9188   0 svchost
    159      42     1704       6984              9304   0 svchost
    145       9     1780       7756       0,02   9368   1 svchost
    237      12     2212      11724              9380   0 svchost
    155      11     1852       8784              9548   0 svchost
    208      13     2724      10784              9624   0 svchost
    218      11     2156       9536              9652   0 svchost
    172       9     1628       7636             10500   0 svchost
    267      15     3804      17452       0,17  10572   1 svchost
    431      24     3612      12236             12652   0 svchost
    299      15     3884      17312       2,14  13236   1 svchost
    422      26     5656      18976       0,27  13404   1 svchost
    281      17     4080      15484             13520   0 svchost
    201      16     7808      11836             13856   0 svchost
    614      22     9908      25340             14084   0 svchost
    314      14     3388      12828             14260   0 svchost
    222      13     3152       9632             15796   0 svchost
    169      10     2468      10056       0,13  15840   1 svchost
    150      10     1756       8284             15932   0 svchost
    319      17     4412      16192             17280   0 svchost
    242      12     2764       9744             17372   0 svchost
    145      10     2332       8636       0,11  17892   1 svchost
   1012      22     8288      18964             19280   0 svchost
    253      21     3684      12512             20060   0 svchost
    215      23     2136       9080             23604   0 svchost
    179      10     1944       7764             23788   0 svchost
   5768       0       52       2708                 4   0 System
   1513      76   177920       1572       0,44  24848   1 SystemSettings
    433      28     8448      23136       1,94  11500   1 SystemSettingsAdminFlows
    585      28     8396      33044      19,00    448   1 SystemSettingsBroker
    350      52    14512      23396      12,41   7624   1 taskhostw
    608      26    10520      24160       0,67  20952   1 taskhostw
    585      34    26396      31188              5616   0 UDClientService
    159      10     3168       9020              5056   0 unsecapp
    140       9     1972       8704       0,13   8840   1 unsecapp
    143       9     1964       8984       0,09  11960   1 unsecapp
    143      10     2072       8464       0,08   6468   1 UserOOBEBroker
    819      35    11956      51444       1,17  20792   1 Widgets
    355      21     5392      22372       0,27  10216   1 WidgetService
    871      37    70540     119792       2,59  17916   1 WindowsTerminal
    145      12     1480       5848              1372   0 wininit
    284      14     2776      11016              1840   1 winlogon
    432      23    39800      48504              4428   0 WmiPrvSE
    278      14     2920      14180              5744   0 WMIRegistrationService
    226       8     1664       5384               992   0 WUDFHost
    518      29    12080      15640              1664   0 WUDFHost
    280      15     4100      10396              1896   0 WUDFHost
    235       9     1588       5632              2144   0 WUDFHost
    942      57    33800      57092       5,28   8912   1 WWAHost
    706      42    86748       8360       6,55  14240   1 XRiteColorAssistant
    774      40   106008      42432              5760   0 XtuService
```


🌞 **Trouver les 3 processus qui ont le plus petit identifiant**

- leur nom et leur identifiant
- ce sont forcément des processus très importants : les premiers lancés par votre OS !
- pour le compte-rendu, isolez les 3 lignes qui les concernent dans la liste de tous les processus

REPONSE : 
        Get-Process | Sort-Object Id | Select-Object -First 3

Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
      0       0       60          8                 0   0 Idle 
   5799       0       52       2708                 4   0 System
      0       0      184      50296               236   0 Secure System




🌞 **Lister tous les services de la machine...**

- avec une commande, lister tous les services qui sont en cours d'exécution
- avec une autre commande, lister tous les services qui existent mais ne sont pas lancés

REPONSE :``` 
        Get-Service | Where-Object { $_.Status -eq 'Running' }
         ```
```
Status   Name               DisplayName
------   ----               -----------
Running  AISpeechService    AISpeech Control Service
Running  Appinfo            Informations d’application
Running  AppXSvc            Service de déploiement AppX (AppXSVC)
Running  AudioEndpointBu... Générateur de points de terminaison...
Running  Audiosrv           Audio Windows
Running  BFE                Moteur de filtrage de base
Running  BITS               Service de transfert intelligent en...
Running  BluetoothUserSe... BluetoothUserService_68c3a
Running  BrokerInfrastru... Service d’infrastructure des tâches...
Running  BTAGService        Service de passerelle audio Bluetooth
Running  BthAvctpSvc        Service AVCTP
Running  bthserv            Service de prise en charge Bluetooth
Running  CameraEventService SpitCameraEventService
Running  camsvc             Service Gestionnaire d’accès aux fo...
Running  cbdhsvc_68c3a      cbdhsvc_68c3a
Running  CDPSvc             Service de plateforme des appareils...
Running  CDPUserSvc_68c3a   CDPUserSvc_68c3a
Running  ClickToRunSvc      Microsoft Office Click-to-Run Service
Running  CoreMessagingRe... CoreMessaging
Running  cplspcon           Intel(R) Content Protection HDCP Se...
Running  CryptSvc           Services de chiffrement
Running  DcomLaunch         Lanceur de processus serveur DCOM
Running  DeviceAssociati... Service d’association de périphérique
Running  DevicesFlowUser... DevicesFlowUserSvc_68c3a
Running  DevQueryBroker     Service Broker de découverte en arr...
Running  Dhcp               Client DHCP
Running  DiagTrack          Expériences des utilisateurs connec...
Running  DispBrokerDeskt... Service de stratégie d'affichage
Running  DisplayEnhancem... Service d'amélioration de l'affichage
Running  Dnscache           Client DNS
Running  DoSvc              Optimisation de livraison
Running  DPS                Service de stratégie de diagnostic
Running  dptftcs            Intel(R) Dynamic Tuning Technology ...
Running  DsSvc              Service de partage des données
Running  DusmSvc            Consommation des données
Running  EFS                Système de fichiers EFS (Encrypting...
Running  EventLog           Journal d’événements Windows
Running  EventSystem        Système d’événement COM+
Running  FontCache          Service de cache de police Windows
Running  gpsvc              Client de stratégie de groupe
Running  hidserv            Service du périphérique d’interface...
Running  hns                Service de réseau hôte
Running  HvHost             Service d'hôte HV
Running  igccservice        Intel(R) Graphics Command Center Se...
Running  ImControllerSer... System Interface Foundation Service
Running  InstallService     Installation du service Microsoft S...
Running  IntelAudioService  Intel(R) Audio Service
Running  InventorySvc       Service d’Appraisal inventaire et c...
Running  ipfsvc             Intel(R) Innovation Platform Framew...
Running  iphlpsvc           Assistance IP
Running  jhi_service        Intel(R) Dynamic Application Loader...
Running  KeyIso             Isolation de clé CNG
Running  LanmanServer       Serveur
Running  LanmanWorkstation  Station de travail
Running  LenovoFnAndFunc... Lenovo Fn and function keys service
Running  LenovoVantageSe... Critical Service for Lenovo Vantage
Running  lfsvc              Service de géolocalisation
Running  LicenseManager     Serveur Gestionnaire de licences Wi...
Running  lmhosts            Assistance NetBIOS sur TCP/IP
Running  logi_lamparray_... Logitech LampArray Service
Running  LSM                Gestionnaire de session locale
Running  MDCoreSvc          Microsoft Defender Service de base
Running  mpssvc             Pare-feu Windows Defender
Running  NahimicService     Nahimic service
Running  NcbService         Service Broker pour les connexions ...
Running  netprofm           Service Liste des réseaux
Running  NgcCtnrSvc         Conteneur Microsoft Passport
Running  NgcSvc             Microsoft Passport
Running  NPSMSvc_68c3a      NPSMSvc_68c3a
Running  nsi                Service Interface du magasin réseau
Running  nvagent            Service de virtualisation de réseau
Running  NVDisplay.Conta... NVIDIA Display Container LS
Running  OneSyncSvc_68c3a   OneSyncSvc_68c3a
Running  PcaSvc             Service de l’Assistant Compatibilit...
Running  PhoneSvc           Service téléphonique
Running  PimIndexMainten... PimIndexMaintenanceSvc_68c3a
Running  PlugPlay           Plug-and-Play
Running  Power              Alimentation
Running  PrintWorkflowUs... PrintWorkflowUserSvc_68c3a
Running  ProfSvc            Service de profil utilisateur
Running  RasMan             Gestionnaire des connexions d’accès...
Running  RmSvc              Service de gestion radio
Running  RpcEptMapper       Mappeur de point de terminaison RPC
Running  RpcLocator         Localisateur d’appels de procédure ...
Running  RpcSs              Appel de procédure distante (RPC)
Running  RtkAudioUnivers... Realtek Audio Universal Service
Running  RtkBtManServ       Realtek Bluetooth Device Manager Se...
Running  SamSs              Gestionnaire de comptes de sécurité
Running  Schedule           Planificateur de tâches
Running  SDRSVC             Sauvegarde Windows
Running  SecurityHealthS... Service Sécurité Windows
Running  SENS               Service de notification d’événement...
Running  SharedAccess       Partage de connexion Internet (ICS)
Running  ShellHWDetection   Détection matériel noyau
Running  Spooler            Spouleur d’impression
Running  SSDPSRV            Découverte SSDP
Running  SstpSvc            Service SSTP (Secure Socket Tunneli...
Running  StateRepository    Service State Repository (StateRepo...
Running  StiSvc             Acquisition d’image Windows (WIA)
Running  StorSvc            Service de stockage
Running  SysMain            SysMain
Running  SystemEventsBroker Service Broker des événements système
Running  TextInputManage... Service de gestion des entrées de t...
Running  Themes             Thèmes
Running  TimeBrokerSvc      Service Broker pour les événements ...
Running  TokenBroker        Gestionnaire de comptes web
Running  TrkWks             Client de suivi de lien distribué
Running  UDCService         Universal Device Client Service
Running  UdkUserSvc_68c3a   UdkUserSvc_68c3a
Running  UnistoreSvc_68c3a  UnistoreSvc_68c3a
Running  UserDataSvc_68c3a  UserDataSvc_68c3a
Running  UserManager        Gestionnaire des utilisateurs
Running  UsoSvc             Service Orchestrator pour les mises...
Running  VaultSvc           Gestionnaire d’informations d’ident...
Running  Wcmsvc             Gestionnaire des connexions Windows
Running  WdNisSvc           Service d’inspection réseau de l’an...
Running  WebClient          WebClient
Running  webthreatdefuse... webthreatdefusersvc_68c3a
Running  WinDefend          Service antivirus Microsoft Defender
Running  WinHttpAutoProx... Service de découverte automatique d...
Running  Winmgmt            Infrastructure de gestion Windows
Running  WlanSvc            Service de configuration automatiqu...
Running  WMIRegistration... Intel(R) Management Engine WMI Prov...
Running  WpnService         Service du système de notifications...
Running  WpnUserService_... WpnUserService_68c3a
Running  wscsvc             Centre de sécurité
Running  WSearch            Windows Search
Running  XTU3SERVICE        XTUOCDriverService
```

        Get-Service | Where-Object { $_.Status -eq 'Stopped' }
```
Status   Name               DisplayName
------   ----               -----------
Stopped  AarSvc_68c3a       AarSvc_68c3a
Stopped  AJRouter           Service de routeur AllJoyn
Stopped  ALG                Service de la passerelle de la couc...
Stopped  AppIDSvc           Identité de l’application
Stopped  AppReadiness       Préparation des applications
Stopped  AppXSvc            Service de déploiement AppX (AppXSVC)
Stopped  autotimesvc        Heure cellulaire
Stopped  AxInstSV           Programme d’installation ActiveX (A...
Stopped  BcastDVRUserSer... BcastDVRUserService_68c3a
Stopped  BDESVC             Service de chiffrement de lecteur B...
Stopped  CaptureService_... CaptureService_68c3a
Stopped  CertPropSvc        Propagation du certificat
Stopped  ClipSVC            Service de licences de client (Clip...
Stopped  CloudBackupRest... CloudBackupRestoreSvc_68c3a
Stopped  COMSysApp          Application système COM+
Stopped  ConsentUxUserSv... ConsentUxUserSvc_68c3a
Stopped  CredentialEnrol... CredentialEnrollmentManagerUserSvc_...
Stopped  dcsvc              Service de configuration (DC) déclaré
Stopped  defragsvc          Optimiser les lecteurs
Stopped  DeviceAssociati... DeviceAssociationBrokerSvc_68c3a
Stopped  DeviceInstall      Service d’installation de périphérique
Stopped  DevicePickerUse... DevicePickerUserSvc_68c3a
Stopped  diagnosticshub.... Service Collecteur standard du conc...
Stopped  diagsvc            Diagnostic Execution Service
Stopped  DmEnrollmentSvc    Service d'inscription de la gestion...
Stopped  dmwappushservice   Service de routage de messages Push...
Stopped  dot3svc            Configuration automatique de réseau...
Stopped  DsmSvc             Gestionnaire d’installation de péri...
Stopped  EapHost            Protocole EAP (Extensible Authentic...
Stopped  EasyAntiCheat_EOS  Easy Anti-Cheat (Epic Online Services)
Stopped  edgeupdate         Microsoft Edge Update Service (edge...
Stopped  edgeupdatem        Microsoft Edge Update Service (edge...
Stopped  embeddedmode       Mode incorporé
Stopped  EntAppSvc          Service de gestion des applications...
Stopped  fdPHost            Hôte du fournisseur de découverte d...
Stopped  FDResPub           Publication des ressources de décou...
Stopped  fhsvc              Service d’historique des fichiers
Stopped  FileSyncHelper     FileSyncHelper
Stopped  FontCache3.0.0.0   Cache de police de Windows Presenta...
Stopped  FrameServer        Serveur de trame de la Caméra Windows
Stopped  FrameServerMonitor Moniteur de serveur de trame Caméra...
Stopped  FvSvc              NVIDIA FrameView SDK service
Stopped  GameInputSvc       GameInput Service
Stopped  GoogleChromeEle... Google Chrome Elevation Service (Go...
Stopped  GoogleUpdaterIn... Service interne de mise à jour Goog...
Stopped  GoogleUpdaterSe... Service de mise à jour Google (Goog...
Stopped  GraphicsPerfSvc    GraphicsPerfSvc
Stopped  icssvc             Service Point d'accès sans fil mobi...
Stopped  IKEEXT             Modules de génération de clés IKE e...
Stopped  Intel(R) Platfo... Intel(R) Platform License Manager S...
Stopped  IpxlatCfgSvc       Service de configuration de convers...
Stopped  KtmRm              Service KtmRm pour Distributed Tran...
Stopped  lltdsvc            Mappage de découverte de topologie ...
Stopped  LxpSvc             Service d'expérience linguistique
Stopped  MapsBroker         Gestionnaire des cartes téléchargées
Stopped  McpManagementSe... McpManagementService
Stopped  MessagingServic... MessagingService_68c3a
Stopped  MicrosoftEdgeEl... Microsoft Edge Elevation Service (M...
Stopped  MixedRealityOpe... Service Windows Mixed Reality OpenXR
Stopped  MozillaMaintenance Mozilla Maintenance Service
Stopped  MSDTC              Coordinateur de transactions distri...
Stopped  MSiSCSI            Service Initiateur iSCSI de Microsoft
Stopped  msiserver          Windows Installer
Stopped  NaturalAuthenti... Authentification naturelle
Stopped  NcaSvc             Assistant Connectivité réseau
Stopped  NcdAutoSetup       Configuration automatique des périp...
Stopped  Netlogon           Netlogon
Stopped  Netman             Connexions réseau
Stopped  NetSetupSvc        Service Configuration du réseau
Stopped  NetTcpPortSharing  Service de partage de ports Net.Tcp
Stopped  NlaSvc             Connaissance des emplacements réseau
Stopped  NvContainerLoca... NVIDIA LocalSystem Container
Stopped  OneDrive Update... OneDrive Updater Service
Stopped  p2pimsvc           Identity Manager réseau homologue
Stopped  p2psvc             Groupement de mise en réseau de pairs
Stopped  P9RdrService_68c3a P9RdrService_68c3a
Stopped  PenService_68c3a   PenService_68c3a
Stopped  perceptionsimul... Service de simulation de perception...
Stopped  PerfHost           Hôte de DLL de compteur de performance
Stopped  pla                Journaux & alertes de performance
Stopped  PNRPAutoReg        Service de publication des noms d’o...
Stopped  PNRPsvc            Protocole PNRP
Stopped  PolicyAgent        Agent de stratégie IPsec
Stopped  PrintNotify        Extensions et notifications d’impri...
Stopped  PushToInstall      Service PushToInstall de Windows
Stopped  QWAVE              Expérience audio-vidéo haute qualit...
Stopped  RasAuto            Gestionnaire des connexions automat...
Stopped  RemoteAccess       Routage et accès distant
Stopped  RemoteRegistry     Registre à distance
Stopped  RetailDemo         Service de démo du magasin
Stopped  SCardSvr           Carte à puce
Stopped  ScDeviceEnum       Service d’énumération de périphériq...
Stopped  SCPolicySvc        Stratégie de retrait de la carte à ...
Stopped  seclogon           Ouverture de session secondaire
Stopped  SEMgrSvc           Gestionnaires des paiements et des ...
Stopped  SensorDataService  Service Données de capteur
Stopped  SensorService      Service de capteur
Stopped  SensrSvc           Service de surveillance des capteurs
Stopped  SessionEnv         Configuration des services Bureau à...
Stopped  SgrmBroker         Service Broker du moniteur d'exécut...
Stopped  SharedRealitySvc   Service de données spatiales
Stopped  shpamsvc           Shared PC Account Manager
Stopped  smphost            SMP de l’Espace de stockages Microsoft
Stopped  SmsRouter          Service Routeur SMS Microsoft Windows.
Stopped  SNMPTrap           Interruption SNMP
Stopped  spectrum           Service de perception Windows
Stopped  sppsvc             Protection logicielle
Stopped  ssh-agent          OpenSSH Authentication Agent
Stopped  Steam Client Se... Steam Client Service
Stopped  svsvc              Vérificateur de points
Stopped  swprv              Fournisseur de cliché instantané de...
Stopped  TapiSrv            Téléphonie
Stopped  TermService        Services Bureau à distance
Stopped  TieringEngineSe... Gestion des niveaux de stockage
Stopped  TroubleshootingSvc Service de résolution des problèmes...
Stopped  TrustedInstaller   Programme d’installation pour les m...
Stopped  tzautoupdate       Programme de mise à jour automatiqu...
Stopped  uhssvc             Microsoft Update Health Service
Stopped  UmRdpService       Redirecteur de port du mode utilisa...
Stopped  upnphost           Hôte de périphérique UPnP
Stopped  VacSvc             Service de composition audio volumé...
Stopped  vds                Disque virtuel
Stopped  vgc                vgc
Stopped  vmcompute          Service de calcul hôte Hyper-V
Stopped  vmicguestinterface Interface de services d’invité Hyper-V
Stopped  vmicheartbeat      Service Pulsation Microsoft Hyper-V
Stopped  vmickvpexchange    Service Échange de données Microsof...
Stopped  vmicrdv            Service de virtualisation Bureau à ...
Stopped  vmicshutdown       Service Arrêt de l’invité Microsoft...
Stopped  vmictimesync       Service Synchronisation date/heure ...
Stopped  vmicvmsession      Service Hyper-V PowerShell Direct
Stopped  vmicvss            Requête du service VSS Hyper-V
Stopped  VSS                Cliché instantané des volumes
Stopped  W32Time            Temps Windows
Stopped  WaaSMedicSvc       WaaSMedicSvc
Stopped  WalletService      WalletService
Stopped  WarpJITSvc         Warp JIT Service
Stopped  wbengine           Service de moteur de sauvegarde en ...
Stopped  WbioSrvc           Service de biométrie Windows
Stopped  wcncsvc            Windows Connect Now - Registre de c...
Stopped  WdiServiceHost     Service hôte WDIServiceHost
Stopped  WdiSystemHost      Hôte système de diagnostics
Stopped  webthreatdefsvc    Service Web Threat Defense
Stopped  Wecsvc             Collecteur d’événements de Windows
Stopped  WEPHOSTSVC         Service hôte du fournisseur de chif...
Stopped  wercplsupport      Prise en charge du Panneau de confi...
Stopped  WerSvc             Service de rapport d’erreurs Windows
Stopped  WFDSConMgrSvc      Service Wi-Fi Direct Service de ges...
Stopped  WiaRpc             Événements d’acquisition d’images f...
Stopped  WinRM              Gestion à distance de Windows (Gest...
Stopped  wisvc              Service Windows Insider
Stopped  wlidsvc            Assistant Connexion avec un compte ...
Stopped  wlpasvc            Service de l’Assistant de profil local
Stopped  WManSvc            Service de gestion de Windows
Stopped  wmiApSrv           Carte de performance WMI
Stopped  WMPNetworkSvc      Service de partage réseau du Lecteu...
Stopped  workfolderssvc     Dossiers de travail
Stopped  WpcMonSvc          Contrôle parental
Stopped  WPDBusEnum         Service Énumérateur d’appareil mobile
Stopped  wuauserv           Windows Update
Stopped  WwanSvc            Service de configuration automatiqu...
Stopped  XblAuthManager     Gestionnaire d'authentification Xbo...
Stopped  XblGameSave        Jeu sauvegardé sur Xbox Live
Stopped  XboxGipSvc         Xbox Accessory Management Service
Stopped  XboxNetApiSvc      Service de mise en réseau Xbox Live
```


### 2. Mémoire et CPU
La mémoire c'est la mémoire vive ou RAM. Le terme mémoire ne fera jamais référence à votre disque dur ou quoi. Mémoire, c'est la RAM.
🌞 RAM

afficher la quantité de RAM totale de la machine
REPONSE :```    
        (Get-CimInstance -ClassName Win32_ComputerSystem).TotalPhysicalMemory / 1GB
         ```
```
15,714714050293
```
afficher la quantité de RAM libre sur la machine
REPONSE : ```
        (Get-CimInstance -ClassName Win32_OperatingSystem).FreePhysicalMemory  / 1GB
        ```
```
0,00676391646265984
```
🌞 CPU

afficher l'utilisation du CPU
ça peut être la charge CPU (CPU load) ou une utilisation en %

REPONSE : 
        ```
        Get-CimInstance -ClassName Win32_Processor | Select-Object -Property LoadPercentage
        ```
```
LoadPercentage
--------------
            21
```

### 3. Stockage

            🌞 Périphériques

            lister les périphériques de stockage
            je veux voir les disques durs branchés à votre PC, pas les partitions
            genre je veux pas voir C: dans le retour de la commande, plutôt la marque du disque dur, et sa taille

```            REPONSE :
                Get-WmiObject -Class Win32_DiskDrive | Select-Object -Property Model, Size
```
```
            Model                          Size
            -----                          ----
            SAMSUNG MZVL2512HDJD-00BL2      512105932800
```
            🌞 Partitions

            lister les partitions du système
            sur Windows, les partitions sont notamment C:, D: etc, mais y'en a d'autres qui ne sont pas utilisées actuellement et qui n'utilisent donc pas de lettres comme D:
```
            REPONSE : 
                Get-WmiObject -Class Win32_DiskPartition | Select-Object -Property Name, Size
```
```
            Name                           Size
            ----                           ----
            Disque n° 0, partition n° 0    272629760
            Disque n° 0, partition n° 1    509722230784
            Disque n° 0, partition n° 2    2097152000
```
            🌞 Espace disque

            afficher l'espace disque restant sur votre partition principale
            sur Windows, c'est C: la partition principale
```
            REPONSE : 
                Get-PSDrive -Name C | Select-Object -Property Used, Free
```
```
            Used                           Free
            ----                           ----
            171566952448                   338155274240
```

### 4. Réseau
Le réseau fait référence à la gestion des cartes réseau de votre PC. Ca fait aussi référence à la gestion des connexions réseau.
Une carte réseau c'est un périphérique qui permet d'envoyer et recevoir des octets avec un câble (ou des ondes WiFi). L'OS se charge d'attribuer une adresse IP sur chaque carte réseau.
Une connexion réseau c'est quand tu lances un programme qui a besoin de se connecter à un service réseau. Genre quand tu joues à LoL ou Minecraft, ou que t'es sur Youtube, tu te connectes à un serveur : tu fais une connexion réseau.
🌞 Cartes réseau

afficher la liste des cartes réseau de votre PC
on doit voit apparaître leur adresse IP et leur nom

``` REPONSE : 
    Get-NetIPAddress | Select-Object -Property InterfaceAlias, IPAddress
```
```
InterfaceAlias               IPAddress
--------------               ---------
Connexion au réseau local* 2 fe80::d5a3:931e:1013:337f%12
Ethernet                     fe80::2fec:f819:38ca:2e75%14
Connexion au réseau local* 1 fe80::ed5c:9d54:ae4d:c5c7%15
Connexion réseau Bluetooth   fe80::5c52:30da:d913:8282%9
Wi-Fi                        fe80::701b:1854:465d:255a%13
Loopback Pseudo-Interface 1  ::1
Connexion au réseau local* 2 169.254.140.247
Ethernet                     169.254.182.37
Connexion au réseau local* 1 169.254.105.72
Connexion réseau Bluetooth   169.254.179.8
Wi-Fi                        172.20.10.2
```
🌞 Connexions réseau

lister les connexions réseau actuellement en cours
"actuellement en cours" c'est qu'elles sont dans l'état "établi" ou "established" en anglais
on doit voir apparaître :

l'adresse IP du serveur auquel vous êtes connectés
le nom et/ou l'identifiant du processus responsable de cette connexion
```
REPONSE : 
    Get-NetTCPConnection -State Established | Select-Object -Property RemoteAddress, OwningProcess
```
```
RemoteAddress  OwningProcess
-------------  -------------
52.20.21.250            22964
172.65.251.78           22964
140.82.112.21           25440
140.82.112.21           21368
152.199.19.160          21368
140.82.112.26           22964
2.18.177.86             16192
52.182.143.210          21368
142.250.110.188         22964
20.54.36.229             5800
162.159.134.234         16192
127.0.0.1                5532
127.0.0.1                5532
127.0.0.1                1896
127.0.0.1                1896
127.0.0.1                3080
127.0.0.1                3080
127.0.0.1                1664
127.0.0.1                1664
```

### 5. Utilisateurs

🌞 Lister les utilisateurs de la machine

on devrait voir au moins :

votre utilisateur

l'utilisateur qui est administrateur sur la machine
```
REPONSE : 
    Get-LocalUser
```
```
Name               Enabled Description
----               ------- -----------
Administrateur     False   Compte d’utilisateur d’administration
DefaultAccount     False   Compte utilisateur géré par le système.
emrep              True
Invité             False   Compte d’utilisateur invité
WDAGUtilityAccount False   Compte d’utilisateur géré et utilisé par le système pour les scénarios Windows Defender Application Guard.
```
🌞 Heure de login

déterminer à quelle heure précisément vous avez ouvert votre session utilisateur
```
REPONSE : 
    (Get-WmiObject -Class Win32_LogonSession | Where-Object { $_.LogonType -eq 2 }) | ForEach-Object { $_.StartTime }
```
```
20241024075350.423649+120
20241024075350.417929+120
```
🌞 Lister les processus en cours d'exécution

cette fois, on doit voir apparaître en plus le nom de l'utilisateur qui a lancé chacun d'entre eux
```
REPONSE : 
    Get-Process | Select-Object -Property Id, ProcessName, @{Name="UserName";Expression={(Get-WmiObject -Class Win32_Process -Filter "ProcessId=$($_.Id)").GetOwner().User}}
```
```
  Id ProcessName          UserName
  -- -----------          --------
7952 AggregatorHost
5460 AISControlService
7212 ApplicationFrameHost emrep
6296 AppVShNotify         emrep
...6 audiodg
...4 backgroundTaskHost   emrep
...8 backgroundTaskHost   emrep
...4 backgroundTaskHost   emrep
7164 chrome               emrep
9868 chrome               emrep
9976 chrome               emrep
...8 chrome               emrep
...8 chrome
...8 chrome               emrep
...2 chrome               emrep
...2 chrome               emrep
...8 chrome               emrep
...4 chrome               emrep
...4 chrome               emrep
...8 chrome
...8 chrome               emrep
...4 chrome               emrep
...6 chrome               emrep
2900 Code                 emrep
6264 Code                 emrep
7044 Code                 emrep
...2 Code                 emrep
...2 Code                 emrep
...0 Code                 emrep
...2 Code                 emrep
...8 Code                 emrep
...0 Code                 emrep
2584 CodeSetup-stable-... emrep
5784 CodeSetup-stable-... emrep
...4 conhost              emrep
...4 CrossDeviceService   emrep
1260 csrss
1380 csrss
...4 ctfmon               emrep
...0 dasHost
...8 DataExchangeHost     emrep
...8 Discord              emrep
...8 Discord              emrep
...8 Discord              emrep
...0 Discord              emrep
...2 Discord              emrep
...2 Discord              emrep
...2 DismHost             emrep
8008 dllhost              emrep
...2 dllhost              emrep
...8 dllhost              emrep
...8 dllhost              emrep
2396 dwm
9140 explorer             emrep
...2 FnHotkeyCapsLKNumLK  emrep
5564 FnHotkeyUtility      emrep
1624 fontdrvhost
1940 fontdrvhost
   0 Idle
5624 IntelAudioService
2056 IntelCpHDCPSvc
8716 ipf_helper           emrep
5668 ipf_uf
5532 ipfsvc
5660 jhi_service
5572 Lenovo.Modern.ImC...
5540 LenovoUtilityService
...0 LenovoVantage-(De...
8752 LenovoVantage-(Ge... emrep
8460 LenovoVantage-(Le...
...2 LenovoVantage-(Va...
...0 LenovoVantageService
7600 Locator
...6 LockApp              emrep
5736 logi_lamparray_se...
1464 LsaIso
1480 lsass
3280 Memory Compression
...0 Microsoft.SharePoint emrep
...2 MoUsoCoreWorker
...4 MpDefenderCoreSer...
1800 msedgewebview2       emrep
6024 msedgewebview2       emrep
9640 msedgewebview2       emrep
...8 msedgewebview2       emrep
...6 msedgewebview2       emrep
...0 msedgewebview2       emrep
...6 msedgewebview2       emrep
...6 MsMpEng
...2 Nahimic3             emrep
9156 nahimicNotifSys      emrep
5588 NahimicService
...0 NahimicSvc32         emrep
...8 NahimicSvc64         emrep
4520 NisSrv
3080 NVDisplay.Container
3700 NVDisplay.Container
...0 OfficeClickToRun
5516 OneApp.IGCC.WinSe...
...2 OpenConsole          emrep
...6 PhoneExperienceHost  emrep
8408 powershell           emrep
9728 PrintDialog          emrep
 268 Registry
8876 RiotClientCrashHa... emrep
4464 RiotClientServices   emrep
5632 RtkAudUService64
...8 RtkAudUService64     emrep
5728 RtkBtManServ
1696 RuntimeBroker        emrep
3688 RuntimeBroker        emrep
...4 RuntimeBroker        emrep
...4 RuntimeBroker        emrep
...8 RuntimeBroker        emrep
...4 RuntimeBroker        emrep
...2 RuntimeBroker        emrep
...0 RuntimeBroker        emrep
...8 RuntimeBroker        emrep
...6 RuntimeBroker        emrep
8352 SearchFilterHost
9684 SearchHost           emrep
...4 SearchIndexer
7948 SearchProtocolHost
 236 Secure System
...2 SecurityHealthSer...
...2 SecurityHealthSys... emrep
3292 SEGameTool           emrep
1444 services
...0 ShellExperienceHost  emrep
7628 sihost               emrep
 888 smss
5476 SpitCamSrv
5136 spoolsv
8836 StartMenuExperien... emrep
1440 svchost
1600 svchost
1732 svchost
1748 svchost
1780 svchost
2016 svchost
2064 svchost
2112 svchost
2152 svchost
2260 svchost
2600 svchost
2684 svchost
2708 svchost
2760 svchost
2940 svchost
2948 svchost
3008 svchost
3136 svchost
3168 svchost
3196 svchost
3204 svchost
3212 svchost
3316 svchost
3384 svchost
3392 svchost
3504 svchost
3592 svchost
3624 svchost
3836 svchost
3976 svchost
4012 svchost
4084 svchost
4436 svchost
4444 svchost
4452 svchost
4684 svchost
4708 svchost
4800 svchost
4848 svchost
5036 svchost
5284 svchost
5304 svchost
5388 svchost
5432 svchost
5488 svchost
5676 svchost
5700 svchost
5752 svchost
5800 svchost
5940 svchost
6496 svchost
6620 svchost
7224 svchost
7684 svchost              emrep
7744 svchost              emrep
7832 svchost
8136 svchost              emrep
8184 svchost              emrep
8536 svchost
8724 svchost
9000 svchost
9188 svchost
9304 svchost
9368 svchost              emrep
9380 svchost
9548 svchost
9624 svchost
9652 svchost
...2 svchost              emrep
...2 svchost
...6 svchost              emrep
...4 svchost              emrep
...0 svchost
...6 svchost
...4 svchost
...0 svchost
...8 svchost
...6 svchost
...0 svchost              emrep
...2 svchost
...0 svchost
...2 svchost
...2 svchost              emrep
...0 svchost
...0 svchost
...4 svchost
...8 svchost
   4 System
...8 SystemSettings       emrep
...0 SystemSettingsAdm... emrep
 448 SystemSettingsBroker emrep
7624 taskhostw            emrep
...2 taskhostw            emrep
5616 UDClientService
5056 unsecapp
8840 unsecapp             emrep
...0 unsecapp             emrep
6468 UserOOBEBroker       emrep
...2 Widgets              emrep
...6 WidgetService        emrep
...6 WindowsTerminal      emrep
1372 wininit
1840 winlogon
4428 WmiPrvSE
5900 WmiPrvSE
5744 WMIRegistrationSe...
 992 WUDFHost
1664 WUDFHost
1896 WUDFHost
2144 WUDFHost
8912 WWAHost              emrep
...0 XRiteColorAssistant  emrep
5760 XtuService
```
🌞 Sur un fichier random qui se trouve dans votre dossier Téléchargements/

déterminer quel utilisateur est le propriétaire du fichier
chaque fichier a un propriétaire, qui peut tout faire sur le fichier, et empêcher les autres utilisateurs de le lire
```
REPONSE : 
    Get-Acl -Path "C:\Users\emrep\Downloads\16944506258_8da4cc35ec_h.jpg" | Select-Object -ExpandProperty Owner
```
```
LAPTOP-82V3F554\emrep
```
### 6. Random
🌞 Uptime
afficher l'heure/la date de l'allumage de la machine
```
REPONSE : 
    (Get-CimInstance -ClassName Win32_OperatingSystem).LastBootUpTime
```
```
jeudi 24 octobre 2024 07:53:10
```
🌞 Device

afficher le modèle du processeur de la machine
```
REPONSE : 
    Get-CimInstance -ClassName Win32_Processor | Select-Object -Property Name
```
```
Name
----
Intel(R) Core(TM) i7-14650HX
```
🌞 Version

afficher le nom et la version exacte de votre OS
```
REPONSE : 
Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object Caption, Version
```
```
Caption                      Version
-------                      -------
Microsoft Windows 11 Famille 10.0.22631
```
🌞 Mise à jour

afficher la date et l'heure de la dernière mise à jour
```
REPONSE : 
    (Get-HotFix | Sort-Object InstalledOn -Descending | Select-Object -First 1)
```
```
Source        Description      HotFixID      InstalledBy          InstalledOn
------        -----------      --------      -----------          -----------
LAPTOP-82V... Security Update  KB5044285     AUTORITE NT\Système  16/10/2024 00:00:00
```

### 7. Ptit amusement
Mise en situation réelle d'une petite investigation sur votre PC, avec le terminal, liés aux notions qu'on a vu.
🌞 Lister les connexions actives

lister les connexions réseau actuellement en cours

choisir l'une des lignes comme cible, une sur laquelle vous souhaiterez obtenir plus d'infos
notez en particulier :

l'adresse IP que vous avez utilisé pour vous connecter à ce serveur (dans une colonne)
l'adresse IP du serveur auquel vous êtes connectés (dans l'autre colonne :d)
le nom/l'identifiant du programme qui fait cette connexion
```
REPONSE : 
    Get-NetTCPConnection -State Established | Select-Object -Property RemoteAddress, OwningProcess
```
```
RemoteAddress   OwningProcess
-------------   -------------
140.82.113.22           21368
34.120.22.49            22964
20.189.173.6            21368
64.233.184.188          22964
172.65.251.78           22964
140.82.114.25           22964
140.82.112.25           22964
20.54.36.229             5800
162.159.134.234         16192
```
🌞 En apprendre + sur le processus en cours d'exécution

à l'aide de son nom ou de son identifiant repéré, déterminez (sûrement en plusieurs commandes) :

son nom et/ou son identifiant si vous ne l'avez pas déjà
l'utilisation RAM de ce processus
l'utilisateur qui a lancé de processus
```
REPONSE :
    Get-Process -Id 22964 | Select-Object -Property Id, ProcessName, @{Name="MemoryUsage(MB)";Expression={[math]::round($_.WorkingSet64/1MB,2)}}, @{Name="UserName";Expression={(Get-WmiObject -Class Win32_Process -Filter "ProcessId=$($_.Id)").GetOwner().User}}
```
```
   Id ProcessName MemoryUsage(MB) UserName
   -- ----------- --------------- --------
22964 chrome                 49,5 emrep
```
🌞 En apprendre + sur le programme

déterminer le chemin vers le programme (vers le fichier .exe sous Windows)

genre le dossier où il se trouve quoi
```
REPONSE :
    Get-Process -Id 22964 | Select-Object -Property Path
```
```
Path
----
C:\Program Files\Google\Chrome\Application\chrome.exe
```
déterminer qui est l'utilisateur qui est propriétaire du programme (le fichier exécutable)
```
REPONSE :
    Get-Acl -Path (Get-Process -Id 22964).Path | Select-Object -ExpandProperty Owner
```
```
BUILTIN\Administrateurs
```
🌞 En apprendre + sur l'adresse IP

utilise ma commande magique pour ça :

# Sur Windows
Invoke-RestMethod -Method Get -Uri http://ip-api.com/json/52.20.21.250
```
REPONSE :

status      : success
country     : United States
countryCode : US
region      : VA
regionName  : Virginia
city        : Ashburn
zip         : 20149
lat         : 39,0438
lon         : -77,4874
timezone    : America/New_York
isp         : Amazon.com, Inc.
org         : AWS EC2 (us-east-1)
as          : AS14618 Amazon.com, Inc.
query       : 52.20.21.250
```
🌞 Délai

mesurer la latence entre vous et ce serveur
ça se fait en utilisant la commande ping : ping <ADRESSE IP>

par exemple, pour envoyer des ptits Pings vers l'adresse IP 52.20.21.250 : ping 52.20.21.250

généralement vous avez une valeur en millisecondes : le temps qu'un message Ping fasse l'aller-retour entre vous et le serveur

Ping est un message extrêmement simpliste, le plus simpliste qu'on peut faire en fait. On veut juste un ptit message pour tester le temps d'aller-retour vers un serveur.
```
REPONSE :
    ping 52.20.21.250

Envoi d’une requête 'Ping'  52.20.21.250 avec 32 octets de données :
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.

Statistiques Ping pour 52.20.21.250:
    Paquets : envoyés = 4, reçus = 0, perdus = 4 (perte 100%),
```