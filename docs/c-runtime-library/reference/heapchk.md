---
title: _heapchk
ms.date: 11/04/2016
apiname:
- _heapchk
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: bdc0137761664a668d6ef95d739f09501e8290e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331717"
---
# <a name="heapchk"></a>_heapchk

Przeprowadza sprawdzanie spójności na stosie.

## <a name="syntax"></a>Składnia

```C
int _heapchk( void );
```

## <a name="return-value"></a>Wartość zwracana

**_heapchk —** zwraca jedną z następujących stałych całkowitych manifestu w Malloc.h.

|Wartość zwracana|Warunek|
|-|-|
| **_HEAPBADBEGIN** | Informacje o nagłówku początkowy jest nieprawidłowy lub nie można odnaleźć. |
| **_HEAPBADNODE** | Znaleziono nieprawidłowy węzeł lub uszkodzenia sterty. |
| **_HEAPBADPTR** | Wskaźnik do sterty jest nieprawidłowy. |
| **_HEAPEMPTY** | Nie zainicjowano stosu. |
| **_HEAPOK** | Sterty wydaje się być zgodne. |

Ponadto, jeśli wystąpi błąd **_heapchk —** ustawia **errno** do **ENOSYS**.

## <a name="remarks"></a>Uwagi

**_Heapchk —** funkcja pomaga debugować problemy związane ze stertą, sprawdzanie spójności minimalny sterty. Jeśli system operacyjny nie obsługuje **_heapchk —**(na przykład Windows 98), funkcja zwraca **_heapok —** i ustawia **errno** do **ENOSYS**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_heapchk**|\<malloc.h>|\<errno.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../../c-runtime-library/heapadd.md)<br/>
[_heapmin](heapmin.md)<br/>
[_heapset](../../c-runtime-library/heapset.md)<br/>
[_heapwalk](heapwalk.md)<br/>
