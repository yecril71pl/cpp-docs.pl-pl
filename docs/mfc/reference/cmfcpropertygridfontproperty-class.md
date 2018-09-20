---
title: Klasa CMFCPropertyGridFontProperty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetLogFont
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridFontProperty [MFC], CMFCPropertyGridFontProperty
- CMFCPropertyGridFontProperty [MFC], GetColor
- CMFCPropertyGridFontProperty [MFC], GetLogFont
ms.assetid: 83693f33-bbd3-4fcb-a9ad-fa79fcf2ca24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d6c1f9f9b2084273345463bccfe4eb2bc78d150
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384393"
---
# <a name="cmfcpropertygridfontproperty-class"></a>Klasa CMFCPropertyGridFontProperty

`CMFCPropertyGridFileProperty` Klasa obsługuje element formantu listy właściwości, który powoduje otwarcie okna dialogowego wyboru czcionki.

## <a name="syntax"></a>Składnia

```
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty](#cmfcpropertygridfontproperty)|Konstruuje `CMFCPropertyGridFontProperty` obiektu.|
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCPropertyGridFontProperty::FormatProperty`|Formatuje tekst reprezentujący wartość właściwości. (Przesłania [CMFCPropertyGridProperty::FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|
|[CMFCPropertyGridFontProperty::GetColor](#getcolor)|Pobiera kolor czcionki, który użytkownik wybiera z okno dialogowe czcionki.|
|[CMFCPropertyGridFontProperty::GetLogFont](#getlogfont)|Pobiera czcionki, który użytkownik wybiera z okno dialogowe czcionki.|
|`CMFCPropertyGridFontProperty::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|
|`CMFCPropertyGridFontProperty::OnClickButton`|Wywoływane przez platformę, gdy użytkownik kliknie przycisk, który jest zawarty we właściwości. (Przesłania [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

## <a name="remarks"></a>Uwagi

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxpropertygridctrl.h

##  <a name="cmfcpropertygridfontproperty"></a>  CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty

Konstruuje `CMFCPropertyGridFontProperty` obiektu.

```
CMFCPropertyGridFontProperty(
    const CString& strName,
    LOGFONT& lf,
    DWORD dwFontDialogFlags = CF_EFFECTS | CF_SCREENFONTS,
    LPCTSTR lpszDescr = NULL,
    DWORD_PTR dwData = 0,
    COLORREF color = (COLORREF)-1);
```

### <a name="parameters"></a>Parametry

*strName*<br/>
[in] Nazwa właściwości.

*LF*<br/>
[in] Struktury logicznej czcionek, która określa atrybuty czcionki.

*dwFontDialogFlags*<br/>
[in] Style, które są stosowane do czcionki okna dialogowego wyświetlanego po kliknięciu przycisku rozwijanego wartości właściwości. Wartością domyślną jest bitową kombinacją (lub) CF_EFFECTS i CF_SCREENFONTS. Aby uzyskać więcej informacji, zobacz *flagi* parametru [struktury CHOOSEFONT](/windows/desktop/api/commdlg/ns-commdlg-tagchoosefonta).

*lpszDescr*<br/>
[in] Opis właściwości czcionki. Wartością domyślną jest NULL.

*dwData*<br/>
[in] Dane specyficzne dla aplikacji, takich jak liczby całkowitej lub wskaźnika do innych danych, który jest skojarzony z właściwością. Wartość domyślna to 0.

*Kolor*<br/>
[in] Kolor czcionki. Wartość domyślna to domyślny kolor.

### <a name="remarks"></a>Uwagi

A `CMFCPropertyGridFontProperty` obiekt reprezentuje właściwość czcionki w kontrolce czcionki siatki właściwości.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak skonstruować obiekt `CMFCPropertyGridFontProperty` klasy. W tym przykładzie jest częścią [przykładowe nowych formantów](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]

##  <a name="getcolor"></a>  CMFCPropertyGridFontProperty::GetColor

Pobiera kolor czcionki, który użytkownik wybiera z okno dialogowe czcionki.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość koloru RGB, który reprezentuje kolor wybranej czcionki.

### <a name="remarks"></a>Uwagi

##  <a name="getlogfont"></a>  CMFCPropertyGridFontProperty::GetLogFont

Pobiera czcionki, który użytkownik wybiera z okno dialogowe czcionki.

```
LPLOGFONT GetLogFont();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) strukturę, która opisuje wybranej czcionki.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[Klasa CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)
