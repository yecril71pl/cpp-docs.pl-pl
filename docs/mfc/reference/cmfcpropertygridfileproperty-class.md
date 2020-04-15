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
ms.openlocfilehash: 0ce3321968f0c29ce3b946f6127e4435b531c422
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360582"
---
# <a name="cmfcpropertygridfileproperty-class"></a>Klasa CMFCPropertyGridFileProperty

Klasa `CMFCPropertyGridFileProperty` obsługuje element kontroli listy właściwości, który otwiera okno dialogowe wyboru pliku.

## <a name="syntax"></a>Składnia

```
class CMFCPropertyGridFileProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty](#cmfcpropertygridfileproperty)|Konstruuje `CMFCPropertyGridFileProperty` obiekt.|
|`CMFCPropertyGridFileProperty::~CMFCPropertyGridFileProperty`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCPropertyGridFileProperty::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|`CMFCPropertyGridFileProperty::OnClickButton`|(Zastępuje [właściwości CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

### <a name="remarks"></a>Uwagi

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxpropertygridctrl.h

## <a name="cmfcpropertygridfilepropertycmfcpropertygridfileproperty"></a><a name="cmfcpropertygridfileproperty"></a>CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty

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

*nazwa strName*<br/>
[w] Nazwa właściwości.

*bOpenFileDialog*<br/>
[w] PRAWDA, aby otworzyć okno dialogowe **Otwórz plik;** FAŁSZ, aby otworzyć okno dialogowe **Zapisywanie pliku.**

*Strfilename*<br/>
[w] Początkowa nazwa pliku.

*lpszDefext*<br/>
[w] Ciąg jednego lub więcej rozszerzeń nazw plików. Wartością domyślną jest NULL.

*Dwflags*<br/>
[w] Flagi okna dialogowego. Wartością domyślną jest kombinacja bitowa (OR) OFN_HIDEREADONLY i OFN_OVERWRITEPROMPT.

*lpszFilter*<br/>
[w] Ciąg jednego lub więcej filtrów plików. Wartością domyślną jest NULL.

*lpszdescr*<br/>
[w] Opis elementu właściwości. Wartością domyślną jest NULL.

*dwData (dane)*<br/>
[w] Dane specyficzne dla aplikacji, który jest skojarzony z elementem właściwości. Na przykład 32-bitowa ćowiaczka całkowita lub wskaźnik do innych danych. Wartość domyślna to 0.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Aby uzyskać pełną listę dostępnych flag, zobacz [OPENFILENAME struktury](/windows/win32/api/commdlg/ns-commdlg-openfilenamew).

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak utworzyć obiekt `CMFCPropertyGridFileProperty` przy użyciu konstruktora klasy. W tym przykładzie jest częścią [przykładu demo programu Visual Studio.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_VisualStudioDemo#22](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[Klasa CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)
