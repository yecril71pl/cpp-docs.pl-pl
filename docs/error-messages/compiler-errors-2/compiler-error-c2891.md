---
title: "C2891 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2891
dev_langs:
- C++
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 979d77ad5b5bd0b68dd539695d6cb1b60b099c55
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2891"></a>C2891 błąd kompilatora
"parametr": nie można przyjąć adresu parametru szablonu  
  
 Nie można przyjąć adresu parametru szablonu, chyba że jest l-wartością. Parametry typu nie są lvalues, ponieważ mają one żadnego adresu. Wartości typu bez listy parametrów szablonu, które nie są lvalues nie mieć również adres. To jest przykładowy kod, który powoduje C2891 błąd kompilatora, ponieważ wartość przekazany jako parametr szablonu jest generowane przez kompilator kopię argumentu szablonu.  
  
```  
template <int i> int* f() { return &i; }  
```  
  
 Parametry szablonu, które są lvalues, takie jak typy referencyjne może mieć swój adres pobrany.  
  
```  
template <int& r> int* f() { return &r; }  
```  
  
 Aby rozwiązać ten problem, nie przyjąć adresu parametru szablonu, chyba że jest l-wartością.