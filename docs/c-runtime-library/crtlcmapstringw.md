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
ms.openlocfilehash: e79ac5d4072595ef1034a0483b9edc8eada916d8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500214"
---
# <a name="__crtlcmapstringw"></a>__crtLCMapStringW

Mapuje jeden ciąg znaków na inny, wykonując określoną transformację zależną od ustawień regionalnych. Ta funkcja może również służyć do generowania klucza sortowania dla ciągu wejściowego.

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
Identyfikator ustawień regionalnych. Ustawienia regionalne zapewniają kontekst mapowania ciągów lub generowania klucza sortowania. Aplikacja może użyć `MAKELCID` makra do utworzenia identyfikatora ustawień regionalnych.

*dwMapFlags*<br/>
Typ transformacji, która ma być używana podczas mapowania ciągu lub generowania klucza sortowania.

*lpSrcStr*<br/>
Wskaźnik do ciągu źródłowego, który funkcja mapuje lub używa do generowania klucza sortowania. Przyjęto, że ten parametr jest ciągiem Unicode.

*cchSrc*<br/>
Rozmiar ciągu wskazywanego przez `lpSrcStr` parametr w znakach. Ta liczba może zawierać terminator o wartości null lub nie zawierać go.

Wartość-1 określa, że ciąg wskazywany przez `lpSrcStr` jest zakończony znakiem null. `cchSrc` W takim przypadku, gdy ta funkcja jest używana w trybie mapowania ciągów, funkcja oblicza samą długość ciągu, a wartość null kończy zamapowanego ciągu przechowywanego w `*lpDestStr`.

*lpDestStr*<br/>
Długi wskaźnik do buforu, do którego funkcja przechowuje zamapowany ciąg lub klucz sortowania.

*cchDest*<br/>
Rozmiar (w znakach) buforu wskazywanego przez `lpDestStr`.

## <a name="return-value"></a>Wartość zwracana

Jeśli wartość `cchDest` jest różna od zera, liczba znaków lub bajty, jeśli `LCMAP_SORTKEY` jest określona, zapisywana w buforze wskazuje na powodzenie. Ta liczba obejmuje pomieszczenie dla terminatora o wartości null.

Jeśli wartość `cchDest` jest równa zero, rozmiar buforu w znakach lub bajty, jeśli `LCMAP_SORTKEY` jest określony, wymagane do odebrania przetłumaczonego ciągu lub klucza sortowania wskazuje na powodzenie. Ten rozmiar obejmuje pomieszczenie dla terminatora o wartości null.

Zero wskazuje na błąd. Aby uzyskać rozszerzone informacje o błędzie, wywołaj `GetLastError` funkcję.

## <a name="remarks"></a>Uwagi

Jeśli `cchSrc` jest większa od zera i `lpSrcStr` jest ciągiem zakończonym wartością null, `__crtLCMapStringW` ustawia `cchSrc` długość ciągu. Następnie `__crtLCMapStringW` wywołuje `LCMapString` funkcję szerokiego ciągu (Unicode) funkcji z określonymi parametrami. Aby uzyskać więcej informacji na temat parametrów i wartości zwracanej przez tę funkcję, zobacz [LCMapString](/windows/win32/api/winnls/nf-winnls-lcmapstringw).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|__crtLCMapStringW|awint. h|