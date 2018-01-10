---
title: Klasa CMFCToolBarComboBoxEdit | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarComboBoxEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit
dev_langs: C++
helpviewer_keywords: CMFCToolBarComboBoxEdit [MFC], CMFCToolBarComboBoxEdit
ms.assetid: 4789c34a-ce58-48ba-a26f-38748b601352
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7d7e83351c9adbf7730fad04f2e4d73431694f3c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfctoolbarcomboboxedit-class"></a>Klasa CMFCToolBarComboBoxEdit
Używa w ramach `CMFCToolBarComboBoxEdit` klasy w celu utworzenia przycisku paska narzędzi, który zachowuje się jak kontrolkę pola kombi do edycji.  
  
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
|`CMFCToolBarComboBoxEdit::PreTranslateMessage`|Wykonuje translację komunikaty okna przed wysłaniem do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) i [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkcje systemu Windows. (Przesłania [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
  
### <a name="remarks"></a>Uwagi  
 Klasa wyprowadzona z `CMFCToolBarComboBoxEdit` klasę, aby dostosować jego operacji edycji.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxtoolbarcomboboxbutton.h  
  
##  <a name="cmfctoolbarcomboboxedit"></a>CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit  
 Konstruuje `CMFCToolBarComboBoxEdit` obiektu.  
  
```  
CMFCToolBarComboBoxEdit(CMFCToolBarComboBoxButton& combo);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`combo`  
 Odwołanie do [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) obiektu, który jest przycisku paska narzędzi, który zawiera kontrolki pola kombi.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCToolBarComboBoxEdit` klasy. Następujący fragment kodu jest częścią [próbka IE Demo](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_IEDemo#5](../../mfc/reference/codesnippet/cpp/cmfctoolbarcomboboxedit-class_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)
