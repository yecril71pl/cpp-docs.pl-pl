---
title: Kompilatora (poziom 1) ostrzeżenie C4530 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4530
dev_langs:
- C++
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 74804aa3ea0450c08710a5d0818eae67ce9b556e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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