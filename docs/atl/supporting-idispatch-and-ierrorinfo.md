---
title: Obsługa interfejsów IDispatch i IErrorInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- IErrorInfo
- IDispatch
dev_langs:
- C++
helpviewer_keywords:
- ISupportErrorInfoImpl method
- IErrorInfo class suppor in ATL
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 7db2220f-319d-4ce9-9382-d340019f14f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d9c27dfe81c3bbd2978f418c8e942ac20190b30
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753611"
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>Obsługa interfejsów IDispatch i IErrorInfo

Można użyć klasy szablonu [IDispatchImpl](../atl/reference/idispatchimpl-class.md) zapewnienie domyślną implementację elementu `IDispatch Interface` część wszelkie dwa interfejsy na obiekcie.

Jeśli obiekt korzysta `IErrorInfo` interfejsu do zgłaszania błędów z powrotem do klienta, a następnie obiektu musi obsługiwać `ISupportErrorInfo Interface` interfejsu. Klasa szablonu [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) zapewnia łatwy sposób implementacji, jeśli masz tylko jeden interfejs, który generuje błędy na obiekcie.

## <a name="see-also"></a>Zobacz też

[Podstawowe informacje na temat obiektów COM ATL](../atl/fundamentals-of-atl-com-objects.md)

