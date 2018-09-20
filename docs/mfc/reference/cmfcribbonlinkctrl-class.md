---
title: Klasa CMFCRibbonLinkCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 24dc82015e003b3a2ddbbd202dd6cba9176154eb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440085"
---
# <a name="cmfcribbonlinkctrl-class"></a>Klasa CMFCRibbonLinkCtrl

Implementuje hiperłącze, które jest umieszczone na Wstążce. Hiperłącze otwiera stronę sieci Web, gdy zostanie kliknięte.
Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonLinkCtrl : public CMFCRibbonButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl](#cmfcribbonlinkctrl)|Tworzy i inicjuje `CMFCRibbonLinkCtrl` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CopyFrom](#copyfrom)|(Przesłania `CMFCRibbonButton::CopyFrom`.)|
|[CMFCRibbonLinkCtrl::GetCompactSize](#getcompactsize)|(Przesłania [CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|
|[CMFCRibbonLinkCtrl::GetLink](#getlink)|Zwraca wartość hiperłącze.|
|[CMFCRibbonLinkCtrl::GetRegularSize](#getregularsize)|(Przesłania [CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|
|[CMFCRibbonLinkCtrl::GetToolTipText](#gettooltiptext)|(Przesłania [CMFCRibbonButton::GetToolTipText](../../mfc/reference/cmfcribbonbutton-class.md#gettooltiptext).)|
|[CMFCRibbonLinkCtrl::IsDrawTooltipImage](#isdrawtooltipimage)|(Przesłania `CMFCRibbonButton::IsDrawTooltipImage`.)|
|[CMFCRibbonLinkCtrl::OnDraw](#ondraw)|(Przesłania [CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|
|[CMFCRibbonLinkCtrl::OnDrawMenuImage](#ondrawmenuimage)|(Przesłania [CMFCRibbonBaseElement::OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|
|[CMFCRibbonLinkCtrl::OnMouseMove](#onmousemove)|(Przesłania `CMFCRibbonButton::OnMouseMove`.)|
|[CMFCRibbonLinkCtrl::OnSetIcon](#onseticon)||
|[CMFCRibbonLinkCtrl::OpenLink](#openlink)|Otwiera stronę sieci Web, określone w hiperlink.|
|[CMFCRibbonLinkCtrl::SetLink](#setlink)|Ustawia wartość hiperłącze.|

## <a name="remarks"></a>Uwagi

Po utworzeniu hiperłącze, dodaj go do panelu, wywołując [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md) [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md) [CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxRibbonLinkCtrl.h

##  <a name="cmfcribbonlinkctrl"></a>  CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl

Tworzy i inicjuje [CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md) obiektu.

```
CMFCRibbonLinkCtrl(
    UINT nID,
    LPCTSTR lpszText,
    LPCTSTR lpszLink);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
[in] Określa identyfikator polecenia polecenia, który jest wykonywany po kliknięciu kontrolki łącza.

*lpszText*<br/>
[in] Określa etykietę do wyświetlenia w formancie łącza.

*lpszLink*<br/>
[in] Określa hiperłącze skojarzonego z kontrolką łącza.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać konstruktora `CMFCRibbonLinkCtrl` klasy. Ten fragment kodu jest częścią [przykładowe gadżetów wstążki](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RibbonGadgets#1](../../mfc/reference/codesnippet/cpp/cmfcribbonlinkctrl-class_1.cpp)]

##  <a name="copyfrom"></a>  CMFCRibbonLinkCtrl::CopyFrom


```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parametry

[in] *src*

### <a name="remarks"></a>Uwagi

##  <a name="getcompactsize"></a>  CMFCRibbonLinkCtrl::GetCompactSize


```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[in] *podstawowego kontrolera domeny*

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getlink"></a>  CMFCRibbonLinkCtrl::GetLink

Zwraca wartość hiperłącze.

```
LPCTSTR GetLink() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość hiperłącze.

### <a name="remarks"></a>Uwagi

##  <a name="getregularsize"></a>  CMFCRibbonLinkCtrl::GetRegularSize


```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[in] *podstawowego kontrolera domeny*

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="gettooltiptext"></a>  CMFCRibbonLinkCtrl::GetToolTipText


```
virtual CString GetToolTipText() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="ondrawmenuimage"></a>  CMFCRibbonLinkCtrl::OnDrawMenuImage


```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>Parametry

[in] *CDC** [in] *CRect*

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="isdrawtooltipimage"></a>  CMFCRibbonLinkCtrl::IsDrawTooltipImage


```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="ondraw"></a>  CMFCRibbonLinkCtrl::OnDraw


```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[in] *podstawowego kontrolera domeny*

### <a name="remarks"></a>Uwagi

##  <a name="onmousemove"></a>  CMFCRibbonLinkCtrl::OnMouseMove


```
virtual void OnMouseMove(CPoint point);
```

### <a name="parameters"></a>Parametry

[in] *punktu*

### <a name="remarks"></a>Uwagi

##  <a name="onseticon"></a>  CMFCRibbonLinkCtrl::OnSetIcon


```
virtual void OnSetIcon();
```

### <a name="remarks"></a>Uwagi

##  <a name="openlink"></a>  CMFCRibbonLinkCtrl::OpenLink

Otwiera stronę sieci Web, określone w hiperlink.

```
BOOL OpenLink();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli skojarzona strona sieci Web została otwarta pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Otwiera stronę sieci Web przy użyciu hiperłącza skojarzonego z `CMFCRibbonLinkCtrl` obiektu.

##  <a name="setlink"></a>  CMFCRibbonLinkCtrl::SetLink

Ustawia wartość hiperłącze.

```
void SetLink(LPCTSTR lpszLink);
```

### <a name="parameters"></a>Parametry

*lpszLink*<br/>
[in] Określa tekst, hiperłącze.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)
