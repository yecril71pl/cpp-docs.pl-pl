---
title: /CLRSUPPORTLASTERROR (Zachowaj kod ostatniego błędu dla wywołań PInvoke)
ms.date: 11/04/2016
f1_keywords:
- /CLRSUPPORTLASTERROR
helpviewer_keywords:
- /CLRSUPPORTLASTERROR linker option
- -CLRSUPPORTLASTERROR linker option
ms.assetid: b7057990-4154-4b1d-9fc9-6236f7be7575
ms.openlocfilehash: 19930591c2d0406c68b1a408622a49c9e8b1d551
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322274"
---
# <a name="clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls"></a>/CLRSUPPORTLASTERROR (Zachowaj kod ostatniego błędu dla wywołań PInvoke)

**/CLRSUPPORTLASTERROR**, który jest domyślnie włączony, zachowuje ostatni kod błędu funkcji wywoływanych za pośrednictwem mechanizmu P/Invoke, który umożliwia wywoływanie funkcji natywnych w DLLS, z kodu skompilowanego z **/clr**.

## <a name="syntax"></a>Składnia

```
/CLRSUPPORTLASTERROR{:NO | SYSTEMDLL}
```

## <a name="remarks"></a>Uwagi

Zachowanie ostatniego kodu błędu oznacza spadek wydajności.  Jeśli nie chcesz ponosić wpływu zachowania ostatniego kodu błędu na wydajność, łącze **z /CLRSUPPORTLASTERROR:NO**.

Wpływ na wydajność można zminimalizować, łącząc się z **/CLRSUPPORTLASTERROR:SYSTEMDLL**, który zachowuje tylko ostatni kod błędu dla funkcji w bibliotekach DLL systemu.  Biblioteka DLL systemu jest zdefiniowana jako jedna z następujących opcji:

|||||
|-|-|-|-|
|ACLUI. Dll|ACTIVEDS. BIBLIOTEKI DLL|ADPTIF. Dll|ADVAPI32. BIBLIOTEKI DLL|
|ASYCFILT. Dll|AUTHZ. Dll|AVICAP32. Dll|AVIFIL32. Dll|
|Szafka. Dll|CLUSAPI. Dll|COMCTL32. Dll|COMDLG32. Dll|
|COMSVCS. Dll|CREDUI. Dll|CRYPT32. Dll|CRYPTNET. Dll|
|CRYPTUI. Dll|D3D8THK. Dll|DBGENG. Dll|DBGHELP. Dll|
|DCIMAN32. Dll|DNSAPI. Dll|DSPROP. Dll|DSUIEXT. Dll|
|GDI32. Dll|GLU32. Dll|HLINK. Dll|ICM32. Dll|
|IMAGEHLP. Dll|IMM32. Dll|IPHLPAPI. BIBLIOTEKI DLL|IPROP. Dll|
|KERNEL32. BIBLIOTEKI DLL|KSUSER. Dll|LOADPERF. Dll|LZ32. Dll|
|MAPI32. Dll|MGMTAPI. Dll|MOBSYNC. Dll|MPR. BIBLIOTEKI DLL|
|MPRAPI. Dll|MQRT. Dll|MSACM32. Dll|MSCMS. Dll|
|MSI. BIBLIOTEKI DLL|MSIMG32. Dll|MSRATING. Dll|MSTASK. Dll|
|MSVFW32. Dll|MSWSOCK. Dll|MTXEX. Dll|NDDEAPI. Dll|
|NETAPI32. BIBLIOTEKI DLL|NPPTOOLS. Dll|Ntdsapi. Dll|NTDSBCLI. Dll|
|NTMSAPI. Dll|ODBC32. Dll|ODBCBCP. Dll|OLE32. BIBLIOTEKI DLL|
|OLEACC. Dll|OLEAUT32. BIBLIOTEKI DLL|OLEDLG. Dll|OPENGL32. Dll|
|Pdh. Dll|PLIKU POWRPROF. BIBLIOTEKI DLL|QOSNAME. Dll|Kwerendy. Dll|
|RASAPI32. Dll|RASDLG. Dll|RASSAPI. Dll|RESUTILS. Dll|
|RICHED20. Dll|RPCNS4. Dll|RPCRT4. BIBLIOTEKI DLL|Rtm. Dll|
|RTUTILS. Dll|SCARDDLG. Dll|SECUR32. BIBLIOTEKI DLL|SENSAPI. Dll|
|SETUPAPI. BIBLIOTEKI DLL|Sfc. Dll|SHELL32. BIBLIOTEKI DLL|SHFOLDER. Dll|
|SHLWAPI. BIBLIOTEKI DLL|SISBKUP. Dll|SNMPAPI. Dll|SRCLIENT. Dll|
|Sti. Dll|TAPI32. Dll|Ruchu. Dll|Adres url. Dll|
|Urlmon. Dll|USER32. BIBLIOTEKI DLL|USERENV. BIBLIOTEKI DLL|USP10. Dll|
|Uxtheme. Dll|VDMDBG. Dll|WERSJA. BIBLIOTEKI DLL|Winfax. Dll|
|WINHTTP. Dll|Wininet. Dll|WINMM. Dll|karta WINSCARD. Dll|
|WINTRUST. Dll|WLDAP32. BIBLIOTEKI DLL|WOW32. Dll|WS2_32.DLL|
|WSNMP32. Dll|WSOCK32.DLL|WTSAPI32. BIBLIOTEKI DLL|XOLEHLP. Dll|

> [!NOTE]
> Zachowanie ostatniego błędu nie jest obsługiwane dla funkcji niezarządzanych, które są używane przez kod CLR, w tym samym module.

- Aby uzyskać więcej informacji, zobacz [/clr (Kompilacja środowiska wykonawczego języka wspólnego)](clr-common-language-runtime-compilation.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **Strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora języka C++ i właściwości kompilacji w programie Visual Studio.](../working-with-project-properties.md)

1. Kliknij folder **Linker.**

1. Kliknij stronę właściwości **Wiersz polecenia.**

1. Wpisz tę opcję w polu **Opcje dodatkowe.**

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="example"></a>Przykład

Poniższy przykład definiuje natywną bibliotekę DLL z jedną wyeksportowanymi funkcją, która modyfikuje ostatni błąd.

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

Poniższy przykład zużywa bibliotekę DLL, demonstrując sposób **używania pliku /CLRSUPPORTLASTERROR**.

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

## <a name="see-also"></a>Zobacz też

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
