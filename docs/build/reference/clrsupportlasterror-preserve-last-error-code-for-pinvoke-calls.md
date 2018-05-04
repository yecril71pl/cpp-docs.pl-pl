---
title: -CLRSUPPORTLASTERROR (Zachowaj kod ostatniego błędu dla wywołań PInvoke) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRSUPPORTLASTERROR
dev_langs:
- C++
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 297414aa71e9d871da795c2ffe567573237c7e0e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR (Zachowaj kod ostatniego błędu dla wywołań PInvoke)
**/ CLRSUPPORTLASTERROR**, który jest domyślnie włączona, zachowuje ostatni kod błędu funkcji wywołanych za pomocą mechanizmu P/Invoke, dzięki czemu można wywoływać funkcje natywne w bibliotekach DLL, z kodu skompilowanego z **/CLR**.  
  
## <a name="syntax"></a>Składnia  
  
```  
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}  
```  
  
## <a name="remarks"></a>Uwagi  
 Zachowuje ostatni kod błędu oznacza spadek wydajności.  Jeśli nie chcesz pociągnąć za sobą jego wpływ na wydajność zachowuje ostatni kod błędu, łącze z **/CLRSUPPORTLASTERROR:NO**.  
  
 Można zminimalizować wpływ na wydajność przez łączenie z **/CLRSUPPORTLASTERROR:SYSTEMDLL**, który zachowuje wyłącznie kod ostatniego błędu dla funkcji w systemie biblioteki dll.  Biblioteki DLL systemu jest zdefiniowany jako jedną z następujących czynności:  
  
|||||  
|-|-|-|-|  
|ACLUI. BIBLIOTEKI DLL|ACTIVEDS. BIBLIOTEKI DLL|ADPTIF. BIBLIOTEKI DLL|ADVAPI32. BIBLIOTEKI DLL|  
|ASYCFILT. BIBLIOTEKI DLL|AUTORYZACJA. BIBLIOTEKI DLL|AVICAP32. BIBLIOTEKI DLL|AVIFIL32. BIBLIOTEKI DLL|  
|PLIK CABINET. BIBLIOTEKI DLL|CLUSAPI. BIBLIOTEKI DLL|COMCTL32. BIBLIOTEKI DLL|COMDLG32. BIBLIOTEKI DLL|  
|COMSVCS. BIBLIOTEKI DLL|CREDUI. BIBLIOTEKI DLL|OKREŚLONY PRZEZ CRYPT32. BIBLIOTEKI DLL|CRYPTNET. BIBLIOTEKI DLL|  
|CRYPTUI. BIBLIOTEKI DLL|D3D8THK. BIBLIOTEKI DLL|DBGENG. BIBLIOTEKI DLL|DBGHELP. BIBLIOTEKI DLL|  
|DCIMAN32. BIBLIOTEKI DLL|DNSAPI. BIBLIOTEKI DLL|DSPROP. BIBLIOTEKI DLL|DSUIEXT. BIBLIOTEKI DLL|  
|GDI32. BIBLIOTEKI DLL|GLU32. BIBLIOTEKI DLL|HLINK. BIBLIOTEKI DLL|ICM32. BIBLIOTEKI DLL|  
|IMAGEHLP. BIBLIOTEKI DLL|IMM32. BIBLIOTEKI DLL|IPHLPAPI. BIBLIOTEKI DLL|IPROP. BIBLIOTEKI DLL|  
|KERNEL32. BIBLIOTEKI DLL|KSUSER. BIBLIOTEKI DLL|LOADPERF. BIBLIOTEKI DLL|LZ32. BIBLIOTEKI DLL|  
|MAPI32. BIBLIOTEKI DLL|BIBLIOTECE MGMTAPI. BIBLIOTEKI DLL|POLECENIE MOBSYNC. BIBLIOTEKI DLL|MPR. BIBLIOTEKI DLL|  
|MPRAPI. BIBLIOTEKI DLL|MQRT. BIBLIOTEKI DLL|MSACM32. BIBLIOTEKI DLL|MSCMS. BIBLIOTEKI DLL|  
|MSI. BIBLIOTEKI DLL|MSIMG32. BIBLIOTEKI DLL|MSRATING. BIBLIOTEKI DLL|MSTASK. BIBLIOTEKI DLL|  
|MSVFW32. BIBLIOTEKI DLL|MSWSOCK. BIBLIOTEKI DLL|MTXEX. BIBLIOTEKI DLL|NDDEAPI. BIBLIOTEKI DLL|  
|NETAPI32. BIBLIOTEKI DLL|NPPTOOLS. BIBLIOTEKI DLL|NTDSAPI. BIBLIOTEKI DLL|NTDSBCLI. BIBLIOTEKI DLL|  
|NTMSAPI. BIBLIOTEKI DLL|ODBC32. BIBLIOTEKI DLL|ODBCBCP. BIBLIOTEKI DLL|OLE32. BIBLIOTEKI DLL|  
|OLEACC. BIBLIOTEKI DLL|OLEAUT32. BIBLIOTEKI DLL|OLEDLG. BIBLIOTEKI DLL|OPENGL32. BIBLIOTEKI DLL|  
|PDH. BIBLIOTEKI DLL|PLIKU POWRPROF. BIBLIOTEKI DLL|QOSNAME. BIBLIOTEKI DLL|ZAPYTANIE. BIBLIOTEKI DLL|  
|RASAPI32. BIBLIOTEKI DLL|RASDLG. BIBLIOTEKI DLL|RASSAPI. BIBLIOTEKI DLL|RESUTILS. BIBLIOTEKI DLL|  
|RICHED20. BIBLIOTEKI DLL|RPCNS4. BIBLIOTEKI DLL|RPCRT4. BIBLIOTEKI DLL|RTM. BIBLIOTEKI DLL|  
|NARZĘDZI RTUTILS. BIBLIOTEKI DLL|SCARDDLG. BIBLIOTEKI DLL|SECUR32. BIBLIOTEKI DLL|SENSAPI. BIBLIOTEKI DLL|  
|SETUPAPI. BIBLIOTEKI DLL|STEROWANIA PRODUKCJĄ. BIBLIOTEKI DLL|SHELL32. BIBLIOTEKI DLL|SHFOLDER. BIBLIOTEKI DLL|  
|SHLWAPI. BIBLIOTEKI DLL|SISBKUP. BIBLIOTEKI DLL|SNMPAPI. BIBLIOTEKI DLL|SRCLIENT. BIBLIOTEKI DLL|  
|STI. BIBLIOTEKI DLL|TAPI32. BIBLIOTEKI DLL|RUCH W SIECI. BIBLIOTEKI DLL|ADRES URL. BIBLIOTEKI DLL|  
|URLMON. BIBLIOTEKI DLL|USER32. BIBLIOTEKI DLL|USERENV. BIBLIOTEKI DLL|USP10. BIBLIOTEKI DLL|  
|UXTHEME. BIBLIOTEKI DLL|VDMDBG. BIBLIOTEKI DLL|WERSJA. BIBLIOTEKI DLL|WINFAX. BIBLIOTEKI DLL|  
|WINHTTP. BIBLIOTEKI DLL|WININET. BIBLIOTEKI DLL|WINMM. BIBLIOTEKI DLL|WINSCARD. BIBLIOTEKI DLL|  
|WINTRUST. BIBLIOTEKI DLL|WLDAP32. BIBLIOTEKI DLL|WOW32. BIBLIOTEKI DLL|WS2_32.DLL|  
|WSNMP32. BIBLIOTEKI DLL|WSOCK32.DLL|WTSAPI32. BIBLIOTEKI DLL|XOLEHLP. BIBLIOTEKI DLL|  
  
> [!NOTE]
>  Zachowuje ostatni błąd nie jest obsługiwana dla niezarządzanych funkcji, które są używane przez kod CLR, w tym samym module.  
  
-   Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **konsolidatora** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji do **dodatkowe opcje** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład definiuje natywnej biblioteki DLL z jednego wyeksportowanej funkcji, które modyfikuje ostatniego błędu.  
  
```  
// CLRSUPPORTLASTERROR_dll.cpp  
// compile with: /LD  
#include <windows.h>  
#include <math.h>  
  
#pragma unmanaged  
__declspec(dllexport) double MySqrt(__int64 n) {  
   SetLastError(DWORD(-1));  
   return sqrt(double(n));  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład korzysta z biblioteki DLL, pokazuje sposób użycia **/CLRSUPPORTLASTERROR**.  
  
```  
// CLRSUPPORTLASTERROR_client.cpp  
// compile with: /clr CLRSUPPORTLASTERROR_dll.lib /link /clrsupportlasterror:systemdll  
// processor: x86  
#include <windows.h>  
#include <wininet.h>  
#include <stdio.h>  
#include <math.h>  
  
#pragma comment(lib, "wininet.lib")  
  
double MySqrt(__int64 n);  
  
#pragma managed  
int main() {  
   double   d = 0.0;  
   __int64 n = 65;  
   HANDLE  hGroup = NULL;  
   GROUPID groupID;  
   DWORD   dwSet = 127, dwGet = 37;  
  
   SetLastError(dwSet);  
   d = MySqrt(n);  
   dwGet = GetLastError();  
  
   if (dwGet == DWORD(-1))  
      printf_s("GetLastError for application call succeeded (%d).\n",  
             dwGet);  
   else  
      printf_s("GetLastError for application call failed (%d).\n",  
             dwGet);  
  
   hGroup = FindFirstUrlCacheGroup(0, CACHEGROUP_SEARCH_ALL,  
                           0, 0, &groupID, 0);  
   dwGet = GetLastError();  
   if (dwGet == 183)  
      printf_s("GetLastError for system call succeeded (%d).\n",  
             dwGet);  
   else  
      printf_s("GetLastError for system call failed (%d).\n",  
             dwGet);  
}  
```  
  
```Output  
GetLastError for application call failed (127).  
GetLastError for system call succeeded (183).  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)