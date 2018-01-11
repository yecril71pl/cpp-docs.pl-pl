---
title: "Kompilatora (poziom 1) ostrzeżenie C4624 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4624
dev_langs: C++
helpviewer_keywords: C4624
ms.assetid: 14f61769-d92e-482b-9515-debd87b30a66
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2a3acf93e1609b6a53f6654afb83a51bad49da84
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4624"></a>Kompilator C4624 ostrzegawcze (poziom 1)
"pochodzi z klasy": destruktor został niejawnie zdefiniowany jako usunięty, ponieważ destruktor klasy podstawowej jest niedostępne lub zostały usunięte  
  
 Destruktor nie jest dostępny lub usunięte w klasie podstawowej i w związku z tym nie został wygenerowany dla klasy pochodnej. Błąd kompilatora spowoduje, że każda próba utworzenia obiektu tego typu na stosie.  
  
 Poniższy przykład generuje C4624 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C4624.cpp  
// compile with: /W1 /c  
class B {  
// Uncomment the following line to fix.  
// public:  
   ~B();  
};  
  
class D : public B {};   // C4624 B's destructor not public  
```