---
title: _recalloc_dbg
ms.date: 11/04/2016
api_name:
- _recalloc_dbg
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
- recalloc_dbg
- _recalloc_dbg
helpviewer_keywords:
- _recalloc_dbg function
- recalloc_dbg function
ms.assetid: 43c3e9b2-be6d-4508-9b0f-3220c8a47ca3
ms.openlocfilehash: 6274e749b2c4e6f64c7c7f82f8764dcf5ba642fe
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949475"
---
# <a name="_recalloc_dbg"></a>_recalloc_dbg

Ponownie przydziela tablicę i inicjuje jej elementy na 0 (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
void *_recalloc_dbg(
   void *userData,
   size_t num,
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*userData*<br/>
Wskaźnik do wcześniej przydzielony blok pamięci.

*Liczba*<br/>
Żądana liczba bloków pamięci.

*zmienia*<br/>
Żądany rozmiar każdego bloku pamięci (w bajtach).

*BlockType*<br/>
Żądany typ bloku pamięci: **_CLIENT_BLOCK** lub **_NORMAL_BLOCK**.

Aby uzyskać informacje o typach bloków alokacji i sposobach ich użycia, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details).

*Nazwa pliku*<br/>
Wskaźnik na nazwę pliku źródłowego, który żądał operacji alokacji lub **ma wartość null**.

*LineNumber*<br/>
Numer wiersza w pliku źródłowym, w którym zażądano operacji alokacji lub **ma wartość null**.

Parametry *filename* i *LineNumber* są dostępne tylko wtedy, gdy **_recalloc_dbg** została wywołana jawnie lub została zdefiniowana stała preprocesora [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) .

## <a name="return-value"></a>Wartość zwracana

Po pomyślnym zakończeniu ta funkcja zwraca wskaźnik do części użytkownika ponownie przydzieloną pamięć, wywołuje nową funkcję obsługi lub zwraca **wartość null**. Pełny opis zachowania zwrotnego znajduje się w sekcji poniższe uwagi. Aby uzyskać więcej informacji o sposobie używania nowej funkcji obsługi, zobacz Funkcja [_recalloc](recalloc.md) .

## <a name="remarks"></a>Uwagi

**_recalloc_dbg** to wersja debugowania funkcji [_recalloc](recalloc.md) . Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, każde wywołanie **_recalloc_dbg** jest ograniczone do wywołania **_recalloc**. Zarówno **_recalloc** , jak i **_recalloc_dbg** ponownie przydzielają blok pamięci w stercie podstawowym, ale **_recalloc_dbg** obsługuje kilka funkcji debugowania: bufory po obu stronach części bloku, aby przetestować pod kątem wycieków, parametr typu bloku Aby śledzić określone typy alokacji i *Nazwa pliku*/*LineNumber* informacje w celu określenia pochodzenia żądań alokacji.

**_recalloc_dbg** ponownie przydziela określony blok pamięci o nieco większym rozmiarze niż żądany rozmiar (*rozmiar* *numeru* * ), który może być większy lub mniejszy od rozmiaru pierwotnie przydzielonego bloku pamięci. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Ponowna Alokacja może spowodować przeniesienie oryginalnego bloku pamięci do innej lokalizacji w stercie, a także zmianę rozmiaru bloku pamięci. Część użytkownika bloku jest wypełniana wartością 0xCD, a każdy z buforów zastąpień jest wypełniony 0xFD.

**_recalloc_dbg** ustawia **errno** na **ENOMEM** , jeśli alokacja pamięci nie powiedzie się; **EINVAL** jest zwracany, jeśli ilość wymaganej pamięci (łącznie z wyżej wymienionym obciążeniem) przekracza **_HEAP_MAXREQ**. Aby uzyskać informacje o tym i innych kodach błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Aby uzyskać informacje o tym, jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania sterty podstawowej, zobacz [szczegóły sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje o różnicach między wywołaniem standardowej funkcji sterty i jej wersji debugowania w kompilacji debugowania aplikacji, zobacz [debugowanie wersji funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_recalloc_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje wyłącznie [bibliotek uruchomieniowych C](../../c-runtime-library/crt-library-features.md) .

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
