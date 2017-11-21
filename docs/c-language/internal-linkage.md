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
ms.openlocfilehash: d54a7efdf80d9f1ee26d6954cca7f4e6efe8f71f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="internal-linkage"></a>Połączenie wewnętrzne
Jeśli zawiera deklarację identyfikatora zakres pliku dla obiekt lub funkcji *Specyfikator klasy magazynu* **statycznych**, identyfikator ma połączenie zewnętrzne. W przeciwnym razie identyfikator ma połączenie zewnętrzne. Zobacz [klasy magazynu](../c-language/c-storage-classes.md) omówienie *Specyfikator klasy magazynu* nonterminal.  
  
 W ramach jednej jednostki tłumaczenia każde wystąpienie identyfikatora z powiązaniem wewnętrznym oznacza tego samego identyfikatora lub funkcji. Wewnętrznie połączonego identyfikatory są unikatowe w jednostce tłumaczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)