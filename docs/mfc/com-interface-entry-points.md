---
title: Punkty wejścia interfejsu COM | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- entry points, COM interfaces
- state management, OLE/COM interfaces
- MFC COM, COM interface entry points
- OLE, interface entry points
- MFC, managing state data
- COM interfaces, entry points
ms.assetid: 9e7421dc-0731-4748-9e1b-90acbaf26d77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 699c6e3dbe5ecd95c947c13374a2e7964307ff79
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040014"
---
# <a name="com-interface-entry-points"></a>Punkty wejścia interfejsu COM
W przypadku funkcji składowych interfejsu COM, użyj [METHOD_PROLOGUE](com-interface-entry-points.md#method_prologue) makra, aby zachować stan globalny odpowiednie podczas wywoływania metody z wyeksportowanego interfejsu.  
  
 Zazwyczaj, funkcje składowe interfejsy implementowane przez `CCmdTarget`-obiektów pochodnych już Użyj tego makra w celu zapewnienia automatycznego inicjowania `pThis` wskaźnika. Na przykład:  
  
 [!code-cpp[NVC_MFCConnectionPoints#5](../mfc/codesnippet/cpp/com-interface-entry-points_1.cpp)]  
  
 Aby uzyskać więcej informacji, zobacz [techniczne 38 Uwaga](../mfc/tn038-mfc-ole-iunknown-implementation.md) na MFC/OLE `IUnknown` implementacji.  
  
 `METHOD_PROLOGUE` — Makro jest zdefiniowany jako:  
  
```cpp
#define METHOD_PROLOGUE(theClass, localClass) \
    theClass* pThis = \
    ((theClass*)((BYTE*)this - offsetof(theClass, m_x##localClass))); \
    AFX_MANAGE_STATE(pThis->m_pModuleState) \

```
  
 Część związane z zarządzaniem stanu globalnego makro jest:  
  
 `AFX_MANAGE_STATE( pThis->m_pModuleState )`  
  
 W tym wyrażeniu *m_pModuleState* będzie traktowana jako zmienną składową krawędzi zawierającego go obiektu. Jest implementowana przez `CCmdTarget` klasy bazowej i jest inicjowana na odpowiednią wartość przez `COleObjectFactory`, podczas tworzenia wystąpienia obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie danymi stanu modułów MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

