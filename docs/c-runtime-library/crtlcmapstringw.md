---
title: __crtLCMapStringW
ms.date: 11/04/2016
apiname:
- __crtLCMapStringW
apilocation:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- __crtLCMapStringW
helpviewer_keywords:
- __crtLCMapStringW
ms.assetid: 45b4ac0e-438c-4fa3-b4d1-34195f4467d9
ms.openlocfilehash: 0c3752baba05e18903c32919505d702081d09dca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468422"
---
# <a name="crtlcmapstringw"></a>__crtLCMapStringW

Mapuje jeden ciąg znaków do innego, wykonując określone przekształcenie zależne od ustawień regionalnych. Tej funkcji można również wygenerować klucz sortowania dla ciągu wejściowego.

## <a name="syntax"></a>Składnia

```cpp
int __crtLCMapStringW(
   LCID    Locale,
   DWORD   dwMapFlags,
   LPCWSTR lpSrcStr,
   int     cchSrc,
   LPWSTR  lpDestStr,
   int     cchDest)
```

#### <a name="parameters"></a>Parametry

*Wersja regionalna*<br/>
Identyfikator ustawień regionalnych. Ustawienia regionalne dostarcza kontekst dla mapowania ciągu lub generowania klucza sortowania. Aplikacja może użyć `MAKELCID` makra, aby utworzyć identyfikator ustawień regionalnych.

*dwMapFlags*<br/>
Typ przekształcenia, które będą używane w ciągu mapowania lub Sortuj generowania klucza.

*lpSrcStr*<br/>
Wskaźnik do ciągu źródłowym, funkcja mapuje lub używa do generowania klucza sortowania. Ten parametr będzie traktowana jako ciąg Unicode.

*cchSrc*<br/>
Rozmiar, w postaci ciągu, wskazywana przez `lpSrcStr` parametru. Ten licznik można uwzględnić terminator o wartości null lub nie ma.

A `cchSrc` wartość -1, określa ciąg wskazywany przez `lpSrcStr` jest zakończony znakiem null. Jeśli jest to możliwe, a ta funkcja jest używany w trybie mapowania ciągów, funkcja oblicza długość ciągu, sama i wartość null kończy ciąg zamapowany, przechowywane w `*lpDestStr`.

*lpDestStr*<br/>
Długie wskaźnik do buforu, w którym funkcja przechowuje zamapowanego klucza ciągu lub sortowania.

*cchDest*<br/>
Rozmiar w znakach bufor wskazywany przez `lpDestStr`.

## <a name="return-value"></a>Wartość zwracana

Jeśli wartość `cchDest` jest różna od zera, liczba znaków, lub liczbę bajtów Jeśli `LCMAP_SORTKEY` jest określić, zapisywane w buforze oznacza sukces. Licznik ten uwzględnia również miejsce dla terminator o wartości null.

Jeśli wartość `cchDest` jest zero, rozmiaru buforu znaków lub liczbę bajtów Jeżeli `LCMAP_SORTKEY` jest określona, wymagane do odbierania przetłumaczonego ciągu lub Sortuj klucza oznacza sukces. Ten rozmiar obejmuje miejsce dla terminator o wartości null.

Wartość zero wskazuje błąd. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać `GetLastError` funkcji.

## <a name="remarks"></a>Uwagi

Jeśli `cchSrc` jest większa od zera i `lpSrcStr` jest ciąg zakończony znakiem null `__crtLCMapStringW` ustawia `cchSrc` do długości ciągu. Następnie `__crtLCMapStringW` wywołuje szerokiego ciągu (Unicode) wersję `LCMapString` funkcji z określonymi parametrami. Aby uzyskać więcej informacji na temat parametrów i wartość zwracana przez tę funkcję, zobacz [LCMapString](/windows/desktop/api/winnls/nf-winnls-lcmapstringa).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|__crtLCMapStringW|awint.h|