---
title: C2533 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2533
dev_langs:
- C++
helpviewer_keywords:
- C2533
ms.assetid: 5b335652-076c-4824-87c8-a741f64a3ce0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06733dc8ee52462ab7fcac4255ee8fa697a9bac4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229669"
---
# <a name="compiler-error-c2533"></a>C2533 błąd kompilatora
"identyfikator": konstruktorom niedozwolony typ zwracany  
  
 Konstruktor nie może mieć zwracanego typu (nie nawet `void` zwracany typ).  
  
 Wspólne źródło tego błędu jest Brak średnika między końcem definicję klasy a pierwszym implementacji konstruktora. Kompilator widzi jako definicję typ zwracany dla funkcji konstruktora klasy, a następnie generuje C2533.  
  
 Poniższy przykład generuje C2533 i pokazuje, jak rozwiązywanie:  
  
```  
// C2533.cpp  
// compile with: /c  
class X {  
public:  
   X();     
};  
  
int X::X() {}   // C2533 - constructor return type not allowed  
X::X() {}   // OK - fix by using no return type  
```