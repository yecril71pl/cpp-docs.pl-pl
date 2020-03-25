---
title: _aligned_free_dbg
ms.date: 11/04/2016
api_name:
- _aligned_free_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _aligned_free_dbg
- aligned_free_dbg
helpviewer_keywords:
- _aligned_free_dbg function
- aligned_free_dbg function
ms.assetid: eb0cb3c8-0992-4db8-bac3-65f1b8311ca6
ms.openlocfilehash: 18c1a23d666070afaf1eff687c7d33b0240f0ac3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171284"
---
# <a name="_aligned_free_dbg"></a>_aligned_free_dbg

Zwalnia blok pamięci, który został przydzielony do [_aligned_malloc](aligned-malloc.md) lub [_aligned_offset_malloc](aligned-offset-malloc.md) (tylko debugowanie).

## <a name="syntax"></a>Składnia

```C
void _aligned_free_dbg(
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Wskaźnik do bloku pamięci, który został zwrócony do funkcji [_aligned_malloc](aligned-malloc.md) lub [_aligned_offset_malloc](aligned-offset-malloc.md) .

## <a name="remarks"></a>Uwagi

Funkcja **_aligned_free_dbg** jest wersją debugowania funkcji [_aligned_free](aligned-free.md) . Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, każde wywołanie **_aligned_free_dbg** zostanie zredukowane do wywołania `_aligned_free`. Zarówno `_aligned_free`, jak i **_aligned_free_dbg** Zwolnij blok pamięci w stercie podstawowej, ale **_aligned_free_dbg** obsługuje funkcję debugowania: możliwość utrzymywania zwolnionych bloków na połączonej liście sterty w celu symulowania warunków niedostatecznej ilości pamięci.

**_aligned_free_dbg** wykonuje sprawdzanie poprawności wszystkich określonych plików i lokalizacji blokowania przed wykonaniem operacji bezpłatnej. Aplikacja nie powinna podawać tych informacji. Gdy blok pamięci jest zwolniony, Menedżer sterty debugowania automatycznie sprawdza integralność buforów po obu stronach części użytkownika i wystawia raport o błędach, jeśli nastąpiło zastąpienie. Jeśli ustawiono _CRTDBG_DELAY_FREE_MEM_DF pole bitowe flagi [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) , zwolniony blok zostanie wypełniony wartością 0xDD, przypisanym typem bloku _FREE_BLOCK i przechowywanym na połączonej liście bloków pamięci sterty.

Jeśli wystąpi błąd podczas zwalniania pamięci, `errno` jest ustawiana z informacjami z systemu operacyjnego w przypadku awarii. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Aby uzyskać informacje o tym, jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania sterty podstawowej, zobacz [szczegóły sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o typach bloków alokacji i sposobach ich użycia, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o różnicach między wywołaniem standardowej funkcji sterty i jej wersji debugowania w kompilacji debugowania aplikacji, zobacz [debugowanie wersji funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_free_dbg**|\<CRTDBG. h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Procedury debugowania](../../c-runtime-library/debug-routines.md)
