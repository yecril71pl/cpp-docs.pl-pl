---
title: Klasa CMFCToolBarComboBoxEdit
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarComboBoxEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit
helpviewer_keywords:
- CMFCToolBarComboBoxEdit [MFC], CMFCToolBarComboBoxEdit
ms.assetid: 4789c34a-ce58-48ba-a26f-38748b601352
ms.openlocfilehash: fcf89623fcde2067f2def83f1e491db015375e02
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280540"
---
# <a name="cmfctoolbarcomboboxedit-class"></a>Klasa CMFCToolBarComboBoxEdit

Środowisko wykorzystuje `CMFCToolBarComboBoxEdit` klasy w celu utworzenia przycisku paska narzędzi, który zachowuje się jak formant pola kombi do edycji.

## <a name="syntax"></a>Składnia

```
class CMFCToolBarComboBoxEdit : public CEdit
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit](#cmfctoolbarcomboboxedit)|Konstruuje `CMFCToolBarComboBoxEdit` obiektu.|
|`CMFCToolBarComboBoxEdit::~CMFCToolBarComboBoxEdit`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCToolBarComboBoxEdit::PreTranslateMessage`|Wykonuje translację komunikatów okien, zanim zostaną rozesłane do [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funkcje Windows. (Przesłania [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|

### <a name="remarks"></a>Uwagi

Wyprowadzić klasę z `CMFCToolBarComboBoxEdit` klasy, aby dostosować jego operacje edycji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtoolbarcomboboxbutton.h

##  <a name="cmfctoolbarcomboboxedit"></a>  CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit

Konstruuje `CMFCToolBarComboBoxEdit` obiektu.

```
CMFCToolBarComboBoxEdit(CMFCToolBarComboBoxButton& combo);
```

### <a name="parameters"></a>Parametry

*combo*<br/>
[in] Odwołanie do [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) obiektu, który jest przycisku paska narzędzi, który zawiera formant pola kombi.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCToolBarComboBoxEdit` klasy. Ten fragment kodu jest częścią [próbka IE Demo](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#5](../../mfc/reference/codesnippet/cpp/cmfctoolbarcomboboxedit-class_1.cpp)]

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)
