---
title: _getdrives
ms.date: 11/04/2016
apiname:
- _getdrives
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- getdrives
- _getdrives
helpviewer_keywords:
- _getdrives function
- getdrives function
- disk drives
ms.assetid: 869bb51f-4209-4328-846e-3aadebaceb9c
ms.openlocfilehash: 444a54a316b1b1e4cfd26df95d172c7e9748fb88
ms.sourcegitcommit: d441305fb19131afbd7fc259d8cda63ea26f2343
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2018
ms.locfileid: "51678317"
---
# <a name="getdrives"></a>_getdrives

Zwraca wartość maski bitów, który reprezentuje aktualnie dostępnych dysków.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
unsigned long _getdrives( void );
```

## <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest maską bitów, który reprezentuje aktualnie dostępnych dysków. Pozycja bitu 0 (najmniej znaczący bit) Określa dysk, A, bit pozycja 1 jest dysk B, pozycja bitu 2 jest dysk C i tak dalej. Jeśli funkcja zawiedzie, wartość zwracana wynosi zero. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać **GetLastError**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_getdrives**|\<direct.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_getdrives.c
// This program retrieves and lists out
// all the logical drives that are
// currently mounted on the machine.

#include <windows.h>
#include <direct.h>
#include <stdio.h>
#include <tchar.h>

TCHAR g_szDrvMsg[] = _T("A:\n");

int main(int argc, char* argv[]) {
   ULONG uDriveMask = _getdrives();

   if (uDriveMask == 0)
   {
      printf( "_getdrives() failed with failure code: %d\n",
              GetLastError());
   }
   else
   {
      printf("The following logical drives are being used:\n");

      while (uDriveMask) {
         if (uDriveMask & 1)
            printf(g_szDrvMsg);

         ++g_szDrvMsg[0];
         uDriveMask >>= 1;
      }
   }
}
```

```Output
The following logical drives are being used:
A:
C:
D:
E:
```

## <a name="see-also"></a>Zobacz także

[Kontrola katalogu](../../c-runtime-library/directory-control.md)<br/>
