---
title: Klasa CMFCRibbonCheckBox
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetCompactSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetIntermediateSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetRegularSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::IsDrawTooltipImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDraw
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawMenuImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawOnList
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::SetACCData
helpviewer_keywords:
- CMFCRibbonCheckBox [MFC], CMFCRibbonCheckBox
- CMFCRibbonCheckBox [MFC], GetCompactSize
- CMFCRibbonCheckBox [MFC], GetIntermediateSize
- CMFCRibbonCheckBox [MFC], GetRegularSize
- CMFCRibbonCheckBox [MFC], IsDrawTooltipImage
- CMFCRibbonCheckBox [MFC], OnDraw
- CMFCRibbonCheckBox [MFC], OnDrawMenuImage
- CMFCRibbonCheckBox [MFC], OnDrawOnList
- CMFCRibbonCheckBox [MFC], SetACCData
ms.assetid: 3a6c3891-c8d1-4af0-b954-7b9ab048782a
ms.openlocfilehash: 089c8056afebef31ff98a435bf145566ae64fe1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375257"
---
# <a name="cmfcribboncheckbox-class"></a>Klasa CMFCRibbonCheckBox

Klasa `CMFCRibbonCheckBox` implementuje pole wyboru, które można dodać do panelu wstążki, paska narzędzi Szybki dostęp lub menu podręcznego.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonCheckBox : public CMFCRibbonButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonCheckBox::GetCompactSize](#getcompactsize)|(Zastępuje [CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|
|[CMFCRibbonCheckBox::GetIntermediateSize](#getintermediatesize)|(Zastępuje [CMFCRibbonButton::GetIntermediateSize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize).)|
|[CMFCRibbonCheckBox::GetRegularSize](#getregularsize)|(Zastępuje [CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|(Przesłania `CMFCRibbonButton::IsDrawTooltipImage`).|
|[CMFCRibbonCheckBox::OnDraw](#ondraw)|(Zastępuje [CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(Zastępuje [CMFCRibbonBaseElement::OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|(Przesłania `CMFCRibbonButton::OnDrawOnList`).|
|[CMFCRibbonCheckBox::SetACCData](#setaccdata)|(Zastępuje [CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|

## <a name="remarks"></a>Uwagi

Aby użyć `CMFCRibbonCheckBox` w aplikacji, dodaj do kodu następujący konstruktor:

```
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)
```

gdzie *nID* jest polem wyboru ID, a *lpszText* jest etykietą tekstową pola wyboru.

Pole wyboru można dodać do panelu wstążki za pomocą [polecenia CMFCRibbonPanel::Dodaj](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxribboncheckbox.h

## <a name="cmfcribboncheckboxcmfcribboncheckbox"></a><a name="cmfcribboncheckbox"></a>CMFCRibbonCheckBox::CMFCRibbonCheckBox

Konstruktor obiektu pola wyboru wstążki

```
CMFCRibbonCheckBox(
    UINT nID,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
[w] Określa identyfikator polecenia.

*lpszText (tekst)*<br/>
[w] Określa etykietę tekstową.

### <a name="return-value"></a>Wartość zwracana

Konstruuje obiekt pola wyboru wstążki.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCRibbonCheckBox` skonstruować obiekt klasy.

[!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]

## <a name="cmfcribboncheckboxgetcompactsize"></a><a name="getcompactsize"></a>CMFCRibbonCheckBox::GetCompactSize

Po zastąpieniu pobiera kompaktowy rozmiar pola wyboru.

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do cdc skojarzonego z polem wyboru.

### <a name="return-value"></a>Wartość zwracana

Zwraca `CSize` obiekt zawierający kompaktowy rozmiar pola wyboru.

### <a name="remarks"></a>Uwagi

Jeśli nie zostanie zastąpiony, zwraca pośredni rozmiar pola wyboru.

## <a name="cmfcribboncheckboxgetintermediatesize"></a><a name="getintermediatesize"></a>CMFCRibbonCheckBox::GetIntermediateSize

Pobiera rozmiar pośredni pola wyboru.

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do cdc skojarzone z tym polem wyboru.

### <a name="return-value"></a>Wartość zwracana

Obiekt `CSize` zawierający rozmiar pośredni pola wyboru.

### <a name="remarks"></a>Uwagi

Jeśli nie zostanie zastąpiony, oblicza rozmiar pośredni jako `AFX_CHECK_BOX_DEFAULT_SIZE`domyślny rozmiar pola wyboru ( ) plus rozmiar tekstu plus marginesy.

## <a name="cmfcribboncheckboxgetregularsize"></a><a name="getregularsize"></a>CMFCRibbonCheckBox::GetRegularSize

Pobiera regularny rozmiar pola wyboru.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do obiektu CDC skojarzonego z tym polem wyboru.

### <a name="return-value"></a>Wartość zwracana

Zwraca `CSize` obiekt zawierający zwykły rozmiar pola wyboru.

### <a name="remarks"></a>Uwagi

Jeśli nie zostanie zastąpiony, zwraca pośredni rozmiar pola wyboru.

## <a name="cmfcribboncheckboxisdrawtooltipimage"></a><a name="isdrawtooltipimage"></a>CMFCRibbonCheckBox::IsDrawTooltipImage

Wskazuje, czy z polem wyboru jest skojarzony obraz etykietki narzędzia.

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli z polem wyboru jest skojarzony obraz etykietki narzędzia, lub wartość FAŁszu, jeśli nie.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboncheckboxondraw"></a><a name="ondraw"></a>CMFCRibbonCheckBox::OnDraw

Wywoływane przez strukturę, aby narysować pole wyboru przy użyciu kontekstu określonego urządzenia.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do CDC, w którym ma być rysowane pole wyboru.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboncheckboxondrawmenuimage"></a><a name="ondrawmenuimage"></a>CMFCRibbonCheckBox::OnDrawMenuImage

Wywoływane przez strukturę, aby narysować obraz menu dla pola wyboru.

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>Parametry

[w] *&#42;CDC*<br/>
Wskaźnik do cdc skojarzonego z polem wyboru.

*Crect*<br/>
[w] Obiekt `CRect` określający prostokąt, w którym ma być rysowany obraz menu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli obraz został narysowany, lub WARTOŚĆ FAŁSZ, jeśli nie.

### <a name="remarks"></a>Uwagi

Jeśli nie zostanie zastąpiony, zwraca wartość FAŁSZ.

## <a name="cmfcribboncheckboxondrawonlist"></a><a name="ondrawonlist"></a>CMFCRibbonCheckBox::OnDrawOnList

Wywoływane przez strukturę, aby narysować pole wyboru w polu listy poleceń.

```
virtual void OnDrawOnList(
    CDC* pDC,
    CString strText,
    int nTextOffset,
    CRect rect,
    BOOL bIsSelected,
    BOOL bHighlighted);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia, w którym ma być rysowane pole wyboru.

*strText (tekst)*<br/>
[w] Wyświetlany tekst.

*nTextOffset (Zestaw nTextOffset)*<br/>
[w] Odległość w pikselach od lewej strony pola listy do wyświetlanego tekstu.

*Rect*<br/>
[w] Prostokąt wyświetlania pola wyboru.

*bWybrany*<br/>
[w] PRAWDA, jeśli pole wyboru jest zaznaczone, lub FAŁSZ, jeśli nie.

*bWyświetlony*<br/>
[w] PRAWDA, jeśli pole wyboru jest wyróżnione, lub FAŁSZ, jeśli nie.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboncheckboxsetaccdata"></a><a name="setaccdata"></a>CMFCRibbonCheckBox::SetACCData

Ustawia dane ułatwień dostępu dla pola wyboru.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parametry

*pRoczysz*<br/>
Okno nadrzędne pola wyboru.

*Danych*<br/>
Dane ułatwień dostępu dla tego pola wyboru.

### <a name="return-value"></a>Wartość zwracana

Zawsze zwraca wartość PRAWDA.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda ustawia dane ułatwień dostępu dla pola wyboru i zawsze zwraca wartość PRAWDA. Zastądeń tę metodę, aby ustawić dane ułatwień dostępu i zwrócić wartość, która wskazuje na sukces lub niepowodzenie.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)
