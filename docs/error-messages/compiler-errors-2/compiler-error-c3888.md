---
title: "C3888 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3888
dev_langs: C++
helpviewer_keywords: C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 26e55c8a675ada3fd2e88976bc9d9a51cfa8b751
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3888"></a>C3888 błąd kompilatora
"Nazwa": wyrażenie const powiązane z tym literałem elementu członkowskiego danych nie jest obsługiwane przez C + +/ CLI  
  
 *Nazwa* element członkowski danych, która jest zadeklarowana za pomocą [literału](../../windows/literal-cpp-component-extensions.md) — słowo kluczowe jest zainicjowany z wartością kompilator nie obsługuje. Kompilator obsługuje stałej typu całkowitego, wyliczeniowego lub typu string. Prawdopodobną przyczyną **C3888** błąd jest, że element członkowski danych jest inicjowany z tablicy bajtów.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź, czy zadeklarowane literał elementu członkowskiego danych jest nieobsługiwany.  
  
## <a name="see-also"></a>Zobacz też  
 [literału](../../windows/literal-cpp-component-extensions.md)