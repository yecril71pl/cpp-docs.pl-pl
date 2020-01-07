---
title: _pgmptr, _wpgmptr
ms.date: 11/04/2016
f1_keywords:
- pgmptr
- _pgmptr
- wpgmptr
- _wpgmptr
helpviewer_keywords:
- wpgmptr function
- _wpgmptr function
- _pgmptr function
- pgmptr function
ms.assetid: 4d44b515-0eff-4136-8bc4-684195f218f5
ms.openlocfilehash: beff0401d0aa2aa21819e58618ef4c02795d4393
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300160"
---
# <a name="_pgmptr-_wpgmptr"></a>_pgmptr, _wpgmptr

Ścieżka pliku wykonywalnego. Przestarzałe Użyj [_get_pgmptr](../c-runtime-library/reference/get-pgmptr.md) i [_get_wpgmptr](../c-runtime-library/reference/get-wpgmptr.md).

## <a name="syntax"></a>Składnia

```
extern char *_pgmptr;
extern wchar_t *_wpgmptr;
```

## <a name="remarks"></a>Uwagi

Gdy program jest uruchamiany z interpretera poleceń (cmd. exe), `_pgmptr` zostanie automatycznie zainicjowany do pełnej ścieżki pliku wykonywalnego. Na przykład jeśli Hello. exe znajduje się w C:\BIN i C:\BIN znajduje się w ścieżce, `_pgmptr` jest ustawiona na C:\BIN\Hello.exe podczas wykonywania:

```
C> hello
```

Gdy program nie jest uruchamiany z wiersza polecenia, `_pgmptr` może zostać zainicjowany do nazwy programu (nazwa podstawowa pliku bez rozszerzenia nazwy pliku) lub do nazwy pliku, ścieżki względnej lub pełnej ścieżki.

`_wpgmptr` jest znakiem dwubajtowym `_pgmptr` do użycia z programami, które używają `wmain`.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|

## <a name="requirements"></a>Wymagania

|Zmienna|Wymagany nagłówek|
|--------------|---------------------|
|`_pgmptr`, `_wpgmptr`|\<stdlib.h>|

## <a name="example"></a>Przykład

Poniższy program ilustruje użycie `_pgmptr`.

```c
// crt_pgmptr.c
// compile with: /W3
// The following program demonstrates the use of _pgmptr.
//
#include <stdio.h>
#include <stdlib.h>
int main( void )
{
   printf("The full path of the executing program is : %Fs\n",
     _pgmptr); // C4996
   // Note: _pgmptr is deprecated; use _get_pgmptr instead
}
```

`_wpgmptr` można użyć, zmieniając `%Fs` `%S` i `main` na `wmain`.

## <a name="see-also"></a>Zobacz także

[Zmienne globalne](../c-runtime-library/global-variables.md)
