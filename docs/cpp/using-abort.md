---
title: "Użycie przerywania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Abort
dev_langs: C++
helpviewer_keywords: abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b2815a6323108422509fb706b36893ee65a6db37
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="using-abort"></a>Użycie przerywania
Wywoływanie [przerwać](../c-runtime-library/reference/abort.md) funkcja powoduje natychmiastowe przerwanie działania. Pomija się proces normalne zniszczenie zainicjowane statycznych obiektów globalnych. Również pomija specjalnego przetwarzania, która została określona za pomocą `atexit` funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodatkowe zagadnienia dotyczące kończenia](../cpp/additional-termination-considerations.md)