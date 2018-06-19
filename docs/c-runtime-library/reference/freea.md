---
title: _freea — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _freea function
- freea function
- memory deallocation
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ac01f965e159dae19bbbd748c1692058063a211
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403606"
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
Poprzednio przydzielony blok pamięci, które ma zostać zwolniony.

## <a name="return-value"></a>Wartość zwracana

Brak.

## <a name="remarks"></a>Uwagi

**_Freea —** funkcja zwalnia blok pamięci (*memblock*) wcześniej było przydzielone przez wywołanie do [_malloca —](malloca.md). **_freea —** sprawdza, czy pamięć została przydzielona na stercie lub stosu. Jeśli został przydzielony na stosie, **_freea —** nie działają. Jeśli został przydzielony na stosie, liczba zwolnionych bajtów jest odpowiednikiem liczbę bajtów, gdy został przydzielony blok. Jeśli *memblock* jest **NULL**, wskaźnik jest ignorowany i **_freea —** natychmiast zwraca. Próba zwolnienia nieprawidłowego wskaźnika (wskaźnik do bloku pamięci, który nie został przydzielony przez **_malloca —**) może wpłynąć na żądania alokacji kolejnych i spowodować błędy.

**_freea —** wywołania **wolnego** wewnętrznie, jeśli stwierdzi, że pamięć jest przydzielony na stosie. Stos jest określany przez znacznik czy pamięć jest na stercie umieszczane w pamięci pod adresem poprzedzającego alokacji pamięci.

W przypadku wystąpienia błędu w zwolnić pamięć, **errno** ustawiono informacje z systemu operacyjnego od charakteru błędu. Aby uzyskać więcej informacji, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Po zwolnieniu blok pamięci, [_heapmin —](heapmin.md) minimalizuje ilość wolnej pamięci na stercie łączenie nieużywane regionów, a ich zwolnienie do systemu operacyjnego. Zwolnionych pamięci, która nie jest zwalniany do systemu operacyjnego zostanie przywrócony do puli bezpłatnej i jest dostępne do alokacji ponownie.

Wywołanie **_freea —** musi towarzyszyć wszystkie wywołania **_malloca —**. Istnieje również błąd do wywołania **_freea —** dwukrotnie dla tej samej pamięci. Gdy aplikacja jest połączony z debugowania wersji biblioteki wykonawcze języka C, zwłaszcza w przypadku [_malloc_dbg —](malloc-dbg.md) funkcje włączone, definiując **_crtdbg_map_alloc —**, możliwe jest łatwiejsze w celu znalezienia brakujących lub Zduplikowany wywołań **_freea —**. Aby uzyskać więcej informacji dotyczących sposobu zarządzania infrastrukturą sterty podczas debugowania procesu, zobacz [sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

**_freea —** jest oznaczony jako `__declspec(noalias)`, co oznacza zagwarantowanie funkcji nie można modyfikować zmienne globalne. Aby uzyskać więcej informacji, zobacz [noalias](../../cpp/noalias.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|---------------------|
|**_freea**|\<stdlib.h > i \<malloc.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_malloca —](malloca.md).

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
[_malloca](malloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
