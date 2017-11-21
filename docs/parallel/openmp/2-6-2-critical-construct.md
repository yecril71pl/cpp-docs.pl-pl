---
title: 2.6.2 konstrukcja krytyczna | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: c46ecd00-b4a2-4a5e-ba92-288c329e773a
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 13e9b4a8611732c7dddb81be1ca6123b725f7169
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="262-critical-construct"></a>2.6.2 — konstrukcja krytyczna
**Krytyczne** dyrektywy identyfikuje konstrukcję ogranicza wykonywania skojarzony strukturalnego bloku do pojedynczego wątku w czasie. Składnia **krytyczne** dyrektywy wygląda następująco:  
  
```  
#pragma omp critical [(name)]  new-linestructured-block  
```  
  
 Opcjonalny *nazwa* może służyć do identyfikowania krytyczne regionu. Identyfikatory używane do identyfikowania krytyczne region mają połączenie zewnętrzne i w obszarze nazw, niezależnie od przestrzenie nazw używanych przez etykiety, tagi, członków i zwykłej identyfikatorów.  
  
 Wątek oczekuje na początku obszaru krytycznych, aż żadnego innego wątku jest wykonywany krytyczne region (w dowolnym miejscu program) o takiej samej nazwie. Wszystkie nienazwane **krytyczne** dyrektywy mapy do tej samej nazwie nieokreślony.