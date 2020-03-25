---
title: __crtLCMapStringW
ms.date: 11/04/2016
api_name:
- __crtLCMapStringW
api_location:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __crtLCMapStringW
helpviewer_keywords:
- __crtLCMapStringW
ms.assetid: 45b4ac0e-438c-4fa3-b4d1-34195f4467d9
ms.openlocfilehash: f239d95c0dfd50f765b6f23d7874f01dce085054
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170998"
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
Identyfikator ustawień regionalnych. Ustawienia regionalne zapewniają kontekst mapowania ciągów lub generowania klucza sortowania. Aplikacja może użyć makra `MAKELCID`, aby utworzyć identyfikator ustawień regionalnych.

*dwMapFlags*<br/>
Typ transformacji, która ma być używana podczas mapowania ciągu lub generowania klucza sortowania.

*lpSrcStr*<br/>
Wskaźnik do ciągu źródłowego, który funkcja mapuje lub używa do generowania klucza sortowania. Przyjęto, że ten parametr jest ciągiem Unicode.

*cchSrc*<br/>
Rozmiar, w znakach, ciągu wskazywanego przez parametr `lpSrcStr`. Ta liczba może zawierać terminator o wartości null lub nie zawierać go.

`cchSrc` wartość-1 określa, że ciąg wskazywany przez `lpSrcStr` jest zakończony znakiem null. W takim przypadku, gdy ta funkcja jest używana w trybie mapowania ciągów, funkcja oblicza samą długość ciągu, a wartość null kończy zamapowanego ciągu zapisanego w `*lpDestStr`.

*lpDestStr*<br/>
Długi wskaźnik do buforu, do którego funkcja przechowuje zamapowany ciąg lub klucz sortowania.

*cchDest*<br/>
Rozmiar (w znakach) buforu wskazywanego przez `lpDestStr`.

## <a name="return-value"></a>Wartość zwracana

Jeśli wartość `cchDest` jest różna od zera, liczba znaków lub bajty, jeśli określono `LCMAP_SORTKEY`, zapisywana w buforze wskazuje na powodzenie. Ta liczba obejmuje pomieszczenie dla terminatora o wartości null.

Jeśli wartość `cchDest` wynosi zero, rozmiar buforu w znakach lub bajty, jeśli określono `LCMAP_SORTKEY`, wymagane do odebrania przetłumaczonego ciągu lub klucza sortowania wskazuje na powodzenie. Ten rozmiar obejmuje pomieszczenie dla terminatora o wartości null.

Zero wskazuje na błąd. Aby uzyskać rozszerzone informacje o błędzie, wywołaj funkcję `GetLastError`.

## <a name="remarks"></a>Uwagi

Jeśli `cchSrc` jest większa od zera, a `lpSrcStr` jest ciągiem zakończonym wartością null, `__crtLCMapStringW` ustawia `cchSrc` na długość ciągu. Następnie `__crtLCMapStringW` wywołuje funkcję `LCMapString` o szerokim ciągu (Unicode) z określonymi parametrami. Aby uzyskać więcej informacji na temat parametrów i wartości zwracanej przez tę funkcję, zobacz [LCMapString](/windows/win32/api/winnls/nf-winnls-lcmapstringw).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|__crtLCMapStringW|awint. h|
