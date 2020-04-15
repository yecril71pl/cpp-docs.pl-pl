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
ms.openlocfilehash: a1c9905d8d7f32a049496c4e164c9eaac13455d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361835"
---
# <a name="cmfcpropertygridfontproperty-class"></a>Klasa CMFCPropertyGridFontProperty

Klasa `CMFCPropertyGridFileProperty` obsługuje element formantu listy właściwości, który otwiera okno dialogowe wyboru czcionek.

## <a name="syntax"></a>Składnia

```
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty](#cmfcpropertygridfontproperty)|Konstruuje `CMFCPropertyGridFontProperty` obiekt.|
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCPropertyGridFontProperty::FormatProperty`|Formatuje tekstową reprezentację wartości właściwości. (Zastępuje [właściwości CMFCPropertyGridProperty::FormatProperty.)](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty)|
|[CMFCPropertyGridFontWłaściwość::GetColor](#getcolor)|Pobiera kolor czcionki wybrany przez użytkownika z okna dialogowego czcionki.|
|[CMFCPropertyGridFontWłaściwość::GetLogFont](#getlogfont)|Pobiera czcionkę, którą użytkownik wybiera z okna dialogowego czcionki.|
|`CMFCPropertyGridFontProperty::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|`CMFCPropertyGridFontProperty::OnClickButton`|Wywoływane przez strukturę, gdy użytkownik kliknie przycisk, który jest zawarty w właściwości. (Zastępuje [właściwości CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

## <a name="remarks"></a>Uwagi

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFontWłaściwość](../../mfc/reference/cmfcpropertygridfontproperty-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxpropertygridctrl.h

## <a name="cmfcpropertygridfontpropertycmfcpropertygridfontproperty"></a><a name="cmfcpropertygridfontproperty"></a>CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty

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

*nazwa strName*<br/>
[w] Nazwa właściwości.

*Lf*<br/>
[w] Logiczna struktura czcionek określająca atrybuty czcionki.

*dwFontDialogSlags*<br/>
[w] Style zastosowane do okna dialogowego czcionki wyświetlanego po kliknięciu przycisku listy rozwijanej wartości właściwości. Wartością domyślną jest kombinacja bitowa (OR) CF_EFFECTS i CF_SCREENFONTS. Aby uzyskać więcej informacji, zobacz *flagi* parametr [choosefont struktury](/windows/win32/api/commdlg/ns-commdlg-choosefontw).

*lpszdescr*<br/>
[w] Opis właściwości czcionki. Wartością domyślną jest NULL.

*dwData (dane)*<br/>
[w] Dane specyficzne dla aplikacji, takie jak liczba całkowita lub wskaźnik do innych danych, które są skojarzone z właściwością. Wartość domyślna to 0.

*color*<br/>
[w] Kolor czcionki. Wartością domyślną jest kolor domyślny.

### <a name="remarks"></a>Uwagi

Obiekt `CMFCPropertyGridFontProperty` reprezentuje właściwość czcionki w formancie czcionki siatki właściwości.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, `CMFCPropertyGridFontProperty` jak skonstruować obiekt klasy. W tym przykładzie jest częścią [new controls próbki](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]

## <a name="cmfcpropertygridfontpropertygetcolor"></a><a name="getcolor"></a>CMFCPropertyGridFontWłaściwość::GetColor

Pobiera kolor czcionki wybrany przez użytkownika z okna dialogowego czcionki.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość koloru RGB reprezentująca wybrany kolor czcionki.

### <a name="remarks"></a>Uwagi

## <a name="cmfcpropertygridfontpropertygetlogfont"></a><a name="getlogfont"></a>CMFCPropertyGridFontWłaściwość::GetLogFont

Pobiera czcionkę, którą użytkownik wybiera z okna dialogowego czcionki.

```
LPLOGFONT GetLogFont();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do struktury [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) opisujący wybraną czcionkę.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[Klasa CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)
