---
title: _heapset
ms.date: 11/04/2016
api_name:
- _heapset
api_location:
- msvcr90.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 2a0aea37237f04939579eb059a42dd33771339ad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351271"
---
# <a name="_heapset"></a>_heapset

Sprawdza sterty pod kątem minimalnej spójności i ustawia wolne wpisy na określoną wartość.

> [!IMPORTANT]
> Ta funkcja jest przestarzała. Począwszy od programu Visual Studio 2015, nie jest dostępna w CRT.

## <a name="syntax"></a>Składnia

```
int _heapset(
   unsigned int fill
);
```

#### <a name="parameters"></a>Parametry

*fill*<br/>
Znak wypełnienia.

## <a name="return-value"></a>Wartość zwracana

`_heapset`zwraca jedną z następujących stałych manifestu liczby całkowitej zdefiniowanych w malloc.h.

|||
|-|-|
| `_HEAPBADBEGIN`  | Początkowe informacje nagłówka nieprawidłowe lub nie znaleziono.  |
| `_HEAPBADNODE`  | Znaleziono uszkodzony lub uszkodzony węzeł.  |
| `_HEAPEMPTY`  | Sterty nie zainicjowane.  |
| `_HEAPOK`  | Heap wydaje się być spójne.  |

Ponadto w przypadku wystąpienia `_heapset` błędu `errno` `ENOSYS`ustawia się na .

## <a name="remarks"></a>Uwagi

Funkcja `_heapset` pokazuje lokalizacje wolnej pamięci lub węzły, które zostały przypadkowo zastąpione.

`_heapset`sprawdza minimalną spójność na stercie, a następnie ustawia każdy bajt `fill` wolnych wpisów sterty do wartości. Ta znana wartość pokazuje, które lokalizacje pamięci sterty zawierają wolne węzły i które zawierają dane, które zostały przypadkowo zapisane w zwolnionej pamięci. Jeśli system operacyjny nie `_heapset`obsługuje (na przykład Windows 98), `errno` `ENOSYS`funkcja zwraca `_HEAPOK` i ustawia na .

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|`_heapset`|\<> malloc.h|\<> errno.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../c-runtime-library/compatibility.md) we wstępie.

## <a name="example"></a>Przykład

```c
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
