---
title: "Pierwszeństwo w zasadach wnioskowania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f7374da0541fc66464947af5a7b2ea7ea7b5c1d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="precedence-in-inference-rules"></a>Pierwszeństwo w zasadach wnioskowania
Jeśli reguła wnioskowania został zdefiniowany wiele razy, NMAKE używa definicji najwyższy priorytet. Na poniższej liście przedstawiono kolejność pierwszeństwa od najwyższego do najniższego:  
  
1.  Reguła wnioskowania zdefiniowane w pliku reguł programu make; nowsze definicje mają pierwszeństwo.  
  
2.  Reguła wnioskowania zdefiniowane w Tools.ini; nowsze definicje mają pierwszeństwo.  
  
3.  Reguła wnioskowania wstępnie zdefiniowane.  
  
## <a name="see-also"></a>Zobacz też  
 [Zasady wnioskowania](../build/inference-rules.md)