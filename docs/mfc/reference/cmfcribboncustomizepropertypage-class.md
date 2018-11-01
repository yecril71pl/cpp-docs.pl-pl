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
ms.openlocfilehash: f667310208d88dff39364de480309b4bfea71d16
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648087"
---
# <a name="cmfcribboncustomizepropertypage-class"></a>Klasa CMFCRibbonCustomizePropertyPage

Implementuje niestandardowy strona **Dostosuj** okno dialogowe w aplikacjach opartych na Wstążce.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonCustomizePropertyPage: public CMFCPropertyPage
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage](#cmfcribboncustomizepropertypage)|Konstruuje `CMFCRibbonCustomizePropertyPage` obiektu.|
|`CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|||
|-|-|
|Nazwa|Opis|
|[CMFCRibbonCustomizePropertyPage::AddCustomCategory](#addcustomcategory)|Dodaje kategorię niestandardową do **polecenia** pola kombi.|
|`CMFCRibbonCustomizePropertyPage::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|
|[CMFCRibbonCustomizePropertyPage::OnOK](#onok)|Wywoływane przez system, gdy użytkownik kliknie **OK** na **Dostosuj** okno dialogowe.|

## <a name="remarks"></a>Uwagi

Jeśli chcesz dodać niestandardowe polecenia do **Dostosuj** okno dialogowe musi obsłużyć komunikat AFX_WM_ON_RIBBON_CUSTOMIZE. Programu obsługi wiadomości, utworzenia wystąpienia `CMFCRibbonCustomizePropertyPage` obiektów na stosie. Utwórz listę poleceń niestandardowych, a następnie wywołaj `AddCustomCategory` można dodać nowej strony do **Dostosuj** okno dialogowe.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano sposób tworzenia `CMFCRibbonCustomizePropertyPage` obiektu i dodać kategorię niestandardową.

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

**Nagłówek:** afxribboncustomizedialog.h

##  <a name="addcustomcategory"></a>  CMFCRibbonCustomizePropertyPage::AddCustomCategory

Dodaje kategorię niestandardową do **polecenia** pola kombi.

```
void AddCustomCategory(
    LPCTSTR lpszName,
    const CList<UINT, UINT>& lstIDS);
```

### <a name="parameters"></a>Parametry

|||
|-|-|
|Parametr|Opis|
|*lpszName*|[in] Określa nazwę kategorię niestandardową.|
|*lstIDS*|[in] Zawiera polecenie wstążki identyfikatorów mają być wyświetlane w kategorii niestandardowej.|

### <a name="remarks"></a>Uwagi

Metoda ta umożliwia dodanie do kategorii o nazwie *lpszName* do **polecenia** pola kombi. Po wybraniu kategorii polecenia określone w *lstIDS* pojawiają się na liście poleceń.

##  <a name="cmfcribboncustomizepropertypage"></a>  CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage

Konstruuje `CMFCRibbonCustomizePropertyPage` obiektu.

```
CMFCRibbonCustomizePropertyPage(CMFCRibbonBar* pRibbonBar = NULL);
```

### <a name="parameters"></a>Parametry

*pRibbonBar*<br/>
[in] Wskaźnik do formantu wstążki, dla której opcji, aby dostosować.

##  <a name="onok"></a>  CMFCRibbonCustomizePropertyPage::OnOK

Calleld przez system, gdy użytkownik kliknie **OK** na **Dostosuj** okno dialogowe.

```
virtual void OnOK();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja stosuje opcje wybrane w **Dostosuj** okno dialogowe do paska narzędzi Szybki dostęp.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
