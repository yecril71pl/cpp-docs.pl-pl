---
title: Klasa CMFCRibbonCustomizePropertyPage | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::AddCustomCategory
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::OnOK
dev_langs: C++
helpviewer_keywords:
- CMFCRibbonCustomizePropertyPage [MFC], CMFCRibbonCustomizePropertyPage
- CMFCRibbonCustomizePropertyPage [MFC], AddCustomCategory
- CMFCRibbonCustomizePropertyPage [MFC], OnOK
ms.assetid: ea32a99a-dfbe-401e-8975-aa191552532f
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2ad58cb0b062e25a52742eec5491489d3744a9ea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribboncustomizepropertypage-class"></a>Klasa CMFCRibbonCustomizePropertyPage
Implementuje niestandardowej strony dla **Dostosuj** okno dialogowe w aplikacjach opartych na Wstążce.  
  
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
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|[CMFCRibbonCustomizePropertyPage::OnOK](#onok)|Wywoływane przez system, gdy użytkownik kliknie **OK** na **Dostosuj** okno dialogowe.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli chcesz dodać niestandardowe polecenia do **Dostosuj** okno dialogowe, musi obsługiwać AFX_WM_ON_RIBBON_CUSTOMIZE wiadomości. Programu obsługi wiadomości, utworzenia wystąpienia `CMFCRibbonCustomizePropertyPage` obiektu na stosie. Utwórz listę niestandardowych poleceń, a następnie wywołać `AddCustomCategory` Aby dodać nową stronę do **Dostosuj** okno dialogowe.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia `CMFCRibbonCustomizePropertyPage` obiektu i Dodaj kategorię niestandardową.  
  
 [!code-cpp[NVC_MFC_RibbonApp#22](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizepropertypage-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cdialog —](../../mfc/reference/cdialog-class.md)  
  
 [Cpropertypage —](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)  
  
 [CMFCRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxribboncustomizedialog.h  
  
##  <a name="addcustomcategory"></a>CMFCRibbonCustomizePropertyPage::AddCustomCategory  
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
|[in]`lpszName`|Określa nazwę kategorii niestandardowej.|  
|[in]`lstIDS`|Zawiera polecenie wstążki identyfikatorów ma być wyświetlany w kategorii niestandardowej.|  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda dodaje kategorię o nazwie `lpszName` do **polecenia** pola kombi. Po wybraniu przez użytkownika kategorii, polecenia określone w `lstIDS` znajdują się na liście polecenia.  
  
##  <a name="cmfcribboncustomizepropertypage"></a>CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage  
 Konstruuje `CMFCRibbonCustomizePropertyPage` obiektu.  
  
```  
CMFCRibbonCustomizePropertyPage(CMFCRibbonBar* pRibbonBar = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pRibbonBar`  
 Wskaźnik do sterowania wstążki, dla którego opcje, aby dostosować.  
  
##  <a name="onok"></a>CMFCRibbonCustomizePropertyPage::OnOK  
 Calleld przez system, gdy użytkownik kliknie **OK** na **Dostosuj** okno dialogowe.  
  
```  
virtual void OnOK();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja stosuje opcje wybrane w **Dostosuj** okno dialogowe do paska narzędzi Szybki dostęp.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
