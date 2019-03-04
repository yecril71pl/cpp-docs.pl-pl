---
title: Klasa CMFCRibbonSlider
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMax
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMin
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRegularSize
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetZoomIncrement
- AFXRIBBONSLIDER/CMFCRibbonSlider::HasZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::OnDraw
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetRange
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomIncrement
helpviewer_keywords:
- CMFCRibbonSlider [MFC], CMFCRibbonSlider
- CMFCRibbonSlider [MFC], GetPos
- CMFCRibbonSlider [MFC], GetRangeMax
- CMFCRibbonSlider [MFC], GetRangeMin
- CMFCRibbonSlider [MFC], GetRegularSize
- CMFCRibbonSlider [MFC], GetZoomIncrement
- CMFCRibbonSlider [MFC], HasZoomButtons
- CMFCRibbonSlider [MFC], OnDraw
- CMFCRibbonSlider [MFC], SetPos
- CMFCRibbonSlider [MFC], SetRange
- CMFCRibbonSlider [MFC], SetZoomButtons
- CMFCRibbonSlider [MFC], SetZoomIncrement
ms.assetid: 9351ac34-f234-4e42-91e2-763f1989c8ff
ms.openlocfilehash: 85c646e2fa524268e4559b587f90c5e06971b765
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300332"
---
# <a name="cmfcribbonslider-class"></a>Klasa CMFCRibbonSlider

`CMFCRibbonSlider` Klasa implementuje kontrolkę suwaka, możesz dodać do paska Wstążki lub paska stanu wstążki. Kontrolka suwaka wstążki przypomina suwaki zoomu, które pojawiają się w aplikacjach pakietu Office 2007.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonSlider : public CMFCRibbonBaseElement
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonSlider::CMFCRibbonSlider](#cmfcribbonslider)|Tworzy i inicjuje kontrolka suwaka wstążki.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonSlider::GetPos](#getpos)|Zwraca bieżące położenie kontrolki suwaka.|
|[CMFCRibbonSlider::GetRangeMax](#getrangemax)|Zwraca maksymalną wartość suwaka.|
|[CMFCRibbonSlider::GetRangeMin](#getrangemin)|Zwraca minimalną wartość suwaka.|
|[CMFCRibbonSlider::GetRegularSize](#getregularsize)|Zwraca zwykłego rozmiaru elementu wstążki. (Przesłania [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonSlider::GetZoomIncrement](#getzoomincrement)|Zwraca rozmiar zmiany wielkości dla kontrolki suwaka.|
|[CMFCRibbonSlider::HasZoomButtons](#haszoombuttons)|Określa, czy suwak ma przycisków powiększenia.|
|[CMFCRibbonSlider::OnDraw](#ondraw)|Metoda wywoływana przez platformę, by narysować elementem wstążki. (Przesłania [CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|
|[CMFCRibbonSlider::SetPos](#setpos)|Ustawia bieżące położenie kontrolki suwaka.|
|[CMFCRibbonSlider::SetRange](#setrange)|Określa zakres kontrolki suwaka, ustawiając wartości minimalne i maksymalne.|
|[CMFCRibbonSlider::SetZoomButtons](#setzoombuttons)|Wyświetlenie lub ukrycie przycisków powiększenia.|
|[CMFCRibbonSlider::SetZoomIncrement](#setzoomincrement)|Ustawia rozmiar zmiany wielkości dla kontrolki suwaka.|

## <a name="remarks"></a>Uwagi

Możesz użyć `SetRange` Metoda konfiguracji zakresu zwiększa powiększenie potrzeby suwaka. Bieżące położenie suwaka można ustawić przy użyciu `SetPos` metody.

Przycisków powiększenia cykliczne można wyświetlić po lewej i prawej stronie kontrolki suwaka, używając `SetZoomButtons` metody. Domyślnie suwak jest poziomy, przycisku powiększenie po lewej stronie zawiera znak minus i przycisku powiększenie prawo wyświetla znak plus.

`SetZoomIncrement` Metoda Określa przyrost do dodania lub odjęcia od aktualnej pozycji, gdy użytkownik kliknie przycisków powiększenia.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak korzystać z różnych metod w `CMFCRibbonSlider` klasy, aby ustawić właściwości suwaka. W przykładzie pokazano sposób tworzenia `CMFCRibbonSlider` obiektu, wyświetlanie przycisków powiększenia, Ustaw bieżące położenie kontrolki suwaka i ustaw zakres wartości dla kontrolki suwaka.

[!code-cpp[NVC_MFC_RibbonApp#12](../../mfc/reference/codesnippet/cpp/cmfcribbonslider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxribbonslider.h

##  <a name="cmfcribbonslider"></a>  CMFCRibbonSlider::CMFCRibbonSlider

Skonstruuj suwaka wstążki.

```
CMFCRibbonSlider(
    UINT nID,
    int nWidth=100);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
[in] Identyfikator suwaka.

[in]. *nWidth* suwaka Szerokość w pikselach.

### <a name="remarks"></a>Uwagi

Konstruuje suwaka wstążki, który jest *nWidth* pikseli w kategorii panelu, w której zostanie dodany suwaka. Domyślnie suwak jest poziomy.

##  <a name="getpos"></a>  CMFCRibbonSlider::GetPos

Zwraca bieżące położenie kontrolki suwaka.

```
int GetPos() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżące położenie kontrolki suwaka, która jest względem początku położenie suwaka.

##  <a name="getrangemax"></a>  CMFCRibbonSlider::GetRangeMax

Pobiera maksymalny przyrost suwaka, które mogą być przesyłane przez suwak w kontrolce suwaka.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalna wartość przyrostu suwaka, które mogą być przesyłane przez suwak w kontrolce suwaka.

##  <a name="getrangemin"></a>  CMFCRibbonSlider::GetRangeMin

Zwraca minimalną inkrementacji, które mogą być przesyłane przez suwak w kontrolce suwaka.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Wartość zwracana

Przyrost minimalne suwak mogą być przesyłane w kontrolce suwaka.

##  <a name="getregularsize"></a>  CMFCRibbonSlider::GetRegularSize

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[in] *podstawowego kontrolera domeny*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getzoomincrement"></a>  CMFCRibbonSlider::GetZoomIncrement

Uzyskaj zmiany wielkości dla kontrolki suwaka.

```
int GetZoomIncrement() const;
```

### <a name="return-value"></a>Wartość zwracana

Zmiany wielkości kontrolki suwaka.

##  <a name="haszoombuttons"></a>  CMFCRibbonSlider::HasZoomButtons

Określa, czy suwak ma przycisków powiększenia.

```
BOOL HasZoomButtons() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli suwak przycisków powiększenia; Wartość FALSE w przeciwnym razie.

##  <a name="ondraw"></a>  CMFCRibbonSlider::OnDraw

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[in] *podstawowego kontrolera domeny*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="setpos"></a>  CMFCRibbonSlider::SetPos

Ustaw bieżące położenie kontrolki suwaka.

```
void SetPos(
    int nPos,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
[in] Określa pozycję, aby ustawić suwak. Pozycja jest określana względem początku suwaka.

*bRedraw*<br/>
[in] W przypadku opcji TRUE suwak zostanie narysowany ponownie.

##  <a name="setrange"></a>  CMFCRibbonSlider::SetRange

Ustaw zakres wartości dla kontrolki suwaka.

```
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
[in] Określa minimalną wartość suwaka.

*nMax*<br/>
[in] Określa maksymalną wartość suwaka.

### <a name="remarks"></a>Uwagi

Określa zakres wartości dla kontrolki suwaka, ustawiając wartości minimalne i maksymalne.

##  <a name="setzoombuttons"></a>  CMFCRibbonSlider::SetZoomButtons

Wyświetlenie lub ukrycie przycisków powiększenia.

```
void SetZoomButtons(BOOL bSet=TRUE);
```

### <a name="parameters"></a>Parametry

[in]. *bUstawienie* true przycisków powiększenia ekranu; Wartość FALSE, aby je ukryć.

##  <a name="setzoomincrement"></a>  CMFCRibbonSlider::SetZoomIncrement

Ustaw zmiany wielkości dla kontrolki suwaka.

```
void SetZoomIncrement(int nZoomIncrement);
```

### <a name="parameters"></a>Parametry

*nZoomIncrement*<br/>
[in] Określa zmiany wielkości kontrolki suwaka.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)
