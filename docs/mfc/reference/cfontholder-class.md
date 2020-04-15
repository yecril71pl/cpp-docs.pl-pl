---
title: Klasa CFontHolder
ms.date: 11/04/2016
f1_keywords:
- CFontHolder
- AFXCTL/CFontHolder
- AFXCTL/CFontHolder::CFontHolder
- AFXCTL/CFontHolder::GetDisplayString
- AFXCTL/CFontHolder::GetFontDispatch
- AFXCTL/CFontHolder::GetFontHandle
- AFXCTL/CFontHolder::InitializeFont
- AFXCTL/CFontHolder::QueryTextMetrics
- AFXCTL/CFontHolder::ReleaseFont
- AFXCTL/CFontHolder::Select
- AFXCTL/CFontHolder::SetFont
- AFXCTL/CFontHolder::m_pFont
helpviewer_keywords:
- CFontHolder [MFC], CFontHolder
- CFontHolder [MFC], GetDisplayString
- CFontHolder [MFC], GetFontDispatch
- CFontHolder [MFC], GetFontHandle
- CFontHolder [MFC], InitializeFont
- CFontHolder [MFC], QueryTextMetrics
- CFontHolder [MFC], ReleaseFont
- CFontHolder [MFC], Select
- CFontHolder [MFC], SetFont
- CFontHolder [MFC], m_pFont
ms.assetid: 728ab472-0c97-440d-889f-1324c6e1b6b8
ms.openlocfilehash: 6a053f127123a9ca21853189b9458738b217ee2b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373816"
---
# <a name="cfontholder-class"></a>Klasa CFontHolder

Implementuje właściwość font i hermetyzuje funkcjonalność obiektu czcionki `IFont` systemu Windows i interfejsu.

## <a name="syntax"></a>Składnia

```
class CFontHolder
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFontHolder::CFontHolder](#cfontholder)|Konstruuje `CFontHolder` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFontHolder::GetDisplayString](#getdisplaystring)|Pobiera ciąg wyświetlany w przeglądarce właściwości kontenera.|
|[CFontHolder::GetFontDispatch](#getfontdispatch)|Zwraca interfejs czcionki. `IDispatch`|
|[CFontHolder::GetFontHandle](#getfonthandle)|Zwraca uchwyt do czcionki systemu Windows.|
|[CFontHolder::InitializeFont](#initializefont)|Inicjuje `CFontHolder` obiekt.|
|[CFontHolder::QueryTextMetrics](#querytextmetrics)|Pobiera informacje dotyczące czcionki pokrewne.|
|[CFontHolder::ReleaseFont](#releasefont)|Odłącza `CFontHolder` obiekt `IFont` od `IFontNotification` i interfejsów.|
|[CFontHolder::Wybierz](#select)|Wybiera zasób czcionki w kontekście urządzenia.|
|[CFontHolder::SetFont](#setfont)|Łączy obiekt `CFontHolder` z `IFont` interfejsem.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CFontHolder::m_pFont](#m_pfont)|Wskaźnik do `CFontHolder` `IFont` interfejsu obiektu.|

## <a name="remarks"></a>Uwagi

`CFontHolder`nie ma klasy podstawowej.

Ta klasa służy do implementowania niestandardowych właściwości czcionek dla formantu. Aby uzyskać informacje na temat tworzenia takich właściwości, zobacz artykuł [ActiveX Formanty: Korzystanie z czcionek](../../mfc/mfc-activex-controls-using-fonts.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CFontHolder`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxctl.h

## <a name="cfontholdercfontholder"></a><a name="cfontholder"></a>CFontHolder::CFontHolder

Konstruuje `CFontHolder` obiekt.

```
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```

### <a name="parameters"></a>Parametry

*pNotyfikuj*<br/>
Wskaźnik do interfejsu `IPropertyNotifySink` czcionki.

### <a name="remarks"></a>Uwagi

Przed użyciem obiektu należy wywołać `InitializeFont` jego zainicjowanie.

## <a name="cfontholdergetdisplaystring"></a><a name="getdisplaystring"></a>CFontHolder::GetDisplayString

Pobiera ciąg, który może być wyświetlany w przeglądarce właściwości kontenera.

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>Parametry

*strValue (wartość)*<br/>
Odwołanie do [CString,](../../atl-mfc-shared/reference/cstringt-class.md) który ma pomieścić ciąg wyświetlania.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli ciąg zostanie pomyślnie pobrany; w przeciwnym razie 0.

## <a name="cfontholdergetfontdispatch"></a><a name="getfontdispatch"></a>CFontHolder::GetFontDispatch

Wywołanie tej funkcji, aby pobrać wskaźnik do interfejsu wysyłki czcionki.

```
LPFONTDISP GetFontDispatch();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CFontHolder` `IFontDisp` interfejsu obiektu. Należy zauważyć, że `GetFontDispatch` funkcja, która wywołuje musi wywołać `IUnknown::Release` ten wskaźnik interfejsu, gdy jest to zrobione z nim.

### <a name="remarks"></a>Uwagi

Zadzwoń `InitializeFont` przed `GetFontDispatch`wywołaniem .

## <a name="cfontholdergetfonthandle"></a><a name="getfonthandle"></a>CFontHolder::GetFontHandle

Wywołanie tej funkcji, aby uzyskać uchwyt do czcionki systemu Windows.

```
HFONT GetFontHandle();

HFONT GetFontHandle(
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>Parametry

*cylogical (cylogical)*<br/>
Wysokość, w jednostkach logicznych, prostokąta, w którym jest rysowana formant.

*cyHimetric (cyHimetric)*<br/>
Wysokość, w MM_HIMETRIC jednostkach, sterowania.

### <a name="return-value"></a>Wartość zwracana

Dojście do Font obiektu; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Stosunek *cyLogical* i *cyHimetric* służy do obliczania właściwego rozmiaru wyświetlania w jednostkach logicznych dla rozmiaru punktu czcionki wyrażonego w jednostkach MM_HIMETRIC:

Rozmiar wyświetlacza = ( *cyLogical* / *cyHimetric*) X rozmiar czcionki

Wersja bez parametrów zwraca uchwyt do czcionki o prawidłowym rozmiarze ekranu.

## <a name="cfontholderinitializefont"></a><a name="initializefont"></a>CFontHolder::InitializeFont

Inicjuje `CFontHolder` obiekt.

```
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,
    LPDISPATCH pFontDispAmbient = NULL);
```

### <a name="parameters"></a>Parametry

*pFontDesc ( pFontDesc )*<br/>
Wskaźnik do struktury opisu czcionki [(FONTDESC),](/windows/win32/api/olectl/ns-olectl-fontdesc)który określa właściwości czcionki.

*pFontDispAmbient*<br/>
Wskaźnik do otaczającej font kontenera właściwości.

### <a name="remarks"></a>Uwagi

Jeśli *pFontDispAmbient* nie jest `CFontHolder` null, obiekt jest połączony `IFont` z klonem interfejsu używanego przez właściwość Font otoczenia kontenera.

Jeśli *pFontDispAmbient* ma wartość NULL, nowy obiekt Font jest tworzony na podstawie opisu czcionki wskazanego przez *pFontDesc* lub, jeśli *pFontDesc* ma wartość NULL, z domyślnego opisu.

Wywołanie tej funkcji `CFontHolder` po skonstruowaniu obiektu.

## <a name="cfontholderm_pfont"></a><a name="m_pfont"></a>CFontHolder::m_pFont

Wskaźnik do `CFontHolder` `IFont` interfejsu obiektu.

```
LPFONT m_pFont;
```

## <a name="cfontholderquerytextmetrics"></a><a name="querytextmetrics"></a>CFontHolder::QueryTextMetrics

Pobiera informacje o fizycznej czcionce `CFontHolder` reprezentowanej przez obiekt.

```
void QueryTextMetrics(LPTEXTMETRIC lptm);
```

### <a name="parameters"></a>Parametry

*lptm*<br/>
Wskaźnik do [textmetric](/windows/win32/api/wingdi/ns-wingdi-textmetricw) struktury, która otrzyma informacje.

## <a name="cfontholderreleasefont"></a><a name="releasefont"></a>CFontHolder::ReleaseFont

Ta funkcja odłącza `CFontHolder` `IFont` obiekt od jego interfejsu.

```
void ReleaseFont();
```

## <a name="cfontholderselect"></a><a name="select"></a>CFontHolder::Wybierz

Wywołanie tej funkcji, aby wybrać czcionkę formantu w określonym kontekście urządzenia.

```
CFont* Select(
    CDC* pDC,
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Kontekst urządzenia, do którego jest zaznaczona czcionka.

*cylogical (cylogical)*<br/>
Wysokość, w jednostkach logicznych, prostokąta, w którym jest rysowana formant.

*cyHimetric (cyHimetric)*<br/>
Wysokość, w MM_HIMETRIC jednostkach, sterowania.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do czcionki, która jest zastępowana.

### <a name="remarks"></a>Uwagi

Zobacz [GetFontHandle do](#getfonthandle) dyskusji *cyLogical* i *cyHimetric* parametrów.

## <a name="cfontholdersetfont"></a><a name="setfont"></a>CFontHolder::SetFont

Zwalnia dowolną istniejącą czcionkę i łączy obiekt z `CFontHolder` interfejsem. `IFont`

```
void SetFont(LPFONT pNewFont);
```

### <a name="parameters"></a>Parametry

*pNewFont*<br/>
Wskaźnik do `IFont` nowego interfejsu.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CPropExchange](../../mfc/reference/cpropexchange-class.md)
