---
title: "Połączenie wewnętrzne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e6ca8a9e9804aa6c14077b023d0014062067f324
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="internal-linkage"></a>Połączenie wewnętrzne
Jeśli zawiera deklarację identyfikatora zakres pliku dla obiekt lub funkcji *Specyfikator klasy magazynu* **statycznych**, identyfikator ma połączenie zewnętrzne. W przeciwnym razie identyfikator ma połączenie zewnętrzne. Zobacz [klasy magazynu](../c-language/c-storage-classes.md) omówienie *Specyfikator klasy magazynu* nonterminal.  
  
 W ramach jednej jednostki tłumaczenia każde wystąpienie identyfikatora z powiązaniem wewnętrznym oznacza tego samego identyfikatora lub funkcji. Wewnętrznie połączonego identyfikatory są unikatowe w jednostce tłumaczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)