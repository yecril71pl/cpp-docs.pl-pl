---
title: _aligned_recalloc_dbg
ms.date: 11/04/2016
apiname:
- _aligned_recalloc_dbg
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
- _aligned_recalloc_dbg
- aligned_recalloc_dbg
helpviewer_keywords:
- aligned_recalloc_dbg function
- _aligned_recalloc_dbg function
ms.assetid: 55c3c27e-561c-4d6b-9bf9-1e34cc556e4b
ms.openlocfilehash: c0f0cacc5efa5e63cbe05b481f922b35742e3924
ms.sourcegitcommit: beeb77b2976e997debc55b1af35024cc62e62799
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/06/2018
ms.locfileid: "52977787"
---
# <a name="alignedrecallocdbg"></a>_aligned_recalloc_dbg

Zmienia rozmiar bloku pamięci, która została przydzielona za pomocą [_aligned_malloc](aligned-malloc.md) lub [_aligned_offset_malloc —](aligned-offset-malloc.md) i inicjuje pamięć na 0 (tylko wersja debugowania).

## <a name="syntax"></a>Składnia

```C
void * _aligned_recalloc_dbg(
   void * memblock,
   size_t num,
   size_t size,
   size_t alignment,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*memblock*<br/>
Wskaźnik bieżącego bloku pamięci.

*Numer*<br/>
Liczba elementów.

*Rozmiar*<br/>
Rozmiar w bajtach każdego elementu.

*Wyrównanie*<br/>
Wartość wyrównania, która musi być całkowitą potęgą liczby 2.

*Nazwa pliku*<br/>
Wskaźnik na nazwę pliku źródłowego, który zażądał operacji alokacji lub **NULL**.

*numer wiersza*<br/>
Numer wiersza w pliku źródłowym, gdzie zażądano operacji alokacji lub **NULL**.

## <a name="return-value"></a>Wartość zwracana

**_aligned_recalloc_dbg —** zwraca pusty wskaźnik do bloku pamięci ponownie przydzielane (i ewentualnie przenoszenia). Wartość zwracana jest **NULL** Jeśli rozmiar wynosi zero, a argument bufor nie jest **NULL**, lub jeśli nie jest za mało dostępnej pamięci, aby rozwinąć blok na dany rozmiar. W pierwszym przypadku oryginalnego bloku jest zwalniana. W drugim przypadku oryginalnego bloku jest bez zmian. Zwracana wartość wskazuje miejsce do magazynowania, który gwarantuje bycia odpowiednio wyrównaną do przechowywania dowolnego typu obiektu. Aby uzyskać wskaźnik do typu innego niż void, użyj typu rzutowanego na wartość zwracaną.

Jest to błąd, ponownego przydzielenia pamięci i zmienić wyrównanie bloku.

## <a name="remarks"></a>Uwagi

**_aligned_recalloc_dbg —** jest wersją debugowania [_aligned_recalloc —](aligned-recalloc.md) funkcji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, każde wywołanie **_aligned_recalloc_dbg —** jest ograniczone do wywołania **_aligned_recalloc —**. Zarówno **_aligned_recalloc —** i **_aligned_recalloc_dbg —** ponownie przydzielić blok pamięci na stosie podstawowym, ale **_aligned_recalloc_dbg —** obsługuje kilka debugowania funkcje: buforów po obu stronach części bloku do testowania przecieków, użytkownika i *filename*/*linenumber* informacji do ustalenia źródła pochodzenia alokacji żądania. Śledzenie określonych typów alokacji z parametrem typu blok nie jest obsługiwane debugowania funkcji alokacji wyrównane. Alokacje wyrównany pojawi się jako typ _normal_block — blok.

**_aligned_recalloc_dbg —** przydzieli blok określonego pamięci z nieco większą ilością miejsca niż żądany rozmiar (*numer* * *rozmiar*) który może być większa lub mniejsza niż rozmiar bloku pamięci pierwotnie przydzielone. Dodatkowe miejsce jest używane przez menedżera stosu debugowania, do łączenia bloków pamięci debugowania i do dostarczenia aplikacji informacji nagłówka debugowania i zastąpienia buforów. Ponownej alokacji może spowodować przeniesienie oryginalnego bloku pamięci do innej lokalizacji w stercie, a także zmiana rozmiaru bloku pamięci. Część użytkownika bloku jest wypełniany wypełniania wartościami 0xcd a zastąpienia jest wypełniany wartościami 0xFD.

**_aligned_recalloc_dbg —** ustawia **errno** do **ENOMEM** Jeśli alokacja pamięci nie powiodło się; **EINVAL** jest zwracany, jeśli ilość pamięci potrzebnej (w tym obciążenie, o których wspomniano) przekracza **_heap_maxreq —**. Aby uzyskać informacji na temat tego i innych kodów błędu, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Ponadto **_aligned_recalloc_dbg —** sprawdza poprawność parametrów. Jeśli *wyrównanie* nie jest potęgą 2, funkcja wywoła procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca **NULL** i ustawia **errno** do **EINVAL**.

Aby dowiedzieć się jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania podstawowej sterty, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacje dotyczące alokacji typów bloków i sposobu ich używania, zobacz [typy bloków na stercie debugowania](/visualstudio/debugger/crt-debug-heap-details). Aby uzyskać informacji na temat różnic między wywołaniem funkcji sterty standard oraz jego wersję debugowania do kompilacji debugowanej aplikacji, zobacz [Debuguj wersje z funkcji alokacji sterty](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_aligned_recalloc_dbg**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
