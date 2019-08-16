---
title: Klasa CMFCPropertyGridFontProperty
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetLogFont
helpviewer_keywords:
- CMFCPropertyGridFontProperty [MFC], CMFCPropertyGridFontProperty
- CMFCPropertyGridFontProperty [MFC], GetColor
- CMFCPropertyGridFontProperty [MFC], GetLogFont
ms.assetid: 83693f33-bbd3-4fcb-a9ad-fa79fcf2ca24
ms.openlocfilehash: a3c5b806482a97d64a9ffab92877781cb8778b6b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505112"
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
|[CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty](#cmfcpropertygridfontproperty)|Konstruuje `CMFCPropertyGridFontProperty` obiekt.|
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCPropertyGridFontProperty::FormatProperty`|Formatuje tekstową reprezentację wartości właściwości. (Przesłania [CMFCPropertyGridProperty:: FormatProperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty).)|
|[CMFCPropertyGridFontProperty::GetColor](#getcolor)|Pobiera kolor czcionki wybierany przez użytkownika z okna dialogowego czcionka.|
|[CMFCPropertyGridFontProperty::GetLogFont](#getlogfont)|Pobiera czcionkę wybieraną przez użytkownika z okna dialogowego czcionka.|
|`CMFCPropertyGridFontProperty::GetThisClass`|Używane przez platformę do uzyskania wskaźnika do obiektu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , który jest skojarzony z tym typem klasy.|
|`CMFCPropertyGridFontProperty::OnClickButton`|Wywoływane przez platformę, gdy użytkownik kliknie przycisk znajdujący się w właściwości. (Przesłania [CMFCPropertyGridProperty:: OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

## <a name="remarks"></a>Uwagi

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxpropertygridctrl. h

##  <a name="cmfcpropertygridfontproperty"></a>CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty

Konstruuje `CMFCPropertyGridFontProperty` obiekt.

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
podczas Nazwa właściwości.

*wiersza*<br/>
podczas Struktura czcionki logicznej, która określa atrybuty czcionki.

*dwFontDialogFlags*<br/>
podczas Style, które są stosowane do okna dialogowego czcionka, które są wyświetlane po kliknięciu przycisku listy rozwijanej wartość właściwości. Wartość domyślna to kombinacja bitowa (lub) CF_EFFECTS i CF_SCREENFONTS. Aby uzyskać więcej informacji, zobacz parametr flags [struktury CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw).

*lpszDescr*<br/>
podczas Opis właściwości font. Wartość domyślna to NULL.

*dwData*<br/>
podczas Dane specyficzne dla aplikacji, takie jak liczba całkowita lub wskaźnik do innych danych, które są skojarzone z właściwością. Wartość domyślna to 0.

*Kolor*<br/>
podczas Kolor czcionki. Wartością domyślną jest kolor domyślny.

### <a name="remarks"></a>Uwagi

`CMFCPropertyGridFontProperty` Obiekt reprezentuje właściwość Font w kontrolce czcionki siatki właściwości.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób konstruowania obiektu `CMFCPropertyGridFontProperty` klasy. Ten przykład jest częścią [nowych kontrolek](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]

##  <a name="getcolor"></a>CMFCPropertyGridFontProperty:: GetColor

Pobiera kolor czcionki wybierany przez użytkownika z okna dialogowego czcionka.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość koloru RGB, która reprezentuje wybrany kolor czcionki.

### <a name="remarks"></a>Uwagi

##  <a name="getlogfont"></a>CMFCPropertyGridFontProperty::GetLogFont

Pobiera czcionkę wybieraną przez użytkownika z okna dialogowego czcionka.

```
LPLOGFONT GetLogFont();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do struktury [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) , który opisuje wybraną czcionkę.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[Klasa CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)
