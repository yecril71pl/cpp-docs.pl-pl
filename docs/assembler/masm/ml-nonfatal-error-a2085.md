---
title: "Błąd niekrytyczny ML A2085 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- A2085
dev_langs:
- C++
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 29d0d58e5cd65c16c848b3cc05e10b9f57488639
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="ml-nonfatal-error-a2085"></a>Błąd niekrytyczny ML A2085
**instrukcji lub rejestru nie są akceptowane w bieżącym trybie Procesora**  
  
 Nastąpiła próba użycia instrukcji, rejestru lub słowo kluczowe, która jest nieprawidłowa dla bieżącego trybu procesora.  
  
 Na przykład wymagać rejestrów 32-bitowych [.386](../../assembler/masm/dot-386.md) lub nowszej. Rejestry sterowania, takie jak CR0 wymagają trybie uprzywilejowanym [.386p —](../../assembler/masm/dot-386p.md) lub nowszej. Ten błąd zostanie również wygenerowany dla **NEAR32**, **FAR32**, i **PŁASKIEJ** słów kluczowych, które wymagają. **386** lub nowszej.  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)