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
ms.openlocfilehash: 132dd7394119081dcaeb098c2088782ff5d40ae4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619340"
---
# <a name="com-interface-entry-points"></a>Punkty wejścia interfejsu COM

W przypadku funkcji Członkowskich interfejsu COM, użyj makra, `METHOD_PROLOGUE` Aby zachować właściwy stan globalny podczas wywoływania metod wyeksportowanego interfejsu.

Zazwyczaj funkcje składowe interfejsów zaimplementowane przez `CCmdTarget` obiekty pochodne już używają tego makra, aby zapewnić automatyczne inicjowanie `pThis` wskaźnika. Przykład:

[!code-cpp[NVC_MFCConnectionPoints#5](codesnippet/cpp/com-interface-entry-points_1.cpp)]

Aby uzyskać dodatkowe informacje, zobacz [Uwagi techniczne 38](tn038-mfc-ole-iunknown-implementation.md) w implementacji MFC/OLE `IUnknown` .

`METHOD_PROLOGUE`Makro jest zdefiniowane jako:

```cpp
#define METHOD_PROLOGUE(theClass, localClass) \
    theClass* pThis = \
    ((theClass*)((BYTE*)this - offsetof(theClass, m_x##localClass))); \
    AFX_MANAGE_STATE(pThis->m_pModuleState) \
```

Częścią makra związanego z zarządzaniem stanem globalnym jest:

`AFX_MANAGE_STATE( pThis->m_pModuleState )`

W tym wyrażeniu przyjmuje się, że *m_pModuleState* jest zmienną członkowską zawierającego obiektu. Jest implementowana przez `CCmdTarget` klasę bazową i jest inicjowana do odpowiedniej wartości przez `COleObjectFactory` , po utworzeniu wystąpienia obiektu.

## <a name="see-also"></a>Zobacz też

[Zarządzanie danymi stanu modułów MFC](managing-the-state-data-of-mfc-modules.md)
