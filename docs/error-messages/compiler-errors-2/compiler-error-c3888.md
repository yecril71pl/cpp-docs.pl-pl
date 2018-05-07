---
title: C3888 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3888
dev_langs:
- C++
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c11c897f35a6c395c4bc6ee6a64be51fa810911b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3888"></a>C3888 błąd kompilatora
"Nazwa": wyrażenie const powiązane z tym literałem elementu członkowskiego danych nie jest obsługiwane przez C + +/ CLI  
  
 *Nazwa* element członkowski danych, która jest zadeklarowana za pomocą [literału](../../windows/literal-cpp-component-extensions.md) — słowo kluczowe jest zainicjowany z wartością kompilator nie obsługuje. Kompilator obsługuje stałej typu całkowitego, wyliczeniowego lub typu string. Prawdopodobną przyczyną **C3888** błąd jest, że element członkowski danych jest inicjowany z tablicy bajtów.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź, czy zadeklarowane literał elementu członkowskiego danych jest nieobsługiwany.  
  
## <a name="see-also"></a>Zobacz też  
 [Literału](../../windows/literal-cpp-component-extensions.md)