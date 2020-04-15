---
title: free
ms.date: 4/2/2020
api_name:
- free
- _o_free
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
- free
helpviewer_keywords:
- memory blocks, deallocating
- free function
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
ms.openlocfilehash: eefbe957ce5057b5038f98bc8da8fb2f0bdd3d1c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345979"
---
# <a name="free"></a>free

Zwalnia lub zwalnia blok pamięci.

## <a name="syntax"></a>Składnia

```C
void free(
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*blok memblock*<br/>
Wcześniej przydzielony blok pamięci do uwolnienia.

## <a name="remarks"></a>Uwagi

**Funkcja wolna** rozdziela blokadę pamięci *(memblock),* który został wcześniej przydzielony przez wywołanie **calloc,** **malloc**lub **realloc**. Liczba zwolnionych bajtów jest równoważna liczbie bajtów żądanych podczas alokacji bloku (lub ponownego przydzielenia, w przypadku **ponownego przydzielenia).** Jeśli *memblock* ma **wartość NULL**, wskaźnik jest ignorowany i natychmiast zwraca **wolny.** Próba zwolnienia nieprawidłowego wskaźnika (wskaźnik do bloku pamięci, który nie został przydzielony przez **calloc,** **malloc**lub **realloc)** może mieć wpływ na kolejne żądania alokacji i powodować błędy.

Jeśli wystąpi błąd podczas zwalniania pamięci, **errno** jest ustawiany z informacjami z systemu operacyjnego na temat charakteru błędu. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Po zwolnieniu bloku pamięci [_heapmin](heapmin.md) minimalizuje ilość wolnej pamięci na stercie, scalając nieużywane regiony i zwalniając je z powrotem do systemu operacyjnego. Zwolniona pamięć, która nie jest zwalniana do systemu operacyjnego, jest przywracana do wolnej puli i jest ponownie dostępna do alokacji.

Gdy aplikacja jest połączona z wersją debugowania bibliotek w czasie wykonywania języka C, **free** jest rozpoznawany [na _free_dbg](free-dbg.md). Aby uzyskać więcej informacji na temat zarządzania stertą podczas procesu debugowania, zobacz [Sterta debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

**free** jest `__declspec(noalias)`oznaczony, co oznacza, że funkcja jest gwarantowana, aby nie modyfikować zmiennych globalnych. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md).

Aby zwolnić pamięć przydzieloną z [_malloca,](malloca.md)użyj [_freea](freea.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**Wolna**|\<> i \<malloc.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [malloc](malloc.md).

## <a name="see-also"></a>Zobacz też

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[_alloca](alloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
[_freea](freea.md)<br/>
