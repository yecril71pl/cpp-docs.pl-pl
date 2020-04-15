---
title: CMFCRibbonSlider, klasa
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
ms.openlocfilehash: f2a05ca1433ca3a44b0459360e3f09fe7a274c68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368833"
---
# <a name="cmfcribbonslider-class"></a>CMFCRibbonSlider, klasa

Klasa `CMFCRibbonSlider` implementuje kontrolkę suwaka, którą można dodać do paska wstążki lub paska stanu wstążki. Suwak wstążki przypomina suwaki powiększenia, które pojawiają się w aplikacjach pakietu Office 2007.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonSlider : public CMFCRibbonBaseElement
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonSlider::CMFCRibbonSlider](#cmfcribbonslider)|Konstruuje i inicjuje kontrolkę suwaka wstążki.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonSlider::GetPos](#getpos)|Zwraca bieżącą pozycję suwaka.|
|[CMFCRibbonSlider::GetRangeMax](#getrangemax)|Zwraca maksymalną wartość suwaka.|
|[CMFCRibbonSlider::GetRangeMin](#getrangemin)|Zwraca minimalną wartość suwaka.|
|[CMFCRibbonSlider::GetRegularSize](#getregularsize)|Zwraca regularny rozmiar elementu wstążki. (Zastępuje [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonSlider::GetZoomIncrement](#getzoomincrement)|Zwraca rozmiar przyrostu powiększenia dla suwaka.|
|[CMFCRibbonSlider::HasZoomButtons](#haszoombuttons)|Określa, czy suwak ma przyciski powiększenia.|
|[CMFCRibbonSlider::OnDraw](#ondraw)|Wywoływana przez strukturę do rysowania elementu wstążki. (Zastępuje [CMFCRibbonBaseElement::OnDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|
|[CMFCRibbonSlider::SetPos](#setpos)|Ustawia bieżącą pozycję suwaka.|
|[CMFCRibbonSlider::SetRange](#setrange)|Określa zakres suwaka, ustawiając wartości minimalne i maksymalne.|
|[CMFCRibbonSlider::SetZoomButtons](#setzoombuttons)|Pokazuje lub ukrywa przyciski powiększenia.|
|[CMFCRibbonSlider::SetZoomIncrement](#setzoomincrement)|Ustawia rozmiar przyrostu powiększenia dla suwaka.|

## <a name="remarks"></a>Uwagi

Za pomocą `SetRange` tej metody można skonfigurować zakres przyrostów powiększenia suwaka. Bieżącą pozycję suwaka można ustawić `SetPos` za pomocą metody.

Za pomocą tej metody można wyświetlać okrągłe przyciski powiększenia po lewej i prawej stronie suwaka. `SetZoomButtons` Domyślnie suwak jest poziomy, lewy przycisk powiększenia wyświetla znak minus, a prawy przycisk powiększenia wyświetla znak plus.

Metoda `SetZoomIncrement` definiuje przyrost, aby dodać lub odjąć od bieżącej pozycji, gdy użytkownik kliknie przyciski powiększenia.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCRibbonSlider` używać różnych metod w klasie, aby ustawić właściwości suwaka. W przykładzie pokazano, `CMFCRibbonSlider` jak skonstruować obiekt, wyświetlić przyciski powiększenia, ustawić bieżącą pozycję suwaka i ustawić zakres wartości dla suwaka.

[!code-cpp[NVC_MFC_RibbonApp#12](../../mfc/reference/codesnippet/cpp/cmfcribbonslider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxribbonslider.h

## <a name="cmfcribbonslidercmfcribbonslider"></a><a name="cmfcribbonslider"></a>CMFCRibbonSlider::CMFCRibbonSlider

Skonstruuj suwak wstążki.

```
CMFCRibbonSlider(
    UINT nID,
    int nWidth=100);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
[w] Identyfikator suwaka.

[w]. *nWidth (ww.* Szerokość suwaka w pikselach.

### <a name="remarks"></a>Uwagi

Tworzy suwak wstążki o szerokości *nWidth* pikseli w kategorii panelu, w którym jest dodawany suwak. Domyślnie suwak jest poziomy.

## <a name="cmfcribbonslidergetpos"></a><a name="getpos"></a>CMFCRibbonSlider::GetPos

Zwraca bieżącą pozycję suwaka.

```
int GetPos() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca pozycja suwaka, która jest pozycją względem początku suwaka.

## <a name="cmfcribbonslidergetrangemax"></a><a name="getrangemax"></a>CMFCRibbonSlider::GetRangeMax

Uzyskuje maksymalny przyrost suwaka, który suwak może przesuwać na suwaku.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Wartość zwracana

Maksymalny przyrost suwaka, który suwak może przesuwać na suwaku.

## <a name="cmfcribbonslidergetrangemin"></a><a name="getrangemin"></a>CMFCRibbonSlider::GetRangeMin

Zwraca minimalny przyrost, który suwak może przesuwać na suwaku.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Wartość zwracana

Minimalny przyrost, który suwak może przesuwać na suwaku.

## <a name="cmfcribbonslidergetregularsize"></a><a name="getregularsize"></a>CMFCRibbonSlider::GetRegularSize

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[w] *pDC*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonslidergetzoomincrement"></a><a name="getzoomincrement"></a>CMFCRibbonSlider::GetZoomIncrement

Uzyskaj przyrost powiększenia dla suwaka.

```
int GetZoomIncrement() const;
```

### <a name="return-value"></a>Wartość zwracana

Przyrost powiększenia dla suwaka.

## <a name="cmfcribbonsliderhaszoombuttons"></a><a name="haszoombuttons"></a>CMFCRibbonSlider::HasZoomButtons

Określa, czy suwak ma przyciski powiększenia.

```
BOOL HasZoomButtons() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli suwak ma przyciski powiększenia; FAŁSZ inaczej.

## <a name="cmfcribbonsliderondraw"></a><a name="ondraw"></a>CMFCRibbonSlider::OnDraw

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[w] *pDC*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonslidersetpos"></a><a name="setpos"></a>CMFCRibbonSlider::SetPos

Ustaw bieżącą pozycję suwaka.

```
void SetPos(
    int nPos,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parametry

*nPos (właso)*<br/>
[w] Określa położenie, które ma być ustawione dla suwaka. Pozycja jest względem początku suwaka.

*bRedraw*<br/>
[w] Jeśli true, suwak zostanie ponownie narysowany.

## <a name="cmfcribbonslidersetrange"></a><a name="setrange"></a>CMFCRibbonSlider::SetRange

Ustaw zakres wartości dla suwaka.

```
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parametry

*nMin (min.*<br/>
[w] Określa minimalną wartość suwaka.

*Nmax*<br/>
[w] Określa maksymalną wartość suwaka.

### <a name="remarks"></a>Uwagi

Określa zakres wartości formantu suwaka, ustawiając wartości minimalne i maksymalne.

## <a name="cmfcribbonslidersetzoombuttons"></a><a name="setzoombuttons"></a>CMFCRibbonSlider::SetZoomButtons

Wyświetlanie lub ukrywanie przycisków powiększenia.

```
void SetZoomButtons(BOOL bSet=TRUE);
```

### <a name="parameters"></a>Parametry

[w]. *bStaw* PRAWDA, aby wyświetlić przyciski powiększenia; FALSE, aby je ukryć.

## <a name="cmfcribbonslidersetzoomincrement"></a><a name="setzoomincrement"></a>CMFCRibbonSlider::SetZoomIncrement

Ustaw przyrost powiększenia dla suwaka.

```
void SetZoomIncrement(int nZoomIncrement);
```

### <a name="parameters"></a>Parametry

*nZoomIncrement*<br/>
[w] Określa przyrost powiększenia suwaka.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)
