---
title: Klasa CFontHolder | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 344e2e39e52aa80624e4959daada5038506bb4c5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433180"
---
# <a name="cfontholder-class"></a>Klasa CFontHolder

Implementuje właściwości czcionki zasobów i hermetyzuje funkcjonalność obiektu czcionki Windows i `IFont` interfejsu.

## <a name="syntax"></a>Składnia

```
class CFontHolder
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFontHolder::CFontHolder](#cfontholder)|Konstruuje `CFontHolder` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFontHolder::GetDisplayString](#getdisplaystring)|Pobiera ciąg wyświetlany w przeglądarce właściwości kontenera.|
|[CFontHolder::GetFontDispatch](#getfontdispatch)|Zwraca czcionki `IDispatch` interfejsu.|
|[CFontHolder::GetFontHandle](#getfonthandle)|Zwraca uchwyt do czcionki Windows.|
|[CFontHolder::InitializeFont](#initializefont)|Inicjuje `CFontHolder` obiektu.|
|[CFontHolder::QueryTextMetrics](#querytextmetrics)|Pobiera informacje o powiązanych czcionki.|
|[CFontHolder::ReleaseFont](#releasefont)|Odłącza `CFontHolder` obiektu z `IFont` i `IFontNotification` interfejsów.|
|[CFontHolder::Select](#select)|Wybiera zasobów czcionki do kontekstu urządzenia.|
|[CFontHolder::SetFont](#setfont)|Łączy `CFontHolder` obiekt `IFont` interfejsu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CFontHolder::m_pFont](#m_pfont)|Wskaźnik do `CFontHolder` obiektu `IFont` interfejsu.|

## <a name="remarks"></a>Uwagi

`CFontHolder` nie ma klasy bazowej.

Ta klasa umożliwia Implementowanie właściwości niestandardowej czcionki dla kontrolki. Aby uzyskać informacje na temat tworzenia takich właściwości, zobacz artykuł [kontrolek ActiveX: przy użyciu czcionek](../../mfc/mfc-activex-controls-using-fonts.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CFontHolder`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxctl.h

##  <a name="cfontholder"></a>  CFontHolder::CFontHolder

Konstruuje `CFontHolder` obiektu.

```
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```

### <a name="parameters"></a>Parametry

*pNotify*<br/>
Wskaźnik na czcionkę `IPropertyNotifySink` interfejsu.

### <a name="remarks"></a>Uwagi

Należy wywołać `InitializeFont` zainicjować wynikowy obiekt przed jego użyciem.

##  <a name="getdisplaystring"></a>  CFontHolder::GetDisplayString

Pobiera ciąg, który może być wyświetlany w przeglądarce właściwości kontenera.

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>Parametry

*strValue*<br/>
Odwołanie do [CString](../../atl-mfc-shared/reference/cstringt-class.md) jest do przechowywania ciągu wyświetlanego.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli ciąg jest pomyślnie pobrane; w przeciwnym razie 0.

##  <a name="getfontdispatch"></a>  CFontHolder::GetFontDispatch

Wywołaj tę funkcję, aby pobrać wskaźnika do interfejs ekspedycji czcionki.

```
LPFONTDISP GetFontDispatch();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CFontHolder` obiektu `IFontDisp` interfejsu. Należy pamiętać, że funkcja wywołująca `GetFontDispatch` musi wywołać `IUnknown::Release` na ten wskaźnik interfejsu, gdy z nią zrobić.

### <a name="remarks"></a>Uwagi

Wywołaj `InitializeFont` przed wywołaniem `GetFontDispatch`.

##  <a name="getfonthandle"></a>  CFontHolder::GetFontHandle

Wywołaj tę funkcję można pobrać uchwytu na czcionkę Windows.

```
HFONT GetFontHandle();


HFONT GetFontHandle(
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>Parametry

*cyLogical*<br/>
Wysokość w jednostkach logicznych prostokąt, w którym jest rysowana formantu.

*cyHimetric*<br/>
Wysokość w jednostkach MM_HIMETRIC formantu.

### <a name="return-value"></a>Wartość zwracana

Dojście do obiektu czcionki. w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Stosunek *cyLogical* i *cyHimetric* jest używane do obliczania rozmiaru wyświetlania właściwe, w jednostkach logicznych, aby uzyskać rozmiar czcionki w punktach wyrażona w jednostkach MM_HIMETRIC:

Rozmiar ekranu = ( *cyLogical* / *cyHimetric*) X rozmiar czcionki

Wersja bez parametrów, która zwraca uchwyt na czcionkę, rozmiar ekranu.

##  <a name="initializefont"></a>  CFontHolder::InitializeFont

Inicjuje `CFontHolder` obiektu.

```
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,
    LPDISPATCH pFontDispAmbient = NULL);
```

### <a name="parameters"></a>Parametry

*pFontDesc*<br/>
Wskaźnik do struktury opis czcionek ( [FONTDESC](/windows/desktop/api/olectl/ns-olectl-tagfontdesc)), który określa właściwości czcionki.

*pFontDispAmbient*<br/>
Wskaźnik do otoczenia właściwość czcionki kontenera.

### <a name="remarks"></a>Uwagi

Jeśli *pFontDispAmbient* nie ma wartości NULL, `CFontHolder` połączony jest obiekt klonu `IFont` interfejs używany przez właściwości czcionki kontenera.

Jeśli *pFontDispAmbient* jest wartość NULL, nowe czcionka obiektu jest utworzona na podstawie opisu czcionki wskazywany przez *pFontDesc* lub, jeśli *pFontDesc* ma wartość NULL, wartości domyślnej Opis.

Wywołaj tę funkcję po konstruowanie `CFontHolder` obiektu.

##  <a name="m_pfont"></a>  CFontHolder::m_pFont

Wskaźnik do `CFontHolder` obiektu `IFont` interfejsu.

```
LPFONT m_pFont;
```

##  <a name="querytextmetrics"></a>  CFontHolder::QueryTextMetrics

Pobiera informacje o fizycznej czcionki, reprezentowane przez `CFontHolder` obiektu.

```
void QueryTextMetrics(LPTEXTMETRIC lptm);
```

### <a name="parameters"></a>Parametry

*lptm*<br/>
Wskaźnik do [TEXTMETRIC](/windows/desktop/api/wingdi/ns-wingdi-tagtextmetrica) struktury, który będzie otrzymywać informacje.

##  <a name="releasefont"></a>  CFontHolder::ReleaseFont

Ta funkcja odłącza `CFontHolder` obiekt z jego `IFont` interfejsu.

```
void ReleaseFont();
```

##  <a name="select"></a>  CFontHolder::Select

Wywołaj tę funkcję, aby wybrać czcionkę kontroli nad w kontekście określonego urządzenia.

```
CFont* Select(
    CDC* pDC,
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
Kontekst urządzenia, do którego wybrano czcionki.

*cyLogical*<br/>
Wysokość w jednostkach logicznych prostokąt, w którym jest rysowana formantu.

*cyHimetric*<br/>
Wysokość w jednostkach MM_HIMETRIC formantu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do czcionki, który jest zastępowany.

### <a name="remarks"></a>Uwagi

Zobacz [GetFontHandle](#getfonthandle) dyskusję na temat *cyLogical* i *cyHimetric* parametrów.

##  <a name="setfont"></a>  CFontHolder::SetFont

Zwalnia wszelkie istniejące czcionki i łączy `CFontHolder` obiekt `IFont` interfejsu.

```
void SetFont(LPFONT pNewFont);
```

### <a name="parameters"></a>Parametry

*pNewFont*<br/>
Wskaźnik do nowego `IFont` interfejsu.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CPropExchange](../../mfc/reference/cpropexchange-class.md)
