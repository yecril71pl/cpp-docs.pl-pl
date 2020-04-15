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
ms.openlocfilehash: a66c0a19c04e0a900b91c0c28c45bb9c766d25c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375206"
---
# <a name="cmfcribboncustomizedialog-class"></a>Klasa CMFCRibbonCustomizeDialog

Wyświetla wstążkę **Dostosuj** stronę.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonCustomizeDialog : public CMFCPropertySheet
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog](#cmfcribboncustomizedialog)|Konstruuje `CMFCRibbonCustomizeDialog` obiekt.|
|`CMFCRibbonCustomizeDialog::~CMFCRibbonCustomizeDialog`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCRibbonCustomizeDialog::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|

## <a name="remarks"></a>Uwagi

MFC automatycznie wystąpienia tej klasy, jeśli nie przetwarzają AFX_WM_ON_RIBBON_CUSTOMIZE wiadomości lub jeśli zwrócisz 0 z obsługi wiadomości.

Jeśli chcesz użyć tej klasy w aplikacji, aby wyświetlić wstążkę Dostosuj okno `DoModal` dialogowe, po prostu utworzyć **wystąpienie** i wywołać metodę.

Ponieważ ta klasa jest pochodną [CMFCPropertySheet Class](../../mfc/reference/cmfcpropertysheet-class.md), można `CMFCPropertySheet` dodać strony niestandardowe przy użyciu interfejsu API.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cpropertysheet](../../mfc/reference/cpropertysheet-class.md)

[Cmfcpropertysheet](../../mfc/reference/cmfcpropertysheet-class.md)

[CMFCRibbonCustomizeDialog](../../mfc/reference/cmfcribboncustomizedialog-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxribboncustomizedialog.h

## <a name="cmfcribboncustomizedialogcmfcribboncustomizedialog"></a><a name="cmfcribboncustomizedialog"></a>CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog

Konstruuje `CMFCRibbonCustomizeDialog` obiekt.

```
CMFCRibbonCustomizeDialog(
    CWnd* pWndParent,
    CMFCRibbonBar* pRibbon);
```

### <a name="parameters"></a>Parametry

*pWndRodziciela*<br/>
[w] Wskaźnik do okna nadrzędnego (zwykle ramki głównej).

*pRibbon ( pRibbon )*<br/>
[w] Wskaźnik do `CMFCRibbonBar` tego, który ma być dostosowany.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak skonstruować `CMFCRibbonCustomizeDialog` obiekt.

[!code-cpp[NVC_MFC_RibbonApp#18](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizedialog-class_1.cpp)]

### <a name="remarks"></a>Uwagi

Konstruktor tworzy [cmfcribbonCustomizePropertyPage Class](../../mfc/reference/cmfcribboncustomizepropertypage-class.md) obiektu i dodaje go do kolekcji stron arkusza właściwości.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
