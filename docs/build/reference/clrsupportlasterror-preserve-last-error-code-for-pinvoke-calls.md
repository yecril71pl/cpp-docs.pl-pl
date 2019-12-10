---
title: /CLRSUPPORTLASTERROR (Zachowaj kod ostatniego błędu dla wywołań PInvoke)
ms.date: 11/04/2016
f1_keywords:
- /CLRSUPPORTLASTERROR
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
ms.openlocfilehash: 64948d81759d415245e741bc6152d56bb35480d2
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988352"
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR (Zachowaj kod ostatniego błędu dla wywołań PInvoke)

**/CLRSUPPORTLASTERROR**, która jest domyślnie włączona, zachowuje ostatni kod błędu funkcji wywoływanych za pośrednictwem mechanizmu P/Invoke, który umożliwia wywoływanie natywnych funkcji w bibliotekach DLL, z kodu skompilowanego z **/CLR**.

## <a name="syntax"></a>Składnia

```
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}
```

## <a name="remarks"></a>Uwagi

Zachowanie ostatniego kodu błędu oznacza spadek wydajności.  Jeśli nie chcesz ponosić wpływu na wydajność, aby zachować kod ostatniego błędu, Połącz się z **/CLRSUPPORTLASTERROR: No**.

Możesz zminimalizować wpływ na wydajność przez łączenie z **/CLRSUPPORTLASTERROR: SYSTEMDLL**, która zachowuje tylko kod ostatniego błędu dla funkcji w bibliotekach DLL systemu.  Systemowa biblioteka DLL jest definiowana jako jeden z następujących:

|||||
|-|-|-|-|
|ACLUI.DLL|ACTIVEDS. BIBLIOTEKI DLL|ADPTIF.DLL|ADVAPI32.DLL|
|ASYCFILT.DLL|AUTHZ.DLL|AVICAP32.DLL|AVIFIL32.DLL|
|Typu. BIBLIOTECE|CLUSAPI.DLL|COMCTL32.DLL|COMDLG32.DLL|
|COMSVCS. BIBLIOTECE|CREDUI.DLL|CRYPT32.DLL|CRYPTNET. BIBLIOTECE|
|CRYPTUI.DLL|D3D8THK.DLL|DBGENG. BIBLIOTECE|DBGHELP. BIBLIOTECE|
|DCIMAN32.DLL|DNSAPI.DLL|DSPROP.DLL|DSUIEXT.DLL|
|GDI32.DLL|GLU32.DLL|Plik. BIBLIOTECE|ICM32.DLL|
|IMAGEHLP.DLL|IMM32.DLL|IPHLPAPI.DLL|IPROP.DLL|
|KERNEL32.DLL|KSUSER.DLL|LOADPERF.DLL|LZ32.DLL|
|MAPI32.DLL|MGMTAPI.DLL|MOBSYNC. BIBLIOTECE|MPR.DLL|
|MPRAPI.DLL|MQRT.DLL|MSACM32.DLL|MSCMS.DLL|
|MSI.DLL|MSIMG32.DLL|MSRATING. BIBLIOTECE|MSTASK.DLL|
|MSVFW32.DLL|MSWSOCK.DLL|MTXEX.DLL|NDDEAPI.DLL|
|NETAPI32.DLL|NPPTOOLS. BIBLIOTECE|NTDSAPI.DLL|NTDSBCLI. BIBLIOTECE|
|NTMSAPI.DLL|ODBC32.DLL|ODBCBCP.DLL|OLE32.DLL|
|OLEACC. BIBLIOTECE|OLEAUT32. BIBLIOTEKI DLL|OLEDLG.DLL|OPENGL32.DLL|
|PDH.DLL|POWRPROF.DLL|QOSNAME.DLL|Dotyczących. BIBLIOTECE|
|RASAPI32.DLL|RASDLG.DLL|RASSAPI.DLL|RESUTILS. BIBLIOTECE|
|RICHED20.DLL|RPCNS4.DLL|RPCRT4.DLL|RTM.DLL|
|RTUTILS. BIBLIOTECE|SCARDDLG.DLL|SECUR32.DLL|SENSAPI.DLL|
|SETUPAPI.DLL|SFC.DLL|SHELL32.DLL|SHFOLDER.DLL|
|SHLWAPI. BIBLIOTEKI DLL|SISBKUP.DLL|SNMPAPI.DLL|SRCLIENT. BIBLIOTECE|
|STI.DLL|TAPI32.DLL|TRAFFIC.DLL|Adres URL. BIBLIOTECE|
|Urlmon. BIBLIOTECE|USER32.DLL|USERENV. BIBLIOTEKI DLL|USP10.DLL|
|UXTHEME. BIBLIOTECE|VDMDBG.DLL|WERSJA. BIBLIOTEKI DLL|WINFAX. BIBLIOTECE|
|WINHTTP.DLL|Oprogramowanie. BIBLIOTECE|WINMM. BIBLIOTECE|WINSCARD.DLL|
|WINTRUST.DLL|WLDAP32.DLL|WOW32.DLL|WS2_32.DLL|
|WSNMP32.DLL|WSOCK32.DLL|WTSAPI32.DLL|XOLEHLP.DLL|

> [!NOTE]
>  Zachowanie ostatniego błędu nie jest obsługiwane dla niezarządzanych funkcji, które są używane przez kod CLR, w tym samym module.

- Aby uzyskać więcej informacji, zobacz [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](clr-common-language-runtime-compilation.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij folder **konsolidator** .

1. Kliknij stronę właściwości **wiersza polecenia** .

1. Wpisz opcję w polu **dodatkowe opcje** .

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="example"></a>Przykład

Poniższy przykład definiuje natywną bibliotekę DLL z jedną wyeksportowaną funkcją, która modyfikuje ostatni błąd.

```cpp
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

Poniższy przykład korzysta z biblioteki DLL, pokazując, jak używać **/CLRSUPPORTLASTERROR**.

```cpp
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

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
