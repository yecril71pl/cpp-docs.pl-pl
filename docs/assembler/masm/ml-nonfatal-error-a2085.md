---
title: Błąd niekrytyczny ML A2085 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2085
dev_langs:
- C++
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82f0a014810679f0b48f79198b1335240f5cd6a8
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="ml-nonfatal-error-a2085"></a>Błąd niekrytyczny ML A2085
**instrukcji lub rejestru nie są akceptowane w bieżącym trybie Procesora**  
  
 Nastąpiła próba użycia instrukcji, rejestru lub słowo kluczowe, która jest nieprawidłowa dla bieżącego trybu procesora.  
  
 Na przykład wymagać rejestrów 32-bitowych [.386](../../assembler/masm/dot-386.md) lub nowszej. Rejestry sterowania, takie jak CR0 wymagają trybie uprzywilejowanym [.386p —](../../assembler/masm/dot-386p.md) lub nowszej. Ten błąd zostanie również wygenerowany dla **NEAR32**, **FAR32**, i **PŁASKIEJ** słów kluczowych, które wymagają. **386** lub nowszej.  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)