---
title: Funkcje wywołania zwrotnego używane przez MFC
ms.date: 11/04/2016
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
ms.openlocfilehash: 8d84f939795e768c6b1356dcd8dc291421aedfdc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371139"
---
# <a name="callback-functions-used-by-mfc"></a>Funkcje wywołania zwrotnego używane przez MFC

Trzy funkcje wywołania zwrotnego są wyświetlane w bibliotece klas programu Microsoft Foundation. Te funkcje wywołania zwrotnego są przekazywane do [CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects), [CDC::GrayString](../../mfc/reference/cdc-class.md#graystring)i [CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc). Należy zauważyć, że wszystkie funkcje wywołania zwrotnego musi pułapka wyjątków MFC przed zwróceniem do systemu Windows, ponieważ wyjątki nie mogą być generowane przez granice wywołania zwrotnego. Aby uzyskać więcej informacji na temat wyjątków, zobacz artykuł [Wyjątki](../../mfc/exception-handling-in-mfc.md).

|Nazwa||
|----------|-----------------|
|[Funkcja wywołania zwrotnego dla CDC::EnumObjects](#enum_objects)||
|[Funkcja wywołania zwrotnego dla CDC::GrayString](#graystring)||
|[Funkcja wywołania zwrotnego dla CDC::SetAbortProc](#setabortproc)||

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="callback-function-for-cdcenumobjects"></a><a name="enum_objects"></a>Funkcja wywołania zwrotnego dla CDC::EnumObjects

*Nazwa ObjectFunc* jest symbolem zastępczym dla nazwy funkcji dostarczonej przez aplikację.

### <a name="syntax"></a>Składnia

```
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,
    LPSTR* lpData);
```

### <a name="parameters"></a>Parametry

*lpszLogObject*<br/>
Wskazuje strukturę danych [LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen) lub [LOGBRUSH,](/windows/win32/api/wingdi/ns-wingdi-logbrush) która zawiera informacje o atrybutach logicznych obiektu.

*lpData*<br/>
Wskazuje dane dostarczone przez aplikację `EnumObjects` przekazane do funkcji.

### <a name="return-value"></a>Wartość zwracana

Funkcja wywołania zwrotnego zwraca **int**. Wartość tego zwrotu jest zdefiniowana przez użytkownika. Jeśli funkcja wywołania zwrotnego `EnumObjects` zwraca 0, zatrzymuje wyliczenie wcześnie.

### <a name="remarks"></a>Uwagi

Rzeczywista nazwa musi zostać wyeksportowana.

## <a name="callback-function-for-cdcgraystring"></a><a name="graystring"></a>Funkcja wywołania zwrotnego dla CDC::GrayString

*OutputFunc* jest symbolem zastępczym dla nazwy funkcji wywołania zwrotnego dostarczonej przez aplikację.

### <a name="syntax"></a>Składnia

```
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,
    LPARAM lpData,
    int nCount);
```

### <a name="parameters"></a>Parametry

*Hdc*<br/>
Identyfikuje kontekst urządzenia pamięci z bitmapą o co najmniej `nWidth` `nHeight` szerokości `GrayString`i wysokości określonej przez i do .

*lpData*<br/>
Wskazuje ciąg znaków do rysowania.

*Ncount*<br/>
Określa liczbę znaków do wysuwu.

### <a name="return-value"></a>Wartość zwracana

Wartość zwracana funkcji wywołania zwrotnego musi być wartość TRUE, aby wskazać sukces; w przeciwnym razie jest false.

### <a name="remarks"></a>Uwagi

Funkcja wywołania zwrotnego (*OutputFunc*) musi narysować obraz względem współrzędnych (0,0), a nie *(x*, *y*).

## <a name="callback-function-for-cdcsetabortproc"></a><a name="setabortproc"></a>Funkcja wywołania zwrotnego dla CDC::SetAbortProc

Nazwa *AbortFunc* jest symbolem zastępczym dla nazwy funkcji dostarczonej przez aplikację.

### <a name="syntax"></a>Składnia

```
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,
    int code);
```

### <a name="parameters"></a>Parametry

*Hpr*<br/>
Identyfikuje kontekst urządzenia.

*Kod*<br/>
Określa, czy wystąpił błąd. Jest 0, jeśli nie wystąpił błąd. Jest SP_OUTOFDISK, jeśli Menedżer wydruku jest obecnie zamasz na dysku i więcej miejsca na dysku będzie dostępne, jeśli aplikacja czeka. Jeśli *kod* jest SP_OUTOFDISK, aplikacja nie musi przerywać zadania drukowania. Jeśli tak nie jest, musi ustąpić Menedżerowi `PeekMessage` `GetMessage` wydruku, wywołując funkcję lub system Windows.

### <a name="return-value"></a>Wartość zwracana

Zwracana wartość funkcji obsługi przerwania jest niezerowa, jeśli zadanie drukowania ma być kontynuowana, i 0, jeśli zostanie anulowana.

### <a name="remarks"></a>Uwagi

Rzeczywista nazwa musi być eksportowana zgodnie z opisem w sekcji Uwagi [CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc).

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects)<br/>
[CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)<br/>
[CDC::GrayString](../../mfc/reference/cdc-class.md#graystring)
