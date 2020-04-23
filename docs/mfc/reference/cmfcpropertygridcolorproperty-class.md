---
title: Klasa CMFCPropertyGridColorProperty
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableAutomaticButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableOtherButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColumnsNumber
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetOriginalValue
helpviewer_keywords:
- CMFCPropertyGridColorProperty [MFC], CMFCPropertyGridColorProperty
- CMFCPropertyGridColorProperty [MFC], EnableAutomaticButton
- CMFCPropertyGridColorProperty [MFC], EnableOtherButton
- CMFCPropertyGridColorProperty [MFC], GetColor
- CMFCPropertyGridColorProperty [MFC], SetColor
- CMFCPropertyGridColorProperty [MFC], SetColumnsNumber
- CMFCPropertyGridColorProperty [MFC], SetOriginalValue
ms.assetid: af37be93-a91e-40a2-9a65-0f3412c6f0f8
ms.openlocfilehash: 393a871a881aa4bddd786b1d4333e02d5e0dbef1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751826"
---
# <a name="cmfcpropertygridcolorproperty-class"></a>Klasa CMFCPropertyGridColorProperty

Klasa `CMFCPropertyGridColorProperty` obsługuje element kontroli listy właściwości, który otwiera okno dialogowe wyboru kolorów.

## <a name="syntax"></a>Składnia

```
class CMFCPropertyGridColorProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty](#cmfcpropertygridcolorproperty)|Konstruuje `CMFCPropertyGridColorProperty` obiekt.|
|`CMFCPropertyGridColorProperty::~CMFCPropertyGridColorProperty`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCPropertyGridColorProperty::EnableAutomaticButton](#enableautomaticbutton)|Włącza *przycisk automatyczny* w oknie dialogowym wyboru kolorów. (Standardowy przycisk automatyczny jest oznaczony jako **Automatyczny).**|
|[CMFCPropertyGridColorProperty::EnableOtherButton](#enableotherbutton)|Włącza *drugi* przycisk w oknie dialogowym wyboru kolorów. (Standardowy drugi przycisk jest oznaczony jako **Więcej kolorów).)**|
|`CMFCPropertyGridColorProperty::FormatProperty`|Formatuje tekstową reprezentację wartości właściwości. (Zastępuje [właściwości CMFCPropertyGridProperty::FormatProperty.)](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty)|
|[CMFCPropertyGridColorProperty::GetColor](#getcolor)|Pobiera bieżący kolor właściwości.|
|`CMFCPropertyGridColorProperty::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|`CMFCPropertyGridColorProperty::OnClickButton`|Wywoływane przez strukturę, gdy użytkownik kliknie przycisk, który jest zawarty w właściwości. (Zastępuje [właściwości CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|
|`CMFCPropertyGridColorProperty::OnDrawValue`|Wywoływana przez strukturę do wyświetlania wartości właściwości. (Zastępuje [właściwości CMFCPropertyGridProperty::OnDrawValue.)](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawvalue)|
|`CMFCPropertyGridColorProperty::OnEdit`|Wywoływane przez platformę, gdy użytkownik ma zamiar zmodyfikować wartość właściwości. (Zastępuje [właściwości CMFCPropertyGridProperty::OnEdit.)](../../mfc/reference/cmfcpropertygridproperty-class.md#onedit)|
|`CMFCPropertyGridColorProperty::OnUpdateValue`|Wywoływana przez strukturę, gdy wartość edytowalnej właściwości uległa zmianie. (Zastępuje [właściwości CMFCPropertyGridProperty::OnUpdateValue](../../mfc/reference/cmfcpropertygridproperty-class.md#onupdatevalue).)|
|[CMFCPropertyGridColorProperty::SetColor](#setcolor)|Ustawia nowy kolor właściwości.|
|[CMFCPropertyGridColorProperty::SetColumnsNumber](#setcolumnsnumber)|Określa liczbę kolumn w bieżącej siatce właściwości koloru.|
|[CMFCPropertyGridColorProperty::SetOriginalValue](#setoriginalvalue)|Ustawia oryginalną wartość właściwości edytowalnej.|

## <a name="remarks"></a>Uwagi

Klasa `CMFCPropertyGridColorProperty` obsługuje właściwość color, która może być dodana do formantu listy właściwości. Aby uzyskać więcej informacji, zobacz [CMFCPropertyGridCtrl Klasy](../../mfc/reference/cmfcpropertygridctrl-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCPropertyGridColorProperty` skonstruować obiekt klasy i skonfigurować `CMFCPropertyGridColorProperty` ten obiekt przy użyciu różnych metod klasy. Kod wyjaśnia, jak włączyć automatyczne i inne przyciski oraz jak ustawić kolor i numer kolumn. W tym przykładzie jest częścią [new controls próbki](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#13](../../mfc/reference/codesnippet/cpp/cmfcpropertygridcolorproperty-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridColorProperty](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxpropertygridctrl.h

## <a name="cmfcpropertygridcolorpropertycmfcpropertygridcolorproperty"></a><a name="cmfcpropertygridcolorproperty"></a>CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty

Konstruuje `CMFCPropertyGridColorProperty` obiekt.

```
CMFCPropertyGridColorProperty(
    const CString& strName,
    const COLORREF& color,
    CPalette* pPalette = NULL,
    LPCTSTR lpszDescr = NULL,
    DWORD_PTR dwData = 0);
```

### <a name="parameters"></a>Parametry

*nazwa strName*<br/>
[w] Nazwa właściwości.

*color*<br/>
[w] Wartość koloru właściwości.

*pPalette (ppalette)*<br/>
[w] Wskaźnik do palety kolorów. Wartością domyślną jest NULL.

*lpszdescr*<br/>
[w] Opis właściwości. Wartością domyślną jest NULL.

*dwData (dane)*<br/>
[w] Dane specyficzne dla aplikacji, takie jak liczba całkowita lub wskaźnik do innych danych, które są skojarzone z właściwością. Wartość domyślna to 0.

## <a name="cmfcpropertygridcolorpropertyenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCPropertyGridColorProperty::EnableAutomaticButton

Włącza *przycisk automatyczny* w oknie dialogowym wyboru kolorów. (Standardowy przycisk automatyczny jest oznaczony jako **Automatyczny).**

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel (lpszLabel)*<br/>
[w] Tekst etykiety przycisku automatycznego.

*kolorAutomatyczny*<br/>
[w] Wartość koloru RGB koloru automatycznego (domyślnego).

*bWłaszą*<br/>
[w] PRAWDA, aby włączyć przycisk automatyczny; w przeciwnym razie FALSE. Wartością domyślną jest PRAWDA.

### <a name="remarks"></a>Uwagi

## <a name="cmfcpropertygridcolorpropertyenableotherbutton"></a><a name="enableotherbutton"></a>CMFCPropertyGridColorProperty::EnableOtherButton

Włącza *drugi* przycisk w oknie dialogowym wyboru kolorów. (Standardowy drugi przycisk jest oznaczony jako **Więcej kolorów).)**

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg = TRUE,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel (lpszLabel)*<br/>
[w] Tekst etykiety drugiego przycisku.

*bAltColorDlg*<br/>
[w] PRAWDA, aby `CMFCColorDialog` wyświetlić okno dialogowe; FAŁSZ, aby wyświetlić okno dialogowe standardowego wyboru kolorów. Wartością domyślną jest PRAWDA.

*bWłaszą*<br/>
[w] PRAWDA, aby wyświetlić drugi przycisk; w przeciwnym razie FALSE.  Wartością domyślną jest PRAWDA.

### <a name="remarks"></a>Uwagi

## <a name="cmfcpropertygridcolorpropertygetcolor"></a><a name="getcolor"></a>CMFCPropertyGridColorProperty::GetColor

Pobiera bieżący kolor właściwości.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość koloru RGB.

### <a name="remarks"></a>Uwagi

## <a name="cmfcpropertygridcolorpropertysetcolor"></a><a name="setcolor"></a>CMFCPropertyGridColorProperty::SetColor

Ustawia nowy kolor właściwości.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[w] Wartość koloru RGB.

### <a name="remarks"></a>Uwagi

## <a name="cmfcpropertygridcolorpropertysetcolumnsnumber"></a><a name="setcolumnsnumber"></a>CMFCPropertyGridColorProperty::SetColumnsNumber

Określa liczbę kolumn w bieżącej siatce właściwości koloru.

```cpp
void SetColumnsNumber(int nColumnsNumber);
```

### <a name="parameters"></a>Parametry

*nColumnsNumber*<br/>
[w] Preferowana liczba kolumn w siatce właściwości koloru.

### <a name="remarks"></a>Uwagi

Ta metoda ustawia wartość `m_nColumnsNumber` chronionego elementu członkowskiego danych.

## <a name="cmfcpropertygridcolorpropertysetoriginalvalue"></a><a name="setoriginalvalue"></a>CMFCPropertyGridColorProperty::SetOriginalValue

Ustawia oryginalną wartość właściwości edytowalnej.

```
virtual void SetOriginalValue(const COleVariant& varValue);
```

### <a name="parameters"></a>Parametry

*wartość varValue*<br/>
[w] Wartość.

### <a name="remarks"></a>Uwagi

Użyj [CMFCPropertyGridProperty::ResetOriginalValue](../../mfc/reference/cmfcpropertygridproperty-class.md#resetoriginalvalue) metody, aby zresetować oryginalną wartość edytowanej właściwości.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[Klasa CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)
