---
title: "C2891 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2891
dev_langs: C++
helpviewer_keywords: C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6c35294472fe4142e7e6689adfc5f5f71c27b664
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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