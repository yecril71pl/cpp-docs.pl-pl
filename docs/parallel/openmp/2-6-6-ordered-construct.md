---
title: "2.6.6 konstrukcja uporządkowana | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 5b3c1ba5-cfb8-4b05-865b-f446ae1c9f7c
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 690db7cbc03e9aa9a3b4780dd2b115812c31f984
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="266-ordered-construct"></a>2.6.6 Konstrukcja uporządkowana
Następujące strukturalnego bloku **uporządkowane** dyrektywa jest wykonywany w kolejności, w którym będzie można wykonywać iteracji w pętli sekwencyjnych. Składnia **uporządkowane** dyrektywy wygląda następująco:  
  
```  
#pragma omp ordered new-linestructured-block  
```  
  
 **Uporządkowane** dyrektywa musi być wewnątrz zakresu dynamicznego **dla** lub **równoległe w** utworzenia. **Dla** lub **równoległe w** dyrektywy, do którego **uporządkowane** wiązania konstrukcja musi mieć **uporządkowane** określony zgodnie z opisem w klauzuli [Sekcji 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) na stronie 11. Podczas wykonywania **dla** lub **równoległe w** skonstruować z **uporządkowane** klauzuli **uporządkowane** konstrukcji są wykonywane wyłącznie w kolejność, w której będzie można wykonać kolejne wykonanie pętli.  
  
 Ograniczenia **uporządkowane** dyrektywy są następujące:  
  
-   Iteracji pętli z **dla** konstrukcja nie musi wykonać dyrektywy uporządkowanej więcej niż jeden raz i nie musisz wykonać więcej niż jeden **uporządkowane** dyrektywy.