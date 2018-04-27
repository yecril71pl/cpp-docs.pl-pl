---
title: _aligned_msize — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _aligned_msize
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
- _aligned_msize
- aligned_msize
dev_langs:
- C++
helpviewer_keywords:
- aligned_msize function
- _aligned_msize function
ms.assetid: 10995edc-2110-4212-9ca9-5e0220a464f4
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 89257778241f6873682258e2f611c8a556e08210
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="alignedmsize"></a>_aligned_msize

Zwraca rozmiar bloku pamięci przydzielić w stercie.

## <a name="syntax"></a>Składnia

```C
size_t _msize(
   void *memblock,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Wskaźnik do bloku pamięci.

*Wyrównanie*<br/>
Wartość wyrównania, która musi być całkowitą potęgą liczby 2.

*offset*<br/>
Przesunięcie alokacji pamięci, aby wymusić wyrównanie.

## <a name="return-value"></a>Wartość zwracana

Zwraca rozmiar (w bajtach) jako liczbę całkowitą bez znaku.

## <a name="remarks"></a>Uwagi

**_Aligned_msize —** funkcja zwraca rozmiar w bajtach blok pamięci przydzielonej przez wywołanie [_aligned_malloc —](aligned-malloc.md) lub [_aligned_realloc —](aligned-realloc.md). *Wyrównanie* i *przesunięcie* wartości musi być taka sama jak wartości przekazane do funkcji, która przydzielony blok.

Gdy aplikacja jest połączony z wersją debugowania biblioteki wykonawcze języka C, **_aligned_msize —** jest rozpoznawana jako [_aligned_msize_dbg](aligned-msize-dbg.md). Aby uzyskać więcej informacji dotyczących sposobu zarządzania infrastrukturą sterty podczas debugowania procesu, zobacz [sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

Ta funkcja weryfikuje jej parametr. Jeśli *memblock* jest wskaźnika o wartości null lub *wyrównanie* nie jest potęgą liczby 2, **_msize —** wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru ](../../c-runtime-library/parameter-validation.md). Jeśli ten błąd jest obsługiwane, funkcja ustawia **errno** do **einval —** i zwraca wartość -1.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_msize**|\<malloc.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
