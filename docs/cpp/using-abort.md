---
title: "Użycie przerywania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Abort
dev_langs:
- C++
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 88f7d2319fd238fbc7bf573d304245ca74696720
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-abort"></a>Użycie przerywania
Wywoływanie [przerwać](../c-runtime-library/reference/abort.md) funkcja powoduje natychmiastowe przerwanie działania. Pomija się proces normalne zniszczenie zainicjowane statycznych obiektów globalnych. Również pomija specjalnego przetwarzania, która została określona za pomocą `atexit` funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodatkowe zagadnienia dotyczące kończenia](../cpp/additional-termination-considerations.md)