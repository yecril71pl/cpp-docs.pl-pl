---
title: _heapset
ms.date: 11/04/2016
apiname:
- _heapset
apilocation:
- msvcr90.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _heapset
- heapset
helpviewer_keywords:
- checking heap
- heapset function
- heaps, checking
- debugging [CRT], heap-related problems
- _heapset function
ms.assetid: 9667eeb0-55bc-4c19-af5f-d1fd0a142b3c
ms.openlocfilehash: c93624b8b56fb53eb15263dbd0d203cd9130eacf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528196"
---
# <a name="heapset"></a>_heapset

Sprawdza sterty minimalny sprawdzania spójności i ustawia wolnych wpisów określoną wartość.

> [!IMPORTANT]
>  Ta funkcja jest przestarzała. Począwszy od programu Visual Studio 2015, nie jest dostępna w CRT.

## <a name="syntax"></a>Składnia

```
int _heapset(
   unsigned int fill
);
```

#### <a name="parameters"></a>Parametry

*Wypełnienie*<br/>
Wprowadź znak.

## <a name="return-value"></a>Wartość zwracana

`_heapset` Zwraca jedną z następujących stałych całkowitych manifestu w Malloc.h.

|||
|-|-|
| `_HEAPBADBEGIN`  | Informacje początkowego nagłówka nieprawidłowe lub nie został odnaleziony.  |
| `_HEAPBADNODE`  | Sterty uszkodzony lub zły węzeł, do których odnaleźć.  |
| `_HEAPEMPTY`  | Nie zainicjowano stosu.  |
| `_HEAPOK`  | Sterty wydaje się być zgodne.  |

Ponadto, jeśli wystąpi błąd `_heapset` ustawia `errno` do `ENOSYS`.

## <a name="remarks"></a>Uwagi

`_heapset` Funkcja wykazuje lokalizacje wolnej pamięci albo przez węzły, które zostały przypadkowo zastąpione.

`_heapset` sprawdza, czy minimalny spójności na stosie, a następnie ustawia poszczególne bajty sterty bezpłatne wpisów, aby `fill` wartość. Tej znanej wartości pokazuje lokalizacji, w których pamięci sterty zawiera węzły w warstwie bezpłatna i które zawierają dane, które przypadkowo polegają na zwolnionej pamięci. Jeśli system operacyjny nie obsługuje `_heapset`(na przykład Windows 98), funkcja zwraca `_HEAPOK` i ustawia `errno` do `ENOSYS`.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|`_heapset`|\<malloc.h>|\<errno.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../c-runtime-library/compatibility.md) we wstępie.

## <a name="example"></a>Przykład

```
// crt_heapset.c
// This program checks the heap and
// fills in free entries with the character 'Z'.

#include <malloc.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int heapstatus;
   char *buffer;

   if( (buffer = malloc( 1 )) == NULL ) // Make sure heap is
      exit( 0 );                        //    initialized
   heapstatus = _heapset( 'Z' );        // Fill in free entries
   switch( heapstatus )
   {
   case _HEAPOK:
      printf( "OK - heap is fine\n" );
      break;
   case _HEAPEMPTY:
      printf( "OK - heap is empty\n" );
      break;
   case _HEAPBADBEGIN:
      printf( "ERROR - bad start of heap\n" );
      break;
   case _HEAPBADNODE:
      printf( "ERROR - bad node in heap\n" );
      break;
   }
   free( buffer );
}
```

```Output
OK - heap is fine
```

## <a name="see-also"></a>Zobacz też

[Alokacja pamięci](../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../c-runtime-library/heapadd.md)<br/>
[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapmin](../c-runtime-library/reference/heapmin.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)