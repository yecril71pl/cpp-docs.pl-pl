---
title: Klasa CMFCRibbonLinkCtrl
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::CopyFrom
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetCompactSize
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetLink
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetRegularSize
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetToolTipText
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::IsDrawTooltipImage
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnDraw
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnDrawMenuImage
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnMouseMove
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnSetIcon
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OpenLink
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::SetLink
helpviewer_keywords:
- CMFCRibbonLinkCtrl [MFC], CMFCRibbonLinkCtrl
- CMFCRibbonLinkCtrl [MFC], CopyFrom
- CMFCRibbonLinkCtrl [MFC], GetCompactSize
- CMFCRibbonLinkCtrl [MFC], GetLink
- CMFCRibbonLinkCtrl [MFC], GetRegularSize
- CMFCRibbonLinkCtrl [MFC], GetToolTipText
- CMFCRibbonLinkCtrl [MFC], IsDrawTooltipImage
- CMFCRibbonLinkCtrl [MFC], OnDraw
- CMFCRibbonLinkCtrl [MFC], OnDrawMenuImage
- CMFCRibbonLinkCtrl [MFC], OnMouseMove
- CMFCRibbonLinkCtrl [MFC], OnSetIcon
- CMFCRibbonLinkCtrl [MFC], OpenLink
- CMFCRibbonLinkCtrl [MFC], SetLink
ms.assetid: 77ae1941-e0ab-4a9d-911e-1752d34c079b
ms.openlocfilehash: 12a83e45176f7fc6020da1f0d0ee5923ef0f466c
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866171"
---
# <a name="cmfcribbonlinkctrl-class"></a>Klasa CMFCRibbonLinkCtrl

Implementuje hiperlink, które jest umieszczone na Wstążce. Po kliknięciu hiperłącza zostanie otwarta strona sieci Web.
Aby uzyskać więcej szczegółów, zobacz kod źródłowy znajdujący się w folderze **VC\\atlmfc\\src\\MFC** instalacji programu Visual Studio.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonLinkCtrl : public CMFCRibbonButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl](#cmfcribbonlinkctrl)|Konstruuje i inicjuje `CMFCRibbonLinkCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CopyFrom](#copyfrom)|(Przesłania `CMFCRibbonButton::CopyFrom`).|
|[CMFCRibbonLinkCtrl::GetCompactSize](#getcompactsize)|(Przesłania [CMFCRibbonButton:: GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|
|[CMFCRibbonLinkCtrl::GetLink](#getlink)|Zwraca wartość hiperlinku.|
|[CMFCRibbonLinkCtrl::GetRegularSize](#getregularsize)|(Przesłania [CMFCRibbonButton:: GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|
|[CMFCRibbonLinkCtrl::GetToolTipText](#gettooltiptext)|(Przesłania [CMFCRibbonButton:: GetToolTipText](../../mfc/reference/cmfcribbonbutton-class.md#gettooltiptext).)|
|[CMFCRibbonLinkCtrl::IsDrawTooltipImage](#isdrawtooltipimage)|(Przesłania `CMFCRibbonButton::IsDrawTooltipImage`).|
|[CMFCRibbonLinkCtrl::OnDraw](#ondraw)|(Przesłania [CMFCRibbonButton:: OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|
|[CMFCRibbonLinkCtrl::OnDrawMenuImage](#ondrawmenuimage)|(Przesłania [CMFCRibbonBaseElement:: OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|
|[CMFCRibbonLinkCtrl::OnMouseMove](#onmousemove)|(Przesłania `CMFCRibbonButton::OnMouseMove`).|
|[CMFCRibbonLinkCtrl::OnSetIcon](#onseticon)||
|[CMFCRibbonLinkCtrl::OpenLink](#openlink)|Otwiera stronę sieci Web określoną w hiperłączu.|
|[CMFCRibbonLinkCtrl::SetLink](#setlink)|Ustawia wartość hiperlinku.|

## <a name="remarks"></a>Uwagi

Po utworzeniu hiperłącza należy dodać je do panelu przez wywołanie [CMFCRibbonPanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp;[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)

## <a name="requirements"></a>Wymagania

**Header:** afxRibbonLinkCtrl.h

##  <a name="cmfcribbonlinkctrl"></a>CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl

Tworzy i inicjuje obiekt [CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md) .

```
CMFCRibbonLinkCtrl(
    UINT nID,
    LPCTSTR lpszText,
    LPCTSTR lpszLink);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
podczas Określa identyfikator polecenia wykonywanego po kliknięciu kontrolki łącza.

*lpszText*<br/>
podczas Określa etykietę, która ma być wyświetlana w formancie łącza.

*lpszLink*<br/>
podczas Określa hiperłącze skojarzone z kontrolką łącza.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia konstruktora `CMFCRibbonLinkCtrl` klasy. Ten fragment kodu jest częścią [przykładu gadżetów wstążki](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RibbonGadgets#1](../../mfc/reference/codesnippet/cpp/cmfcribbonlinkctrl-class_1.cpp)]

##  <a name="copyfrom"></a>CMFCRibbonLinkCtrl::CopyFrom

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parametry

podczas *src*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="getcompactsize"></a>CMFCRibbonLinkCtrl::GetCompactSize

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

podczas *kontroler PDC*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getlink"></a>CMFCRibbonLinkCtrl:: getlink

Zwraca wartość hiperlinku.

```
LPCTSTR GetLink() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość hiperlinku.

### <a name="remarks"></a>Uwagi

##  <a name="getregularsize"></a>CMFCRibbonLinkCtrl::GetRegularSize

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

podczas *kontroler PDC*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="gettooltiptext"></a>CMFCRibbonLinkCtrl::GetToolTipText

```
virtual CString GetToolTipText() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="ondrawmenuimage"></a>CMFCRibbonLinkCtrl::OnDrawMenuImage

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>Parametry

podczas *Przechwytywanie&#42;*  zmian<br/>
podczas *CRect*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="isdrawtooltipimage"></a>CMFCRibbonLinkCtrl::IsDrawTooltipImage

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="ondraw"></a>CMFCRibbonLinkCtrl:: OnDraw

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

podczas *kontroler PDC*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="onmousemove"></a>CMFCRibbonLinkCtrl:: OnMouseMove

```
virtual void OnMouseMove(CPoint point);
```

### <a name="parameters"></a>Parametry

podczas *punkt*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="onseticon"></a>CMFCRibbonLinkCtrl::OnSetIcon

```
virtual void OnSetIcon();
```

### <a name="remarks"></a>Uwagi

##  <a name="openlink"></a>CMFCRibbonLinkCtrl::OpenLink

Otwiera stronę sieci Web określoną w hiperłączu.

```
BOOL OpenLink();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli skojarzona Strona sieci Web została pomyślnie otwarta; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Otwiera stronę sieci Web przy użyciu hiperłącza skojarzonego z `CMFCRibbonLinkCtrl` obiektem.

##  <a name="setlink"></a>CMFCRibbonLinkCtrl:: SetLink

Ustawia wartość hiperlinku.

```
void SetLink(LPCTSTR lpszLink);
```

### <a name="parameters"></a>Parametry

*lpszLink*<br/>
podczas Określa tekst hiperlinku.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)
