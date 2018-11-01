---
title: Klasa COleControlModule
ms.date: 11/04/2016
f1_keywords:
- OleControlModule
helpviewer_keywords:
- OLE control modules [MFC]
- MFC ActiveX controls [MFC], OLE control modules
- COleControlModule class [MFC]
- control modules [MFC]
ms.assetid: 0721724d-d4af-4eda-ad34-5a2b27810dd4
ms.openlocfilehash: a2480407ddb9f937b0691f3e07103eb159fea8b6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556393"
---
# <a name="colecontrolmodule-class"></a>Klasa COleControlModule

Klasa bazowa, z której pochodzi obiekt modułu sterowania OLE.

## <a name="syntax"></a>Składnia

```
class COleControlModule : public CWinApp
```

## <a name="remarks"></a>Uwagi

Ta klasa dostarcza funkcji elementów członkowskich do inicjowania modułu sterowania. Każdy moduł sterowania OLE, który korzysta z klas Microsoft Foundation może zawierać tylko jeden obiekt pochodzący od `COleControlModule`. Ten obiekt jest tworzony, gdy inne obiekty globalne w C++ są konstruowane. Zadeklaruj swoje pochodnej `COleControlModule` obiektów na poziomie globalnym.

Aby uzyskać więcej informacji na temat korzystania z `COleControlModule` klasy, zobacz [CWinApp](../../mfc/reference/cwinapp-class.md) klasy i artykuł [formantów ActiveX](../../mfc/mfc-activex-controls.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWinThread](../../mfc/reference/cwinthread-class.md)

[Klasa CWinApp](../../mfc/reference/cwinapp-class.md)

`COleControlModule`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxctl.h

## <a name="see-also"></a>Zobacz też

[Próbki MFC TESTHELP](../../visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)

