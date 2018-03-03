---
title: "Kompilatora (poziom 1) ostrzeżenie C4530 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4530
dev_langs:
- C++
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: adfa006e3b84517601237bbd844ac983115e74ec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4530"></a>Kompilator C4530 ostrzegawcze (poziom 1)
Obsługa wyjątków języka C++ używane, ale semantyka rozwinięć nie są włączone. Określ/ehsc  
  
 Użyto C++, obsługa wyjątków, ale [/ehsc](../../build/reference/eh-exception-handling-model.md) nie zostały wybrane.  
  
 Nie została włączona opcja/ehsc, obiekt z automatycznego magazynu w ramce między funkcje wykonywania do rzutowania i przechwytywanie do rzutowania nie zostać zniszczone. Jednak utworzyć obiektu magazynu automatyczne w **spróbuj** lub **catch** bloku zostaną zniszczone.  
  
 Poniższy przykład generuje C4530:  
  
```  
// C4530.cpp  
// compile with: /W1  
int main() {  
   try{} catch(int*) {}   // C4530  
}  
```  
  
 Kompiluj próbki/ehsc, aby rozwiązać ostrzeżenia.