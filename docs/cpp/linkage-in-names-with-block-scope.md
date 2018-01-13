---
title: "Połączenia nazw z zasięgiem bloku | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- scope [C++], linkage rules
- linkage [C++], scope linkage rules
- names [C++], scope linkage rules
- block scope [C++]
- external linkage, scope linkage rules
ms.assetid: 73efa91a-f761-47f7-bbd9-9f9e3508e218
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fed200614ef6385aab24755e5eb202fd875494c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linkage-in-names-with-block-scope"></a>Połączenia nazw z zasięgiem bloku
Mają zastosowanie następujące reguły połączenia nazw z zasięgiem bloku (lokalnych nazw):  
  
-   Nazwy zadeklarowany jako `extern` ma połączenie zewnętrzne, chyba że zostały one wcześniej zadeklarowany jako **statycznych**.  
  
-   Innych nazw z zasięgiem bloku ma bez połączenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Program i połączenie](../cpp/program-and-linkage-cpp.md)