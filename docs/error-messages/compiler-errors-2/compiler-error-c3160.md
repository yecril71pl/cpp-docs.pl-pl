---
title: C3160 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3160
dev_langs:
- C++
helpviewer_keywords:
- C3160
ms.assetid: a250c433-8adf-43b9-8dee-c3794e09b0a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 670dd386be82b4356262cb59442d36fb1d6f646b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3160"></a>C3160 błąd kompilatora
"wskaźnik": element członkowski danych zarządzanego lub klasy WinRT nie może mieć tego typu  
  
 Wskaźniki kolekcji wewnętrznej pamięci może wskazywać wnętrza zarządzanego lub klasy WinRT. Ponieważ wolniej niż obiekt całości wskaźniki i wymagają specjalnej obsługi przez moduł garbage collector, nie można zadeklarować wewnętrznych wskaźników zarządzane jako elementy członkowskie klasy.  
  
 Poniższy przykład generuje C3160:  
  
```  
// C3160.cpp  
// compile with: /clr  
ref struct A {  
   // cannot create interior pointers inside a class  
   interior_ptr<int> pg;   // C3160  
   int g;   // OK  
   int* pg2;   // OK  
};  
  
int main() {  
   interior_ptr<int> pg2;   // OK  
}  
```  
