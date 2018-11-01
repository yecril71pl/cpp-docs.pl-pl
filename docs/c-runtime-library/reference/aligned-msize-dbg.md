---
title: _aligned_msize_dbg
ms.date: 11/04/2016
apiname:
- _aligned_msize_dbg
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
- _aligned_msize_dbg
helpviewer_keywords:
- _aligned_msize_dbg
ms.assetid: f1c44af0-3f66-4033-81d1-d71d3afecba0
ms.openlocfilehash: 054f7b88f93eef37a9a88fbb7895452f7c158716
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451301"
---
# <a name="alignedmsizedbg"></a>_aligned_msize_dbg

Zwraca rozmiar bloku pamięci przydzielony w stercie (tylko wersja debugowania).

## <a name="syntax"></a>Składnia

```C
size_t _aligned_msize_dbg(
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

*Wyrównanie* i *przesunięcie* wartości muszą być takie same jak wartość przekazana do funkcji, która przydzielona bloku.

**_aligned_msize_dbg** jest wersją debugowania [_aligned_msize —](aligned-msize.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, każde wywołanie **_aligned_msize_dbg** jest ograniczone do wywołania **_aligned_msize —**. Zarówno **_aligned_msize —** i **_aligned_msize_dbg** Oblicz rozmiar bloku pamięci w stosie podstawowym, ale **_aligned_msize_dbg** dodaje funkcję debugowania: obejmuje buforów po obu stronach pamięci część użytkownika bloku rozmiaru zwróconego.

Ta funkcja sprawdza poprawność swojego parametru. Jeśli *memblock* jest pustym wskaźnikiem lub *wyrównanie* nie jest potęgą liczby 2, **_msize —** wywołuje program obsługi nieprawidłowego parametru, zgodnie z opisem w [Walidacja parametru ](../../c-runtime-library/parameter-validation.md). Jeśli obsługiwany jest błąd, funkcja ustawia **errno** do **EINVAL** i zwraca wartość -1.

Aby dowiedzieć się jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania podstawowej sterty, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje dotyczące alokacji typów bloków i sposobu ich używania, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacji na temat różnic między wywołaniem funkcji sterty standard oraz jego wersję debugowania do kompilacji debugowanej aplikacji, zobacz [Debuguj wersje z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_msize_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="see-also"></a>Zobacz także

[Alokacja pamięci](../../c-runtime-library/memory-allocation.md)<br/>
