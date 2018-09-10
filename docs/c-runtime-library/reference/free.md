---
title: bezpłatne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- free
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
- free
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, deallocating
- free function
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35a1ae1a27b08db14673b125ecbc2978fd4738a3
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100486"
---
# <a name="free"></a>free

Cofa alokację lub zwalnia blok pamięci.

## <a name="syntax"></a>Składnia

```C
void free(
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Poprzednio przydzielony blok pamięci, która będzie zwolniona.

## <a name="remarks"></a>Uwagi

**Bezpłatne** funkcja zwalnia blok pamięci (*memblock*) zostały uprzednio alokowane przez wywołanie **calloc**, **— funkcja malloc**, lub **realloc**. Liczba zwolnionych bajtów jest równa liczbie bajtów, jeśli blok został przydzielony (lub przydzielone w przypadku właściwości **realloc**). Jeśli *memblock* jest **o wartości NULL**, wskaźnik jest ignorowany i **bezpłatne** natychmiast powraca. Podjęto próbę bezpłatne nieprawidłowy wskaźnik (wskaźnik do bloku pamięci, która nie została przydzielona przez **calloc**, **— funkcja malloc**, lub **realloc**) może mieć wpływ na żądania alokacji kolejnych i powodować błędy.

W przypadku wystąpienia błędu w zwalnianie pamięci, **errno** została ustawiona za pomocą informacji z systemu operacyjnego od charakteru błędu. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Po zwolnieniu bloku pamięci, [_heapmin —](heapmin.md) minimalizuje ilość wolnej pamięci na stosie przez łączenie nieużywane regionów i zwalniania ich do systemu operacyjnego. Zwolnionej pamięci, która nie została wydana w systemie operacyjnym zostanie przywrócony do wolnej puli i jest dostępny do alokacji ponownie.

Gdy aplikacja jest połączona z wersji debugowania bibliotek uruchomieniowych C, **bezpłatne** jest rozpoznawana jako [_free_dbg —](free-dbg.md). Aby uzyskać więcej informacji na temat sposobu zarządzania stosem podczas debugowania, zobacz [sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

**bezpłatne** jest oznaczony jako `__declspec(noalias)`, co oznacza, że funkcja daje gwarancję niemodyfikowania zmiennych globalnych. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md).

Aby zwolnić pamięć przydzielana za pomocą [_malloca](malloca.md), użyj [_freea —](freea.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**free**|\<stdlib.h > i \<malloc.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [— funkcja malloc](malloc.md).

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[_alloca](alloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
[_freea](freea.md)<br/>
