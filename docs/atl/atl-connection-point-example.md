---
title: Przykład punktu połączenia ATL
ms.date: 11/04/2016
helpviewer_keywords:
- connection points [C++], examples
- examples [ATL]
ms.assetid: a49721b7-f308-43de-8868-f662a94bc81a
ms.openlocfilehash: 3113637a3f777a56bc0b0994203ce709fbc189d5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265070"
---
# <a name="atl-connection-point-example"></a>Przykład punktu połączenia ATL

W tym przykładzie zawiera obiekt, który obsługuje [ipropertynotifysink —](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) jako interfejsu wychodzącego:

[!code-cpp[NVC_ATL_Windowing#84](../atl/codesnippet/cpp/atl-connection-point-example_1.h)]

Podczas określania `IPropertyNotifySink` interfejsu wychodzącego, można użyć klasy [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) zamiast `IConnectionPointImpl`. Na przykład:

[!code-cpp[NVC_ATL_Windowing#85](../atl/codesnippet/cpp/atl-connection-point-example_2.h)]

## <a name="see-also"></a>Zobacz także

[Punkt połączenia](../atl/atl-connection-points.md)
