---
title: /CLRSUPPORTLASTERROR (Zachowaj kod ostatniego błędu dla wywołań PInvoke)
ms.date: 11/04/2016
f1_keywords:
- /CLRSUPPORTLASTERROR
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
ms.openlocfilehash: 5e4a5c86e53d74c8b704ee3780991d496fc1802a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807679"
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR (Zachowaj kod ostatniego błędu dla wywołań PInvoke)

**/ CLRSUPPORTLASTERROR**, która jest domyślnie włączona, zachowuje kod ostatniego błędu funkcji wywoływanym za pośrednictwem mechanizmu P/Invoke, dzięki czemu można wywoływać funkcje natywne w bibliotekach DLL, z kodu skompilowanego z **/CLR**.

## <a name="syntax"></a>Składnia

```
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}
```

## <a name="remarks"></a>Uwagi

Zachowywanie kod ostatniego błędu oznacza spadek wydajności.  Jeśli nie chcesz ponosić wpływ na wydajność zachowania kod ostatniego błędu, połączyć z **/CLRSUPPORTLASTERROR:NO**.

Można zminimalizować wpływ na wydajność dzięki połączeniu z **/CLRSUPPORTLASTERROR:SYSTEMDLL**, który tylko zachowuje kod ostatniego błędu dla funkcji w systemie biblioteki dll.  Biblioteki DLL systemu jest zdefiniowany jako jeden z następujących czynności:

|||||
|-|-|-|-|
|ACLUI.DLL|ACTIVEDS.DLL|ADPTIF.DLL|ADVAPI32.DLL|
|ASYCFILT.DLL|AUTHZ.DLL|AVICAP32.DLL|AVIFIL32.DLL|
|PLIK CABINET. BIBLIOTEKI DLL|CLUSAPI.DLL|COMCTL32.DLL|COMDLG32.DLL|
|COMSVCS.DLL|CREDUI.DLL|CRYPT32.DLL|CRYPTNET.DLL|
|CRYPTUI.DLL|D3D8THK.DLL|DBGENG. BIBLIOTEKI DLL|DBGHELP.DLL|
|DCIMAN32.DLL|DNSAPI.DLL|DSPROP.DLL|DSUIEXT.DLL|
|GDI32.DLL|GLU32.DLL|HLINK.DLL|ICM32.DLL|
|IMAGEHLP.DLL|IMM32.DLL|IPHLPAPI.DLL|IPROP.DLL|
|KERNEL32.DLL|KSUSER.DLL|LOADPERF.DLL|LZ32.DLL|
|MAPI32.DLL|MGMTAPI.DLL|MOBSYNC.DLL|MPR.DLL|
|MPRAPI.DLL|MQRT.DLL|MSACM32.DLL|MSCMS.DLL|
|MSI.DLL|MSIMG32.DLL|MSRATING. BIBLIOTEKI DLL|MSTASK.DLL|
|MSVFW32.DLL|MSWSOCK.DLL|MTXEX.DLL|NDDEAPI.DLL|
|NETAPI32.DLL|NPPTOOLS. BIBLIOTEKI DLL|NTDSAPI.DLL|NTDSBCLI.DLL|
|NTMSAPI.DLL|ODBC32.DLL|ODBCBCP.DLL|OLE32.DLL|
|OLEACC.DLL|OLEAUT32.DLL|OLEDLG.DLL|OPENGL32.DLL|
|PDH.DLL|POWRPROF.DLL|QOSNAME.DLL|ZAPYTANIE. BIBLIOTEKI DLL|
|RASAPI32.DLL|RASDLG.DLL|RASSAPI.DLL|RESUTILS. BIBLIOTEKI DLL|
|RICHED20.DLL|RPCNS4.DLL|RPCRT4.DLL|RTM.DLL|
|RTUTILS.DLL|SCARDDLG.DLL|SECUR32.DLL|SENSAPI.DLL|
|SETUPAPI.DLL|SFC.DLL|SHELL32.DLL|SHFOLDER.DLL|
|SHLWAPI.DLL|SISBKUP.DLL|SNMPAPI.DLL|SRCLIENT. BIBLIOTEKI DLL|
|STI.DLL|TAPI32.DLL|TRAFFIC.DLL|ADRES URL. BIBLIOTEKI DLL|
|URLMON. BIBLIOTEKI DLL|USER32.DLL|USERENV.DLL|USP10.DLL|
|UXTHEME. BIBLIOTEKI DLL|VDMDBG.DLL|WERSJA. BIBLIOTEKI DLL|WINFAX.DLL|
|WINHTTP.DLL|WININET. BIBLIOTEKI DLL|WINMM.DLL|WINSCARD.DLL|
|WINTRUST.DLL|WLDAP32.DLL|WOW32.DLL|WS2_32.DLL|
|WSNMP32.DLL|WSOCK32.DLL|WTSAPI32.DLL|XOLEHLP.DLL|

> [!NOTE]
>  Zachowywanie ostatni błąd nie jest obsługiwana dla niezarządzanych funkcji, które są używane przez kod CLR, w tym samym module.

- Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](clr-common-language-runtime-compilation.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje w **dodatkowe opcje** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="example"></a>Przykład

Poniższy przykład definiuje natywnej biblioteki DLL za pomocą jednego eksportowanych funkcji, która modyfikuje ostatniego błędu.

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

Poniższy przykład wykorzystuje bibliotekę DLL, pokazuje sposób użycia studia **/CLRSUPPORTLASTERROR**.

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

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
