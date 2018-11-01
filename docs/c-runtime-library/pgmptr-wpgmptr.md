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
ms.openlocfilehash: c59134afc3b4d0f6360984c67dede28c27010bae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597538"
---
# <a name="pgmptr-wpgmptr"></a>_pgmptr, _wpgmptr

Ścieżka pliku wykonywalnego. Przestarzałe; Użyj [_get_pgmptr —](../c-runtime-library/reference/get-pgmptr.md) i [_get_wpgmptr —](../c-runtime-library/reference/get-wpgmptr.md).

## <a name="syntax"></a>Składnia

```
extern char *_pgmptr;
extern wchar_t *_wpgmptr;
```

## <a name="remarks"></a>Uwagi

Gdy program jest uruchamiany z interpreter poleceń (Cmd.exe), `_pgmptr` jest inicjowana automatycznie do pełnej ścieżki pliku wykonywalnego. Na przykład, jeśli Hello.exe C:\BIN i C:\BIN znajduje się w ścieżce, `_pgmptr` ustawiono C:\BIN\Hello.exe podczas wykonywania:

```
C> hello
```

Jeśli program nie zostanie uruchomiony z wiersza polecenia `_pgmptr` może być zainicjowana, nazwę programu (nazwa podstawowa dla pliku bez rozszerzenia nazwy pliku) lub nazwę pliku, ścieżka względna lub pełną ścieżkę.

`_wpgmptr` jest odpowiednikiem znaku dwubajtowego `_pgmptr` do użytku z programem programy używające `wmain`.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|

## <a name="requirements"></a>Wymagania

|Zmienna|Wymagany nagłówek|
|--------------|---------------------|
|`_pgmptr`, `_wpgmptr`|\<stdlib.h>|

## <a name="example"></a>Przykład

Następujący program pokazuje użycie `_pgmptr`.

```
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

Można użyć `_wpgmptr` , zmieniając `%Fs` do `%S` i `main` do `wmain`.

## <a name="see-also"></a>Zobacz też

[Zmienne globalne](../c-runtime-library/global-variables.md)