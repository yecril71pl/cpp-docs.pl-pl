---
title: "Obsługa interfejsu IDispatch i IErrorInfo | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f39db3e844df884e8e95352bed2a078b01beede8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>Obsługa interfejsu IDispatch i IErrorInfo
Można użyć klasy szablonu [elementem IDispatchImpl](../atl/reference/idispatchimpl-class.md) zapewnienie domyślną implementację `IDispatch Interface` część interfejsami podwójną na obiekt.  
  
 Jeśli używa obiektu `IErrorInfo` interfejsu na zgłaszanie błędów z powrotem do klienta, a następnie obiekt musi obsługiwać `ISupportErrorInfo Interface` interfejsu. Klasy szablonów [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) zapewnia łatwy sposób wdrożyć, jeśli masz tylko jeden interfejs, który generuje błędy na obiekt.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje na temat obiektów COM ATL](../atl/fundamentals-of-atl-com-objects.md)

