---
title: free
ms.date: 11/04/2016
api_name:
- free
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- free
helpviewer_keywords:
- memory blocks, deallocating
- free function
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
ms.openlocfilehash: 7e09bec7c83eae64064e3997f2e8d5632a47258a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956727"
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
Wcześniej przydzielono blok pamięci, który ma zostać zwolniony.

## <a name="remarks"></a>Uwagi

Funkcja **bezpłatna zwalnia** blok pamięci (*memblock*), który został wcześniej przydzielony przez wywołanie metody **calloc**, **malloc**lub **realloc**. Liczba bajtów zwolnionych jest równa liczbie bajtów żądanych, gdy blok został przydzielony (lub ponownie przydzielony w przypadku **przedziału**). Jeśli *memblock* ma **wartość null**, wskaźnik jest ignorowany **i natychmiast** zwraca wartość. Próba zwolnienia nieprawidłowego wskaźnika (wskaźnik do bloku pamięci, który nie został alokowany przez **calloc**, **malloc**lub **realloc**), może mieć wpływ na kolejne żądania alokacji i powoduje błędy.

Jeśli wystąpi błąd podczas zwalniania pamięci, **errno** jest ustawiany z informacjami z systemu operacyjnego w przypadku awarii. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Po zwolnieniu bloku pamięci [_heapmin](heapmin.md) minimalizuje ilość wolnej pamięci w stercie przez podzbiór nieużywanych regionów i zwolnienie ich z powrotem do systemu operacyjnego. Zwolniona pamięć, która nie została wydana w systemie operacyjnym, zostaje przywrócona do puli bezpłatna i ponownie dostępna do przydzielenia.

Gdy aplikacja jest połączona z wersją debugową bibliotek uruchomieniowych C, **bezpłatny** program jest rozpoznawany jako [_free_dbg](free-dbg.md). Aby uzyskać więcej informacji na temat sposobu zarządzania sterty podczas procesu debugowania, zobacz [sterta debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

wartość **Free** jest `__declspec(noalias)`oznaczona, co oznacza, że funkcja nie modyfikuje zmiennych globalnych. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md).

Aby zwolnić pamięć przydzieloną za pomocą [_malloca](malloca.md), użyj [_freea](freea.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**free**|\<STDLIB. h > i \<malloc. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład dla opcji [malloc](malloc.md).

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[_alloca](alloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
[_freea](freea.md)<br/>
