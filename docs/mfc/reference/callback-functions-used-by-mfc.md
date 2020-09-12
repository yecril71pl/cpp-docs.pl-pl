---
title: Funkcje wywołania zwrotnego używane przez MFC
ms.date: 11/04/2016
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
ms.openlocfilehash: 553e87320828590c9e1e9204b54622f2f1ca6d80
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040889"
---
# <a name="callback-functions-used-by-mfc"></a>Funkcje wywołania zwrotnego używane przez MFC

W biblioteka MFC są wyświetlane trzy funkcje wywołania zwrotnego. Te funkcje wywołania zwrotnego są przesyłane do funkcji [przechwytywania:: EnumObjects](../../mfc/reference/cdc-class.md#enumobjects), [przechwytywania:: GrayString](../../mfc/reference/cdc-class.md#graystring)i [przechwytywania:: SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc). Należy pamiętać, że wszystkie funkcje wywołania zwrotnego muszą być przed powrotem w systemie Windows, ponieważ wyjątki nie mogą być zgłaszane przez granice wywołania zwrotnego. Aby uzyskać więcej informacji o wyjątkach, zobacz [wyjątki](../../mfc/exception-handling-in-mfc.md)w artykule.

[Funkcja wywołania zwrotnego dla funkcji przechwytywania:: EnumObjects](#enum_objects)\
[Funkcja wywołania zwrotnego dla funkcji przechwytywania:: GrayString](#graystring)\
[Funkcja wywołania zwrotnego dla CDC::SetAbortProc](#setabortproc)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

## <a name="callback-function-for-cdcenumobjects"></a><a name="enum_objects"></a> Funkcja wywołania zwrotnego dla funkcji przechwytywania:: EnumObjects

Nazwa *ObjectFunc* jest symbolem zastępczym dla nazwy funkcji dostarczonej przez aplikację.

### <a name="syntax"></a>Składnia

```
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,
    LPSTR* lpData);
```

### <a name="parameters"></a>Parametry

*lpszLogObject*<br/>
Wskazuje strukturę danych [LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen) lub [LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush) , która zawiera informacje o atrybutach logicznych obiektu.

*lpData*<br/>
Wskazuje dane dostarczone przez aplikację przekazane do `EnumObjects` funkcji.

### <a name="return-value"></a>Wartość zwracana

Funkcja wywołania zwrotnego zwraca wartość **`int`** . Wartość tego powrotu jest zdefiniowana przez użytkownika. Jeśli funkcja wywołania zwrotnego zwróci wartość 0, program `EnumObjects` przestaje wyliczać wcześniej.

### <a name="remarks"></a>Uwagi

Rzeczywista nazwa musi zostać wyeksportowana.

## <a name="callback-function-for-cdcgraystring"></a><a name="graystring"></a> Funkcja wywołania zwrotnego dla funkcji przechwytywania:: GrayString

*OutputFunc* jest symbolem zastępczym dla nazwy funkcji wywołania zwrotnego dostarczonej przez aplikację.

### <a name="syntax"></a>Składnia

```
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,
    LPARAM lpData,
    int nCount);
```

### <a name="parameters"></a>Parametry

*Używający HDC*<br/>
Identyfikuje kontekst urządzenia pamięci z mapą bitową o szerokości i wysokości określonej przez `nWidth` i `nHeight` do `GrayString` .

*lpData*<br/>
Wskazuje ciąg znaków do rysowania.

*nCount*<br/>
Określa liczbę znaków do wyprowadzenia.

### <a name="return-value"></a>Wartość zwracana

Zwracana wartość funkcji wywołania zwrotnego musi mieć wartość TRUE, aby wskazać powodzenie; w przeciwnym razie ma wartość FALSE.

### <a name="remarks"></a>Uwagi

Funkcja wywołania zwrotnego (*OutputFunc*) musi narysować obraz względem współrzędnych (0, 0), a nie (*x*, *y*).

## <a name="callback-function-for-cdcsetabortproc"></a><a name="setabortproc"></a> Funkcja wywołania zwrotnego dla funkcji przechwytywania:: SetAbortProc

Nazwa *AbortFunc* jest symbolem zastępczym dla nazwy funkcji dostarczonej przez aplikację.

### <a name="syntax"></a>Składnia

```
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,
    int code);
```

### <a name="parameters"></a>Parametry

*hPr*<br/>
Identyfikuje kontekst urządzenia.

*kodu*<br/>
Określa, czy wystąpił błąd. Wartość 0 oznacza, że nie wystąpił błąd. Jest SP_OUTOFDISK, jeśli Menedżer wydruku nie ma obecnie miejsca na dysku, a więcej miejsca na dysku stanie się dostępne, gdy aplikacja zostanie zaczeka. Jeśli *kod* jest SP_OUTOFDISK, aplikacja nie musi przerywać zadania drukowania. Jeśli tak nie jest, musi przekazać do Menedżera wydruku, wywołując `PeekMessage` `GetMessage` funkcję lub Windows.

### <a name="return-value"></a>Wartość zwracana

Wartość zwracana funkcji przerwania obsługi jest różna od zera, jeśli zadanie drukowania jest kontynuowane, a 0, jeśli zostało anulowane.

### <a name="remarks"></a>Uwagi

Rzeczywista nazwa musi zostać wyeksportowana zgodnie z opisem w sekcji spostrzeżenia w tabeli przestawnej [:: SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc).

## <a name="see-also"></a>Zobacz także

[Struktury, style, wywołania zwrotne i mapy komunikatów](structures-styles-callbacks-and-message-maps.md)<br/>
[Przechwytywanie zmian:: EnumObjects](../../mfc/reference/cdc-class.md#enumobjects)<br/>
[Przechwytywanie zmian:: SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)<br/>
[Przechwytywanie zmian:: GrayString](../../mfc/reference/cdc-class.md#graystring)
