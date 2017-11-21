---
title: Klasa CMFCPropertyPage | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
dev_langs: C++
helpviewer_keywords: CMFCPropertyPage [MFC], CMFCPropertyPage
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 20f3a702ea1f98e3bd06c6dca0cfcdd4b78f1d8b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcpropertypage-class"></a>Klasa CMFCPropertyPage
`CMFCPropertyPage` Klasa obsługuje wyświetlanie menu wyskakujące na stronie właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCPropertyPage : public CPropertyPage  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCPropertyPage::CMFCPropertyPage](#cmfcpropertypage)|Konstruuje `CMFCPropertyPage` obiektu.|  
|`CMFCPropertyPage::~CMFCPropertyPage`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CMFCPropertyPage::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|`CMFCPropertyPage::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|`CMFCPropertyPage::OnSetActive`|Ta funkcja elementu członkowskiego jest wywoływana przez platformę, gdy strona jest wybierany przez użytkownika i staje się stroną aktywną. (Przesłania [CPropertyPage::OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).)|  
|`CMFCPropertyPage::PreTranslateMessage`|Wykonuje translację komunikaty okna przed wysłaniem do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) i [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkcje systemu Windows. Aby uzyskać więcej informacji i składnia metody, zobacz [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Przesłania `CPropertyPage::PreTranslateMessage`.)|  
  
## <a name="remarks"></a>Uwagi  
 `CMFCPropertyPage` Klasa reprezentuje poszczególnych stron arkusza właściwości, znanej także jako okno dialogowe kartę.  
  
 Użyj `CMFCPropertyPage` klasy razem z [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) klasy. Aby użyć menu na stronie właściwości, należy zastąpić wszystkie wystąpienia `CPropertyPage` klasy z `CMFCPropertyPage` klasy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cdialog —](../../mfc/reference/cdialog-class.md)  
  
 [Cpropertypage —](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxpropertypage.h  
  
##  <a name="cmfcpropertypage"></a>CMFCPropertyPage::CMFCPropertyPage  
 Konstruuje `CMFCPropertyPage` obiektu.  
  
```  
CMFCPropertyPage(
    UINT nIDTemplate,  
    UINT nIDCaption=0);

 
CMFCPropertyPage(
    LPCTSTR lpszTemplateName,  
    UINT nIDCaption=0);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDTemplate`  
 Identyfikator zasobu szablon dla tej strony.  
  
 `nIDCaption`  
 Identyfikator zasobu etykiety mają zostać umieszczone w karcie tej strony. W przypadku wartości 0 nazwy są uzyskiwane z szablonu okno dialogowe dla tej strony. Wartość domyślna to 0.  
  
 `lpszTemplateName`  
 Wskazuje nazwę szablonu dla tej strony. Nie może być `NULL`.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji o parametrach konstruktora, zobacz [CPropertyPage::CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage).  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)
