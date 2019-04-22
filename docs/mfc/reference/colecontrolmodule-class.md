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
ms.openlocfilehash: f6d486c7bacb897d70d85414ac3d0bd0d13e447b
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58780291"
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

[CWinApp](../../mfc/reference/cwinapp-class.md)

`COleControlModule`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxctl.h

## <a name="see-also"></a>Zobacz także

[Próbki MFC TESTHELP](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
