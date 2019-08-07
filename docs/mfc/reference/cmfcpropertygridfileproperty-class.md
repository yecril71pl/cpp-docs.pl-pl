---
title: Klasa CMFCPropertyGridFileProperty
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty
helpviewer_keywords:
- CMFCPropertyGridFileProperty [MFC], CMFCPropertyGridFileProperty
ms.assetid: 2bb8b8b4-47fc-4798-bd5e-dc8ea0b4cd9d
ms.openlocfilehash: 4b64d18a67ea499c202b81481684227200846483
ms.sourcegitcommit: c3bf94210bdb73be80527166264d49e33784152c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821279"
---
# <a name="cmfcpropertygridfileproperty-class"></a>Klasa CMFCPropertyGridFileProperty

`CMFCPropertyGridFileProperty` Klasa obsługuje element formantu listy właściwości, który otwiera okno dialogowe wyboru pliku.

## <a name="syntax"></a>Składnia

```
class CMFCPropertyGridFileProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty](#cmfcpropertygridfileproperty)|Konstruuje `CMFCPropertyGridFileProperty` obiekt.|
|`CMFCPropertyGridFileProperty::~CMFCPropertyGridFileProperty`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCPropertyGridFileProperty::GetThisClass`|Używane przez platformę do uzyskania wskaźnika do obiektu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , który jest skojarzony z tym typem klasy.|
|`CMFCPropertyGridFileProperty::OnClickButton`|(Przesłania [CMFCPropertyGridProperty:: OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

### <a name="remarks"></a>Uwagi

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxpropertygridctrl. h

##  <a name="cmfcpropertygridfileproperty"></a>CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty

Konstruuje `CMFCPropertyGridFileProperty` obiekt.

```
CMFCPropertyGridFileProperty(
    const CString& strName,
    BOOL bOpenFileDialog,
    const CString& strFileName,
    LPCTSTR lpszDefExt=NULL,
    DWORD dwFlags=OFN_HIDEREADONLY|OFN_OVERWRITEPROMPT,
    LPCTSTR lpszFilter=NULL,
    LPCTSTR lpszDescr=NULL,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Parametry

*strName*<br/>
podczas Nazwa właściwości.

*bOpenFileDialog*<br/>
podczas Wartość TRUE, aby otworzyć okno dialogowe **Otwórz plik** ; Wartość FALSE, aby otworzyć okno dialogowe **Zapisz plik** .

*strFileName*<br/>
podczas Początkowa nazwa pliku.

*lpszDefExt*<br/>
podczas Ciąg składający się z co najmniej jednego rozszerzenia nazwy pliku. Wartość domyślna to NULL.

*flagiDW*<br/>
podczas Flagi okna dialogowego. Wartość domyślna to kombinacja bitowa (lub) OFN_HIDEREADONLY i OFN_OVERWRITEPROMPT.

*lpszFilter*<br/>
podczas Ciąg co najmniej jednego filtru plików. Wartość domyślna to NULL.

*lpszDescr*<br/>
podczas Opis elementu właściwości. Wartość domyślna to NULL.

*dwData*<br/>
podczas Dane specyficzne dla aplikacji, które są skojarzone z elementem właściwości. Na przykład 32-bitowa liczba całkowita lub wskaźnik do innych danych. Wartość domyślna to 0.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Pełną listę dostępnych flag można znaleźć w temacie [OPENFILENAME Structure](/windows/win32/api/commdlg/ns-commdlg-openfilenamew).

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób tworzenia obiektu przy użyciu konstruktora `CMFCPropertyGridFileProperty` klasy. Ten przykład jest częścią [przykładu demonstracyjnego Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#22](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[Klasa CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)
