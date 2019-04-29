---
title: _aligned_free_dbg
ms.date: 11/04/2016
apiname:
- _aligned_free_dbg
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
- _aligned_free_dbg
- aligned_free_dbg
helpviewer_keywords:
- _aligned_free_dbg function
- aligned_free_dbg function
ms.assetid: eb0cb3c8-0992-4db8-bac3-65f1b8311ca6
ms.openlocfilehash: f51b9b9573ab2e23a0a60979c55a33d2e5cff747
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341902"
---
# <a name="alignedfreedbg"></a>_aligned_free_dbg

Zwalnia blok pamięci, która została przydzielona za pomocą [_aligned_malloc](aligned-malloc.md) lub [_aligned_offset_malloc —](aligned-offset-malloc.md) (tylko debugowanie).

## <a name="syntax"></a>Składnia

```C
void _aligned_free_dbg(
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Wskaźnik do bloku pamięci, który został zwrócony do [_aligned_malloc](aligned-malloc.md) lub [_aligned_offset_malloc —](aligned-offset-malloc.md) funkcji.

## <a name="remarks"></a>Uwagi

**_Aligned_free_dbg —** funkcja jest wersją debugowania [_aligned_free —](aligned-free.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, każde wywołanie **_aligned_free_dbg —** jest ograniczone do wywołania `_aligned_free`. Zarówno `_aligned_free` i **_aligned_free_dbg —** zwolnieniu bloku pamięci w stosie podstawowym, ale **_aligned_free_dbg —** obsługuje funkcję debugowania: możliwość zachowania zwolnionych bloków w stosie połączonej listy Symulowanie warunków małej ilości pamięci.

**_aligned_free_dbg —** wykonuje sprawdzanie poprawności dla wszystkich określonych plików i lokalizacje bloku przed wykonaniem tej operacji bezpłatne. Nie oczekiwano aplikacji może przekazać tę informację. Gdy blok pamięci jest zwalniana, Menedżer stosu debugowania automatycznie sprawdza spójność buforów po obu stronach części użytkownika i generuje raport o błędach, jeżeli zastąpienie wystąpiło. Jeśli _CRTDBG_DELAY_FREE_MEM_DF bit pole [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) flaga jest ustawiona, wypełnione wartością 0xDD, przypisywany jest typ bloku _FREE_BLOCK i trzymane w połączonej liście stosu bloków pamięci zwolnione bloku.

Jeśli wystąpi błąd w pamięci, zwalniając `errno` została ustawiona za pomocą informacji z systemu operacyjnego od charakteru błędu. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Aby dowiedzieć się jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania podstawowej sterty, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje dotyczące alokacji typów bloków i sposobu ich używania, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacji na temat różnic między wywołaniem funkcji sterty standard oraz jego wersję debugowania do kompilacji debugowanej aplikacji, zobacz [Debuguj wersje z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_free_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)