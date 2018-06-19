---
title: 2.6.6 konstrukcja uporządkowana | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5b3c1ba5-cfb8-4b05-865b-f446ae1c9f7c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa66d9fb8a0a9af2fc33497690bfe67a3ea5d717
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690348"
---
# <a name="266-ordered-construct"></a>2.6.6 Konstrukcja uporządkowana
Następujące strukturalnego bloku **uporządkowane** dyrektywa jest wykonywany w kolejności, w którym będzie można wykonywać iteracji w pętli sekwencyjnych. Składnia **uporządkowane** dyrektywy wygląda następująco:  
  
```  
#pragma omp ordered new-linestructured-block  
```  
  
 **Uporządkowane** dyrektywa musi być wewnątrz zakresu dynamicznego **dla** lub **równoległe w** utworzenia. **Dla** lub **równoległe w** dyrektywy, do którego **uporządkowane** wiązania konstrukcja musi mieć **uporządkowane** określony zgodnie z opisem w klauzuli [Sekcji 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) na stronie 11. Podczas wykonywania **dla** lub **równoległe w** skonstruować z **uporządkowane** klauzuli **uporządkowane** konstrukcji są wykonywane wyłącznie w kolejność, w której będzie można wykonać kolejne wykonanie pętli.  
  
 Ograniczenia **uporządkowane** dyrektywy są następujące:  
  
-   Iteracji pętli z **dla** konstrukcja nie musi wykonać dyrektywy uporządkowanej więcej niż jeden raz i nie musisz wykonać więcej niż jeden **uporządkowane** dyrektywy.