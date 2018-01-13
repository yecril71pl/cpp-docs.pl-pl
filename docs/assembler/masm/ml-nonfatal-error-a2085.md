---
title: "Błąd niekrytyczny ML A2085 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A2085
dev_langs: C++
helpviewer_keywords: A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f987b775c13b0e477fd5c1d215d556069535a0fd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ml-nonfatal-error-a2085"></a>Błąd niekrytyczny ML A2085
**instrukcji lub rejestru nie są akceptowane w bieżącym trybie Procesora**  
  
 Nastąpiła próba użycia instrukcji, rejestru lub słowo kluczowe, która jest nieprawidłowa dla bieżącego trybu procesora.  
  
 Na przykład wymagać rejestrów 32-bitowych [.386](../../assembler/masm/dot-386.md) lub nowszej. Rejestry sterowania, takie jak CR0 wymagają trybie uprzywilejowanym [.386p —](../../assembler/masm/dot-386p.md) lub nowszej. Ten błąd zostanie również wygenerowany dla **NEAR32**, **FAR32**, i **PŁASKIEJ** słów kluczowych, które wymagają. **386** lub nowszej.  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)