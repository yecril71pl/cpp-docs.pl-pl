---
title: 2.6.2 konstrukcja krytyczna | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c46ecd00-b4a2-4a5e-ba92-288c329e773a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae7070fcc590307e71b0c34259bcbe1c12200550
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="262-critical-construct"></a>2.6.2 — konstrukcja krytyczna
**Krytyczne** dyrektywy identyfikuje konstrukcję ogranicza wykonywania skojarzony strukturalnego bloku do pojedynczego wątku w czasie. Składnia **krytyczne** dyrektywy wygląda następująco:  
  
```  
#pragma omp critical [(name)]  new-linestructured-block  
```  
  
 Opcjonalny *nazwa* może służyć do identyfikowania krytyczne regionu. Identyfikatory używane do identyfikowania krytyczne region mają połączenie zewnętrzne i w obszarze nazw, niezależnie od przestrzenie nazw używanych przez etykiety, tagi, członków i zwykłej identyfikatorów.  
  
 Wątek oczekuje na początku obszaru krytycznych, aż żadnego innego wątku jest wykonywany krytyczne region (w dowolnym miejscu program) o takiej samej nazwie. Wszystkie nienazwane **krytyczne** dyrektywy mapy do tej samej nazwie nieokreślony.