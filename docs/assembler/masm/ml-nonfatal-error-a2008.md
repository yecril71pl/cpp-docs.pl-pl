---
title: "Błąd niekrytyczny ML A2008 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- A2008
dev_langs:
- C++
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: afef8194fea15f9ebfa65201d43ddbdda2b61786
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="ml-nonfatal-error-a2008"></a>Błąd niekrytyczny ML A2008
**Błąd składni:**  
  
 Token w bieżącej lokalizacji spowodował błąd składni.  
  
 Jedną z następujących przyczyn:  
  
-   Prefiks kropka został dodany do lub pominięte dyrektywy.  
  
-   Słowa zarezerwowanego (takich jak **C** lub **rozmiar**) została użyta jako identyfikator.  
  
-   Instrukcja użyto nie jest dostępna, zachowując bieżący wybór procesora lub Koprocesor.  
  
-   Operator porównania czasu wykonywania (takich jak `==`) został użyty w instrukcji warunkowej zestawu zamiast operatora relacyjnego (takich jak [EQ](../../assembler/masm/operator-eq.md)).  
  
-   Instrukcji lub dyrektywy podano za mało argumentów operacji.  
  
-   Przestarzała dyrektywa została użyta.  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)