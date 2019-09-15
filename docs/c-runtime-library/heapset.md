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
ms.openlocfilehash: 65b74798c4b3b513acea0b51ecc0cb7df98391c1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944307"
---
# <a name="_heapset"></a>_heapset

Sprawdza sterty pod kątem minimalnej spójności i ustawia bezpłatne wpisy na określoną wartość.

> [!IMPORTANT]
>  Ta funkcja jest przestarzała. Począwszy od programu Visual Studio 2015, nie jest on dostępny w CRT.

## <a name="syntax"></a>Składnia

```
int _heapset(
   unsigned int fill
);
```

#### <a name="parameters"></a>Parametry

*pełni*<br/>
Znak wypełnienia.

## <a name="return-value"></a>Wartość zwracana

`_heapset`zwraca jedną z następujących stałych w postaci manifestu Integer zdefiniowanej w pliku malloc. h.

|||
|-|-|
| `_HEAPBADBEGIN`  | Informacje o początkowym nagłówku są nieprawidłowe lub nie zostały odnalezione.  |
| `_HEAPBADNODE`  | Znaleziono uszkodzony stertę lub zły węzeł.  |
| `_HEAPEMPTY`  | Sterta nie została zainicjowana.  |
| `_HEAPOK`  | Sterta wydaje się być spójna.  |

Ponadto, jeśli wystąpi błąd, `_heapset` ustawia `errno` na `ENOSYS`.

## <a name="remarks"></a>Uwagi

`_heapset` Funkcja pokazuje wolne lokalizacje pamięci lub węzły, które zostały przypadkowo nadpisane.

`_heapset`sprawdza minimalną spójność sterty, a następnie ustawia każdy bajt bezpłatnych wpisów sterty na `fill` wartość. Ta znana wartość wskazuje, które lokalizacje pamięci sterty zawierają wolne węzły, które zawierają dane, które nie zostały celowo zapisywana w pamięci podręcznej. Jeśli `_heapset`system operacyjny nie obsługuje (na przykład Windows 98), funkcja zwraca `_HEAPOK` i ustawia `errno` jako `ENOSYS`.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|`_heapset`|\<malloc.h>|\<errno.h>|

Aby uzyskać więcej informacji o zgodności, zobacz temat [zgodność](../c-runtime-library/compatibility.md) we wprowadzeniu.

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

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../c-runtime-library/heapadd.md)<br/>
[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapmin](../c-runtime-library/reference/heapmin.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)
