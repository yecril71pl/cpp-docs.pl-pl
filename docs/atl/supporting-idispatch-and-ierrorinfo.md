---
title: Obsługa interfejsów IDispatch i IErrorInfo
ms.date: 11/04/2016
helpviewer_keywords:
- ISupportErrorInfoImpl method
- IErrorInfo class suppor in ATL
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 7db2220f-319d-4ce9-9382-d340019f14f7
ms.openlocfilehash: 2dcebd215ff5e1bdf72323323dfbaebd16fa3403
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807419"
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>Obsługa interfejsów IDispatch i IErrorInfo

Można użyć klasy szablonu [IDispatchImpl](../atl/reference/idispatchimpl-class.md) zapewnienie domyślną implementację elementu `IDispatch Interface` część wszelkie dwa interfejsy na obiekcie.

Jeśli obiekt korzysta `IErrorInfo` interfejsu do zgłaszania błędów z powrotem do klienta, a następnie obiektu musi obsługiwać `ISupportErrorInfo Interface` interfejsu. Klasa szablonu [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) zapewnia łatwy sposób implementacji, jeśli masz tylko jeden interfejs, który generuje błędy na obiekcie.

## <a name="see-also"></a>Zobacz także

[Podstawowe informacje na temat obiektów COM ATL](../atl/fundamentals-of-atl-com-objects.md)
