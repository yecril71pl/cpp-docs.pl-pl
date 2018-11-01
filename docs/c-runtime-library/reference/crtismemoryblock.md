---
title: _CrtIsMemoryBlock
ms.date: 11/04/2016
apiname:
- _CrtIsMemoryBlock
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
- CrtlsMemoryBlock
- _CrtIsMemoryBlock
helpviewer_keywords:
- _CrtIsMemoryBlock function
- CrtIsMemoryBlock function
ms.assetid: f7cbbc60-3690-4da0-a07b-68fd7f250273
ms.openlocfilehash: c4a85ebeb45552c6f5355853de2a45766d6bc984
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555769"
---
# <a name="crtismemoryblock"></a>_CrtIsMemoryBlock

Sprawdza, czy blok pamięci określonej znajduje się w lokalnej sterty i czy ma ona identyfikator typu bloku sterty debugowania prawidłowy (tylko wersja debugowania).

## <a name="syntax"></a>Składnia

```C
int _CrtIsMemoryBlock(
   const void *userData,
   unsigned int size,
   long *requestNumber,
   char **filename,
   int *linenumber
);
```

### <a name="parameters"></a>Parametry

*danych użytkownika*<br/>
Wskaźnik na początku bloku pamięci, aby sprawdzić.

*Rozmiar*<br/>
Rozmiar określony blok (w bajtach).

*requestNumber*<br/>
Wskaźnik z liczbą alokacji bloku lub **NULL**.

*Nazwa pliku*<br/>
Wskaźnik na nazwę pliku źródłowego, który zażądał bloku lub **NULL**.

*numer wiersza*<br/>
Wskaźnik do numeru wiersza w pliku źródłowym lub **NULL**.

## <a name="return-value"></a>Wartość zwracana

**_Crtismemoryblock —** zwraca **TRUE** Jeśli blok pamięci określonej znajduje się w obrębie lokalnej sterty i ma identyfikator typu bloku sterty debugowania prawidłowy; w przeciwnym razie funkcja zwraca **FALSE**.

## <a name="remarks"></a>Uwagi

**_Crtismemoryblock —** funkcja sprawdza, czy blok pamięci określonej znajduje się w obrębie aplikacji lokalnej sterty i ma identyfikator typu nieprawidłowy blok. Tej funkcji można również uzyskać numerem porządkowym obiektu alokacji i numer nazwy/wiersza pliku źródłowego, w którym pierwotnie żądaną alokacji bloku pamięci. Przekazywanie non -**NULL** wartości *requestNumber*, *filename*, lub *linenumber* powoduje, że parametry **_ Crtismemoryblock —** Aby ustawić te parametry do wartości w nagłówku bloku pamięci debugowania, jeśli znajdzie bloku w lokalnej sterty. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_crtismemoryblock —** są usuwane podczas przetwarzania wstępnego.

Jeśli **_crtismemoryblock —** nie powiedzie się, zwraca **FALSE** i parametry wyjściowe są inicjowane na wartości domyślne: *requestNumber* i **numer wiersza**  są ustawione na 0 i *filename* ustawiono **NULL**.

Ponieważ ta funkcja zwraca **TRUE** lub **FALSE**, mogą być przekazywane do jednego z [_ASSERT](assert-asserte-assert-expr-macros.md) makra, aby utworzyć prosty błąd debugowania mechanizm obsługi. Poniższy przykład powoduje błąd potwierdzenia, jeśli określony adres nie znajduje się w obrębie lokalnej sterty:

```C
_ASSERTE( _CrtIsMemoryBlock( userData, size, &requestNumber,
          &filename, &linenumber ) );
```

Aby uzyskać więcej informacji o tym, jak **_crtismemoryblock —** mogą być używane z innych funkcji debugowania i makr, zobacz [makra dla raportowania](/visualstudio/debugger/macros-for-reporting). Aby dowiedzieć się jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania podstawowej sterty, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtIsMemoryBlock**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="example"></a>Przykład

Zobacz przykład [_crtisvalidheappointer —](crtisvalidheappointer.md) tematu.

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
