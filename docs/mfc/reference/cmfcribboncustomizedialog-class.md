---
title: Klasa CMFCRibbonCustomizeDialog
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog
helpviewer_keywords:
- CMFCRibbonCustomizeDialog [MFC], CMFCRibbonCustomizeDialog
ms.assetid: ce67de7f-5eaa-4c75-9b94-f290f36df073
ms.openlocfilehash: d73fd05a775ac26f5d289a5233341102f40e9af3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260000"
---
# <a name="cmfcribboncustomizedialog-class"></a>Klasa CMFCRibbonCustomizeDialog

Wyświetla wstążki **Dostosuj** strony.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonCustomizeDialog : public CMFCPropertySheet
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog](#cmfcribboncustomizedialog)|Konstruuje `CMFCRibbonCustomizeDialog` obiektu.|
|`CMFCRibbonCustomizeDialog::~CMFCRibbonCustomizeDialog`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCRibbonCustomizeDialog::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|

## <a name="remarks"></a>Uwagi

MFC tworzy wystąpienie tej klasy automatycznie, jeśli nie przetwarzają komunikatów AFX_WM_ON_RIBBON_CUSTOMIZE lub zwracają 0 z obsługi wiadomości.

Jeśli chcesz użyć tej klasy w aplikacji do wyświetlenia na wstążce **Dostosuj** okna dialogowego pole, po prostu tworzenia jego instancji i wywołania `DoModal` metody.

Ponieważ ta klasa jest pochodną [klasa CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md), można dodać niestandardowe strony za pomocą `CMFCPropertySheet` interfejsu API.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

[CMFCRibbonCustomizeDialog](../../mfc/reference/cmfcribboncustomizedialog-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxribboncustomizedialog.h

##  <a name="cmfcribboncustomizedialog"></a>  CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog

Konstruuje `CMFCRibbonCustomizeDialog` obiektu.

```
CMFCRibbonCustomizeDialog(
    CWnd* pWndParent,
    CMFCRibbonBar* pRibbon);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[in] Wskaźnik do nadrzędnego okna (zazwyczaj głównej ramki).

*pRibbon*<br/>
[in] Wskaźnik do `CMFCRibbonBar` który ma zostać dostosowana.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano sposób tworzenia `CMFCRibbonCustomizeDialog` obiektu.

[!code-cpp[NVC_MFC_RibbonApp#18](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizedialog-class_1.cpp)]

### <a name="remarks"></a>Uwagi

Tworzy konstruktora [klasa CMFCRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md) obiektu i dodaje go do kolekcji strony arkusza właściwości.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
