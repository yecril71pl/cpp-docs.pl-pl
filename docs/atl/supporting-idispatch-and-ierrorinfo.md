---
title: Obsługa interfejsu IDispatch i IErrorInfo | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 94f4c99da3989cce84bd5b6bd3bbfee8df97ff43
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360952"
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>Obsługa interfejsu IDispatch i IErrorInfo
Można użyć klasy szablonu [elementem IDispatchImpl](../atl/reference/idispatchimpl-class.md) zapewnienie domyślną implementację `IDispatch Interface` część interfejsami podwójną na obiekt.  
  
 Jeśli używa obiektu `IErrorInfo` interfejsu na zgłaszanie błędów z powrotem do klienta, a następnie obiekt musi obsługiwać `ISupportErrorInfo Interface` interfejsu. Klasy szablonów [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) zapewnia łatwy sposób wdrożyć, jeśli masz tylko jeden interfejs, który generuje błędy na obiekt.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje na temat obiektów COM ATL](../atl/fundamentals-of-atl-com-objects.md)

