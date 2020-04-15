---
title: _heapchk
ms.date: 4/2/2020
api_name:
- _heapchk
- _o__heapchk
api_location:
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _heapchk
- heapchk
helpviewer_keywords:
- debugging [CRT], heap-related problems
- consistency checking of heaps
- heapchk function
- heaps, checking consistency
- _heapchk function
ms.assetid: 859619a5-1e35-4f02-9e09-11d9fa266ec0
ms.openlocfilehash: 21c7f9e22728109676d3fc611405ccd43ac773f8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344059"
---
# <a name="_heapchk"></a>_heapchk

Uruchamia kontrole spójności na stercie.

## <a name="syntax"></a>Składnia

```C
int _heapchk( void );
```

## <a name="return-value"></a>Wartość zwracana

**_heapchk** zwraca jedną z następujących stałych manifestu liczby całkowitej zdefiniowanych w malloc.h.

|Wartość zwracana|Warunek|
|-|-|
| **_HEAPBADBEGIN** | Początkowe informacje nagłówka są złe lub nie można ich odnaleźć. |
| **_HEAPBADNODE** | Znaleziono uszkodzony węzeł lub sterty jest uszkodzony. |
| **_HEAPBADPTR** | Wskaźnik do sterty jest nieprawidłowy. |
| **_HEAPEMPTY** | Sterta nie została zainicjowana. |
| **_HEAPOK** | Heap wydaje się być spójne. |

Ponadto w przypadku wystąpienia błędu **_heapchk** ustawia **errno** na **ENOSYS**.

## <a name="remarks"></a>Uwagi

Funkcja **_heapchk** pomaga debugować problemy związane ze stertą, sprawdzając minimalną spójność sterty. Jeśli system operacyjny nie obsługuje **_heapchk**(na przykład Windows 98), funkcja zwraca **_HEAPOK** i ustawia **errno** na **ENOSYS**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_heapchk**|\<> malloc.h|\<> errno.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_heapchk.c
// This program checks the heap for
// consistency and prints an appropriate message.

#include <malloc.h>
#include <stdio.h>

int main( void )
{
   int  heapstatus;
   char *buffer;

   // Allocate and deallocate some memory
   if( (buffer = (char *)malloc( 100 )) != NULL )
      free( buffer );

   // Check heap status
   heapstatus = _heapchk();
   switch( heapstatus )
   {
   case _HEAPOK:
      printf(" OK - heap is fine\n" );
      break;
   case _HEAPEMPTY:
      printf(" OK - heap is empty\n" );
      break;
   case _HEAPBADBEGIN:
      printf( "ERROR - bad start of heap\n" );
      break;
   case _HEAPBADNODE:
      printf( "ERROR - bad node in heap\n" );
      break;
   }
}
```

```Output
OK - heap is fine
```

## <a name="see-also"></a>Zobacz też

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../../c-runtime-library/heapadd.md)<br/>
[_heapmin](heapmin.md)<br/>
[_heapset](../../c-runtime-library/heapset.md)<br/>
[_heapwalk](heapwalk.md)<br/>
