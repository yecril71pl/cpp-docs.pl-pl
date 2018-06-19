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
ms.openlocfilehash: fc6dfd832d18dbabc1ebc10aec252cc8afe15346
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402520"
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

*memblock* poprzednio przydzielony blok pamięci, które ma zostać zwolniony.

## <a name="remarks"></a>Uwagi

**Wolnego** funkcja zwalnia blok pamięci (*memblock*) wcześniej było przydzielone przez wywołanie do **calloc —**, **— funkcja malloc**, lub **realloc**. Liczba bajtów, gdy został przydzielony blok odpowiada liczba zwolnionych bajtów (lub przydzielone w odniesieniu **realloc**). Jeśli *memblock* jest **NULL**, wskaźnik jest ignorowany i **wolnego** natychmiast zwraca. Próba zwolnienia nieprawidłowego wskaźnika (wskaźnik do bloku pamięci, który nie został przydzielony przez **calloc —**, **— funkcja malloc**, lub **realloc**) może mieć wpływ na kolejne alokacji żądań i spowodować błędy.

W przypadku wystąpienia błędu w zwolnić pamięć, **errno** ustawiono informacje z systemu operacyjnego od charakteru błędu. Aby uzyskać więcej informacji, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Po zwolnieniu blok pamięci, [_heapmin —](heapmin.md) minimalizuje ilość wolnej pamięci na stercie łączenie nieużywane regionów, a ich zwolnienie do systemu operacyjnego. Zwolnionych pamięci, która nie jest zwalniany do systemu operacyjnego zostanie przywrócony do puli bezpłatnej i jest dostępne do alokacji ponownie.

Gdy aplikacja jest połączony z wersją debugowania biblioteki wykonawcze języka C, **wolnego** jest rozpoznawana jako [_free_dbg —](free-dbg.md). Aby uzyskać więcej informacji dotyczących sposobu zarządzania infrastrukturą sterty podczas debugowania procesu, zobacz [sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

**bezpłatne** jest oznaczony jako `__declspec(noalias)`, co oznacza zagwarantowanie funkcji nie można modyfikować zmienne globalne. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md).

Aby zwolnić pamięć przydzielona z [_malloca —](malloca.md), użyj [_freea —](freea.md).

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
