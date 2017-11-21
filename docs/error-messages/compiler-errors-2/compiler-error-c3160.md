---
title: "C3160 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3160
dev_langs: C++
helpviewer_keywords: C3160
ms.assetid: a250c433-8adf-43b9-8dee-c3794e09b0a5
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: df09956b70d88b2ebb9efa542aad898f3d1295f2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
