---
title: Punkty wejścia interfejsu COM
ms.date: 03/27/2019
helpviewer_keywords:
- entry points, COM interfaces
- state management, OLE/COM interfaces
- MFC COM, COM interface entry points
- OLE, interface entry points
- MFC, managing state data
- COM interfaces, entry points
ms.assetid: 9e7421dc-0731-4748-9e1b-90acbaf26d77
ms.openlocfilehash: eb8fc425d6b9849f6367d9b207e5181652386be3
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2019
ms.locfileid: "58564739"
---
# <a name="com-interface-entry-points"></a>Punkty wejścia interfejsu COM

W przypadku funkcji składowych interfejsu COM, użyj `METHOD_PROLOGUE` makra, aby zachować stan globalny odpowiednie podczas wywoływania metody z wyeksportowanego interfejsu.

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

## <a name="see-also"></a>Zobacz także

[Zarządzanie danymi stanu modułów MFC](../mfc/managing-the-state-data-of-mfc-modules.md)
