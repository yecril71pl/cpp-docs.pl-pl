---
title: Klasa CMFCRibbonCustomizePropertyPage
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::AddCustomCategory
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::OnOK
helpviewer_keywords:
- CMFCRibbonCustomizePropertyPage [MFC], CMFCRibbonCustomizePropertyPage
- CMFCRibbonCustomizePropertyPage [MFC], AddCustomCategory
- CMFCRibbonCustomizePropertyPage [MFC], OnOK
ms.assetid: ea32a99a-dfbe-401e-8975-aa191552532f
ms.openlocfilehash: 57fbd1e1f574beebff8baab014e7ab615f56333f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754177"
---
# <a name="cmfcribboncustomizepropertypage-class"></a>Klasa CMFCRibbonCustomizePropertyPage

Implementuje niestandardową stronę okna dialogowego **Dostosowywanie** w aplikacjach opartych na wstążce.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonCustomizePropertyPage: public CMFCPropertyPage
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage](#cmfcribboncustomizepropertypage)|Konstruuje `CMFCRibbonCustomizePropertyPage` obiekt.|
|`CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCRibbonCustomizePropertyPage::AddCustomCategory](#addcustomcategory)|Dodaje kategorię niestandardową do pola kombi **Polecenia.**|
|`CMFCRibbonCustomizePropertyPage::CreateObject`|Używany przez platformę do tworzenia dynamicznego wystąpienia tego typu klasy.|
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|[CMFCRibbonCustomizePropertyPage::OnOK](#onok)|Wywoływane przez system, gdy użytkownik kliknie **przycisk OK** w oknie dialogowym **Dostosowywanie.**|

## <a name="remarks"></a>Uwagi

Aby dodać polecenia niestandardowe do okna dialogowego **Dostosowywanie,** należy obsłużyć komunikat AFX_WM_ON_RIBBON_CUSTOMIZE. W programie obsługi wiadomości wystąpienia `CMFCRibbonCustomizePropertyPage` obiektu na stosie. Utwórz listę poleceń niestandardowych, `AddCustomCategory` a następnie zadzwoń, aby dodać nową stronę do okna dialogowego **Dostosowywanie.**

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak skonstruować `CMFCRibbonCustomizePropertyPage` obiekt i dodać kategorię niestandardową.

[!code-cpp[NVC_MFC_RibbonApp#22](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizepropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[Cpropertypage](../../mfc/reference/cpropertypage-class.md)

[STRONA CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

[CMFCRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxribboncustomizedialog.h

## <a name="cmfcribboncustomizepropertypageaddcustomcategory"></a><a name="addcustomcategory"></a>CMFCRibbonCustomizePropertyPage::AddCustomCategory

Dodaje kategorię niestandardową do pola kombi **Polecenia.**

```cpp
void AddCustomCategory(
    LPCTSTR lpszName,
    const CList<UINT, UINT>& lstIDS);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*Lpszname*|[w] Określa niestandardową nazwę kategorii.|
|*lstIDS (lstIDS)*|[w] Zawiera identyfikatory poleceń wstążki, które mają być wyświetlane w kategorii niestandardowej.|

### <a name="remarks"></a>Uwagi

Ta metoda dodaje kategorię o nazwie *lpszName* do pola kombi **Polecenia.** Gdy użytkownik wybierze kategorię, polecenia określone w *lstIDS* pojawiają się na liście poleceń.

## <a name="cmfcribboncustomizepropertypagecmfcribboncustomizepropertypage"></a><a name="cmfcribboncustomizepropertypage"></a>CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage

Konstruuje `CMFCRibbonCustomizePropertyPage` obiekt.

```
CMFCRibbonCustomizePropertyPage(CMFCRibbonBar* pRibbonBar = NULL);
```

### <a name="parameters"></a>Parametry

*pRibbonBar (pRibbonBar)*<br/>
[w] Wskaźnik do formantu wstążki, dla którego opcje dostosowywania.

## <a name="cmfcribboncustomizepropertypageonok"></a><a name="onok"></a>CMFCRibbonCustomizePropertyPage::OnOK

Wywołanie przez system, gdy użytkownik kliknie **przycisk OK** w oknie dialogowym **Dostosowywanie.**

```
virtual void OnOK();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja stosuje opcje wybrane w oknie dialogowym **Dostosowywanie** do paska narzędzi Szybki dostęp.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
