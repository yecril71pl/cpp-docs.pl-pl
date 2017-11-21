---
title: "Obsługa interfejsu IDispatch i IErrorInfo | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IErrorInfo
- IDispatch
dev_langs: C++
helpviewer_keywords:
- ISupportErrorInfoImpl method
- IErrorInfo class suppor in ATL
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 7db2220f-319d-4ce9-9382-d340019f14f7
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b6d34f0d0616ae3980d1132b1f70812fe273d275
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>Obsługa interfejsu IDispatch i IErrorInfo
Można użyć klasy szablonu [elementem IDispatchImpl](../atl/reference/idispatchimpl-class.md) zapewnienie domyślną implementację `IDispatch Interface` część interfejsami podwójną na obiekt.  
  
 Jeśli używa obiektu `IErrorInfo` interfejsu na zgłaszanie błędów z powrotem do klienta, a następnie obiekt musi obsługiwać `ISupportErrorInfo Interface` interfejsu. Klasy szablonów [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) zapewnia łatwy sposób wdrożyć, jeśli masz tylko jeden interfejs, który generuje błędy na obiekt.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje na temat ATL COM — obiekty](../atl/fundamentals-of-atl-com-objects.md)

