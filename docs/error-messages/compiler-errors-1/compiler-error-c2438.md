---
title: C2438 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2438
dev_langs:
- C++
helpviewer_keywords:
- C2438
ms.assetid: 3a0ab3ba-d0e4-4d8f-971d-e503397cc827
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf42740c137953007cab2c5301bff122b553e5f6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2438"></a>C2438 błąd kompilatora
'Identyfikator': nie można zainicjować danych statycznej klasy poprzez Konstruktor  
  
 Konstruktor służy do inicjowania statyczny element członkowski klasy. Statyczne elementy członkowskie muszą zostać zainicjowane w definicji poza deklaracją klasy.  
  
 Poniższy przykład generuje C2438:  
  
```  
// C2438.cpp  
struct X {  
   X(int i) : j(i) {}   // C2438  
   static int j;  
};  
  
int X::j;  
  
int main() {  
   X::j = 1;  
}  
```