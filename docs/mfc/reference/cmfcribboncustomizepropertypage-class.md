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
ms.openlocfilehash: 92408e91b41b474da3a2da6ad0646feb3a6b8fc2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831843"
---
# <a name="cmfcribboncustomizepropertypage-class"></a>Klasa CMFCRibbonCustomizePropertyPage

Implementuje niestandardową stronę dla okna dialogowego **Dostosowywanie** w aplikacjach opartych na wstążki.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonCustomizePropertyPage: public CMFCPropertyPage
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|-|-|
|[CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage](#cmfcribboncustomizepropertypage)|Konstruuje `CMFCRibbonCustomizePropertyPage` obiekt.|
|`CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|-|-|
|[CMFCRibbonCustomizePropertyPage::AddCustomCategory](#addcustomcategory)|Dodaje kategorię niestandardową do pola kombi **Commands** .|
|`CMFCRibbonCustomizePropertyPage::CreateObject`|Używane przez platformę do tworzenia wystąpienia dynamicznego tego typu klasy.|
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|Używane przez platformę do uzyskania wskaźnika do obiektu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , który jest skojarzony z tym typem klasy.|
|[CMFCRibbonCustomizePropertyPage:: OnOK —](#onok)|Wywoływane przez system, gdy użytkownik kliknie przycisk **OK** w oknie dialogowym **Dostosuj** .|

## <a name="remarks"></a>Uwagi

Jeśli chcesz dodać niestandardowe polecenia do okna dialogowego **Dostosowywanie** , musisz obsłużyć AFX_WM_ON_RIBBON_CUSTOMIZE komunikat. W programie obsługi komunikatów Utwórz wystąpienie `CMFCRibbonCustomizePropertyPage` obiektu na stosie. Utwórz listę poleceń niestandardowych, a następnie Wywołaj polecenie, `AddCustomCategory` Aby dodać nową stronę do okna dialogowego **Dostosowywanie** .

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób konstruowania `CMFCRibbonCustomizePropertyPage` obiektu i dodawania kategorii niestandardowej.

[!code-cpp[NVC_MFC_RibbonApp#22](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizepropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

[CMFCRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxribboncustomizedialog. h

## <a name="cmfcribboncustomizepropertypageaddcustomcategory"></a><a name="addcustomcategory"></a> CMFCRibbonCustomizePropertyPage::AddCustomCategory

Dodaje kategorię niestandardową do pola kombi **Commands** .

```cpp
void AddCustomCategory(
    LPCTSTR lpszName,
    const CList<UINT, UINT>& lstIDS);
```

### <a name="parameters"></a>Parametry

*lpszName*\
podczas Określa niestandardową nazwę kategorii.

*lstIDS*\
podczas Zawiera identyfikatory poleceń wstążki, które mają być wyświetlane w kategorii niestandardowej.

### <a name="remarks"></a>Uwagi

Ta metoda dodaje kategorię o nazwie *lpszName* do pola kombi **Commands** . Gdy użytkownik wybierze kategorię, polecenia określone w *lstIDS* pojawiają się na liście poleceń.

## <a name="cmfcribboncustomizepropertypagecmfcribboncustomizepropertypage"></a><a name="cmfcribboncustomizepropertypage"></a> CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage

Konstruuje `CMFCRibbonCustomizePropertyPage` obiekt.

```
CMFCRibbonCustomizePropertyPage(CMFCRibbonBar* pRibbonBar = NULL);
```

### <a name="parameters"></a>Parametry

*pRibbonBar*<br/>
podczas Wskaźnik do kontrolki wstążki, dla której można dostosować opcje.

## <a name="cmfcribboncustomizepropertypageonok"></a><a name="onok"></a> CMFCRibbonCustomizePropertyPage:: OnOK —

Calleld przez system, gdy użytkownik kliknie przycisk **OK** w oknie dialogowym **Dostosuj** .

```
virtual void OnOK();
```

### <a name="remarks"></a>Uwagi

Implementacja domyślna stosuje opcje wybrane w oknie dialogowym **Dostosuj** do paska narzędzi Szybki dostęp.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
