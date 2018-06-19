---
title: C2534 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2534
dev_langs:
- C++
helpviewer_keywords:
- C2534
ms.assetid: 481f9f54-5b51-4aa0-8eea-218f10807705
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bae52374e09852ffb68c5807353155d9928924eb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33228249"
---
# <a name="compiler-error-c2534"></a>C2534 błąd kompilatora
"identyfikator": Konstruktor nie może zwracać wartości  
  
 Konstruktor nie może zwracać wartości ani mieć zwracanego typu (nie nawet `void` zwracany typ).  
  
 Ten błąd może być ustalony przez usunięcie `return` instrukcji z definicji konstruktora.  
  
 Poniższy przykład generuje C2534:  
  
```  
// C2534.cpp  
class A {  
public:  
   int i;  
   A() { return i; }   // C2534  
};  
```