---
title: "Punkty wejścia interfejsu COM | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- entry points, COM interfaces
- state management, OLE/COM interfaces
- MFC COM, COM interface entry points
- OLE, interface entry points
- MFC, managing state data
- COM interfaces, entry points
ms.assetid: 9e7421dc-0731-4748-9e1b-90acbaf26d77
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 010df3546a6ac2b6276281c39efdd76abd5ec222
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="com-interface-entry-points"></a>Punkty wejścia interfejsu COM
Dla funkcji Członkowskich interfejsu COM, użyj [method_prologue —](com-interface-entry-points.md#method_prologue) makra w celu prawidłowego stanu globalnego podczas wywoływania metody z wyeksportowanego interfejsu.  
  
 Zwykle funkcje Członkowskie interfejsy implementowane przez `CCmdTarget`-obiekty pochodne używają już to makro aby zapewnić automatyczne inicjowanie `pThis` wskaźnika. Na przykład:  
  
 [!code-cpp[NVC_MFCConnectionPoints#5](../mfc/codesnippet/cpp/com-interface-entry-points_1.cpp)]  
  
 Aby uzyskać dodatkowe informacje, zobacz [38 Uwaga techniczna](../mfc/tn038-mfc-ole-iunknown-implementation.md) na MFC/OLE **IUnknown** implementacji.  
  
 `METHOD_PROLOGUE` Makro jest zdefiniowany jako:  
  
 `#define METHOD_PROLOGUE(theClass, localClass) \`  
  
 `theClass* pThis = \`  
  
 `((theClass*)((BYTE*)this - offsetof(theClass, m_x##localClass))); \`  
  
 `AFX_MANAGE_STATE(pThis->m_pModuleState) \`  
  
 Część związane z zarządzaniem stan globalny makro jest:  
  
 `AFX_MANAGE_STATE( pThis->m_pModuleState )`  
  
 W tym wyrażeniu *m_pModuleState* zakłada, że zmiennej członkowskiej krawędzi zawierającego go obiektu. Jest implementowany przez `CCmdTarget` klasa podstawowa i jest ustawiana na odpowiednią wartość przez `COleObjectFactory`po utworzeniu wystąpienia obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie danymi stanu modułów MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

