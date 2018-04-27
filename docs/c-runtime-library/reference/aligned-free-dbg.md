---
title: _aligned_free_dbg — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _aligned_free_dbg function
- aligned_free_dbg function
ms.assetid: eb0cb3c8-0992-4db8-bac3-65f1b8311ca6
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: efbe33940a4dad3ddb3ce73809ae2dc31f6d05c6
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="alignedfreedbg"></a>_aligned_free_dbg

Zwalnia blok pamięci przydzielony przy [_aligned_malloc —](aligned-malloc.md) lub [_aligned_offset_malloc —](aligned-offset-malloc.md) (tylko debugowanie).

## <a name="syntax"></a>Składnia

```C
void _aligned_free_dbg(
   void *memblock
);
```

### <a name="parameters"></a>Parametry

*memblock* wskaźnik do bloku pamięci, który został zwrócony do [_aligned_malloc —](aligned-malloc.md) lub [_aligned_offset_malloc —](aligned-offset-malloc.md) funkcji.

## <a name="remarks"></a>Uwagi

**_Aligned_free_dbg —** funkcji jest wersja debugowania [_aligned_free —](aligned-free.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowana, każde wywołanie **_aligned_free_dbg —** zostanie zmniejszona do wywołania **_aligned_free —**. Zarówno **_aligned_free —** i **_aligned_free_dbg —** wolne blok pamięci w stosie podstawowej, ale **_aligned_free_dbg —** bierze pod uwagę funkcja debugowania: możliwość przechowywania zwolnionych bloki w połączonej listy sterty celu symulacji warunków braku pamięci.

**_aligned_free_dbg —** wykonuje sprawdzanie poprawności dla wszystkich określonych plików i lokalizacje bloku przed wykonaniem operacji wolne. Aplikacja nie powinien zapewniać te informacje. Gdy zostanie zwolniona blok pamięci, menedżera sterty debugowania automatycznie sprawdza spójność buforów po obu stronach części użytkownika i wystawia raportu o błędach, jeśli przeprowadzono zastępowanie. Jeśli **_crtdbg_delay_free_mem_df —** pola bitowego ze [_crtdbgflag —](../../c-runtime-library/crtdbgflag.md) flaga jest ustawiona, zwolnionych bloku jest wypełniony przypisanej wartości 0xDD, **_free_block —** zablokować typu i zachowane w stercie połączonej listy bloków pamięci.

W przypadku wystąpienia błędu w zwolnić pamięć, **errno** ustawiono informacje z systemu operacyjnego od charakteru błędu. Aby uzyskać więcej informacji, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Aby dowiedzieć się jak bloki pamięci są przydzielone, zainicjować i zarządzane w wersji podstawowej sterty debugowania, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Informacje o typach bloku alokacji i sposobu ich używania, zobacz [typów bloków w stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o różnicach między wywoływanie funkcji sterty standardowe i jego wersji do debugowania w kompilację debugowania aplikacji, zobacz [debugowania wersji z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_free_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
