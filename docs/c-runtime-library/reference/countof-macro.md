---
title: _countof — Makro
ms.date: 03/22/2018
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
apitype: DLLExport
f1_keywords:
- _countof
- countof
helpviewer_keywords:
- countof macro
- _countof macro
ms.assetid: 86198767-f7e5-4beb-898d-3cbbf60350a3
ms.openlocfilehash: 60b4350d6cf14a545de67de0bdaee70ee2099006
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536139"
---
# <a name="countof-macro"></a>_countof — Makro

Oblicza liczbę elementów w tablicy statycznie przydzielonych.

## <a name="syntax"></a>Składnia

```C
#define _countof(array) (sizeof(array) / sizeof(array[0]))
```

### <a name="parameters"></a>Parametry

*Tablica*<br/>
Nazwa tablicy.

## <a name="return-value"></a>Wartość zwracana

Liczba elementów w tablicy, wyrażone jako **size_t**.

## <a name="remarks"></a>Uwagi

**_countof** jest implementowany jako funkcyjne makro preprocesora. Wersja języka C++ ma dodatkowy szablon maszyny do wykrywania w czasie kompilacji, jeśli wskaźnik jest przekazywany zamiast statycznie zadeklarowanych tablicy.

Upewnij się, że *tablicy* jest faktycznie tablicy, nie wskaźnik. W języku C **_countof** daje błędne wyniki, jeśli *tablicy* jest wskaźnikiem. W języku C++ **_countof** nie zostanie skompilowany, jeśli *tablicy* jest wskaźnikiem.  Tablica jest przekazywany jako parametr do funkcji *decays ze wskaźnikiem*, co oznacza, że w obrębie funkcji, nie można użyć **_countof** Aby określić rozmiar tablicy.

## <a name="requirements"></a>Wymagania

|Macro|Wymagany nagłówek|
|-----------|---------------------|
|**_countof**|\<stdlib.h>|

## <a name="example"></a>Przykład

```cpp
// crt_countof.cpp
#define _UNICODE
#include <stdio.h>
#include <stdlib.h>
#include <tchar.h>

int main( void )
{
   _TCHAR arr[20], *p;
   printf( "sizeof(arr) = %zu bytes\n", sizeof(arr) );
   printf( "_countof(arr) = %zu elements\n", _countof(arr) );
   // In C++, the following line would generate a compile-time error:
   // printf( "%zu\n", _countof(p) ); // error C2784 (because p is a pointer)

   _tcscpy_s( arr, _countof(arr), _T("a string") );
   // unlike sizeof, _countof works here for both narrow- and wide-character strings
}
```

```Output
sizeof(arr) = 40 bytes
_countof(arr) = 20 elements
```

## <a name="see-also"></a>Zobacz także

[sizeof, operator](../../cpp/sizeof-operator.md)<br/>
