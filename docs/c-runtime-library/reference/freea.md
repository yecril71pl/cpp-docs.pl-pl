---
title: _freea
ms.date: 11/04/2016
apiname:
- _freea
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
- freea
- _freea
helpviewer_keywords:
- _freea function
- freea function
- memory deallocation
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
ms.openlocfilehash: ac9c5528755898b0de131bccf94185b501b0e720
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605897"
---
# <a name="freea"></a>_freea

Cofa alokację lub zwalnia blok pamięci.

## <a name="syntax"></a>Składnia

```C
void _freea(
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Poprzednio przydzielony blok pamięci, która będzie zwolniona.

## <a name="return-value"></a>Wartość zwracana

Brak.

## <a name="remarks"></a>Uwagi

**_Freea —** funkcja zwalnia blok pamięci (*memblock*) zostały uprzednio alokowane przez wywołanie [_malloca](malloca.md). **_freea —** kontroli w celu sprawdzenia, jeśli pamięć została przydzielona na stosie lub stosu. Jeśli została przydzielona na stosie, **_freea —** nic nie robi. Jeśli został przydzielony na stosie, liczba zwolnionych bajtów jest równoważna liczbie bajtów, jeśli blok został przydzielony. Jeśli *memblock* jest **NULL**, wskaźnik jest ignorowany i **_freea —** natychmiast powraca. Podjęto próbę bezpłatne nieprawidłowy wskaźnik (wskaźnik do bloku pamięci, która nie została przydzielona przez **_malloca**) mogą mieć wpływ na żądania alokacji kolejnych i powodować błędy.

**_freea —** wywołania **bezpłatne** wewnętrznie, jeśli wykryje, że pamięć jest alokowane na stosie. Czy jest pamięć na stosie lub stos jest określana przez znacznik umieszczone w pamięć pod adresem, bezpośrednio poprzedzających ilość przydzielonej pamięci.

W przypadku wystąpienia błędu w zwalnianie pamięci, **errno** została ustawiona za pomocą informacji z systemu operacyjnego od charakteru błędu. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Po zwolnieniu bloku pamięci, [_heapmin —](heapmin.md) minimalizuje ilość wolnej pamięci na stosie przez łączenie nieużywane regionów i zwalniania ich do systemu operacyjnego. Zwolnionej pamięci, która nie została wydana w systemie operacyjnym zostanie przywrócony do wolnej puli i jest dostępny do alokacji ponownie.

Wywołanie **_freea —** musi towarzyszyć wszystkie wywołania do **_malloca**. Warto również błędem jest wywołanie **_freea —** dwa razy na tej samej pamięci. Gdy aplikacja jest połączona z wersji debugowania bibliotek uruchomieniowych C, zwłaszcza w przypadku [_malloc_dbg](malloc-dbg.md) funkcje włączone, definiując **_CRTDBG_MAP_ALLOC**, łatwiej znaleźć brakujące lub zduplikowane wywołania **_freea —**. Aby uzyskać więcej informacji na temat sposobu zarządzania stosem podczas debugowania, zobacz [sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

**_freea —** jest oznaczony jako `__declspec(noalias)`, co oznacza, że funkcja daje gwarancję niemodyfikowania zmiennych globalnych. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_freea**|\<stdlib.h > i \<malloc.h >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_malloca](malloca.md).

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[_malloca](malloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
