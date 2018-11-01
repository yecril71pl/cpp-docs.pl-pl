---
title: Obsługa interfejsów IDispatch i IErrorInfo
ms.date: 11/04/2016
f1_keywords:
- IErrorInfo
- IDispatch
helpviewer_keywords:
- ISupportErrorInfoImpl method
- IErrorInfo class suppor in ATL
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 7db2220f-319d-4ce9-9382-d340019f14f7
ms.openlocfilehash: ea45f0bdd2363f4392baee049629c55259e45af0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502439"
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>Obsługa interfejsów IDispatch i IErrorInfo

Można użyć klasy szablonu [IDispatchImpl](../atl/reference/idispatchimpl-class.md) zapewnienie domyślną implementację elementu `IDispatch Interface` część wszelkie dwa interfejsy na obiekcie.

Jeśli obiekt korzysta `IErrorInfo` interfejsu do zgłaszania błędów z powrotem do klienta, a następnie obiektu musi obsługiwać `ISupportErrorInfo Interface` interfejsu. Klasa szablonu [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) zapewnia łatwy sposób implementacji, jeśli masz tylko jeden interfejs, który generuje błędy na obiekcie.

## <a name="see-also"></a>Zobacz też

[Podstawowe informacje na temat obiektów COM ATL](../atl/fundamentals-of-atl-com-objects.md)

