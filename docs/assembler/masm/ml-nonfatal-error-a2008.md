---
title: Błąd niekrytyczny ML A2008 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2008
dev_langs:
- C++
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50f7329f698d23f875a29bc316067c39e8d1b8c1
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32055222"
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