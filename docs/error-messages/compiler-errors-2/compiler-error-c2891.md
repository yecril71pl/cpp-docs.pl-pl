---
title: C2891 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2891
dev_langs:
- C++
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01741d1cc67f0045c46ab392212625b9e1a2d8ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246373"
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