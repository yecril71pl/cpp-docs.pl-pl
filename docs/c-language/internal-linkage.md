---
title: Połączenie wewnętrzne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0b5703ca23a30cdb1d080e1dc379dabfc6c0df1f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="internal-linkage"></a>Połączenie wewnętrzne
Jeśli zawiera deklarację identyfikatora zakres pliku dla obiekt lub funkcji *Specyfikator klasy magazynu* **statycznych**, identyfikator ma połączenie zewnętrzne. W przeciwnym razie identyfikator ma połączenie zewnętrzne. Zobacz [klasy magazynu](../c-language/c-storage-classes.md) omówienie *Specyfikator klasy magazynu* nonterminal.  
  
 W ramach jednej jednostki tłumaczenia każde wystąpienie identyfikatora z powiązaniem wewnętrznym oznacza tego samego identyfikatora lub funkcji. Wewnętrznie połączonego identyfikatory są unikatowe w jednostce tłumaczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)