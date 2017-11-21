---
title: "Kompilatora (poziom 1) ostrzeżenie C4540 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4540
dev_langs: C++
helpviewer_keywords: C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 04ae3142d319659c1f76dfccf31fe870a82692e8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4540"></a>Kompilator C4540 ostrzegawcze (poziom 1)
dynamic_cast służący do konwertowania do niedostępnej lub niejednoznacznej podstawy; test czasu wykonywania nie powiedzie się ("type1" na "type2")  
  
 Możesz użyć `dynamic_cast` Aby przekonwertować z jednego typu. Kompilator ustalić, czy rzutowanie zawsze nie powiedzie się (zwracać **NULL**), ponieważ klasa podstawowa jest niedostępna (`private`, na przykład) lub niejednoznaczne (występuje więcej niż raz w hierarchii klas dla wystąpienia).  
  
 Poniżej przedstawiono przykład to ostrzeżenie. Klasa **B** pochodzi od klasy **A**. Program używa `dynamic_cast` rzutowania z klasy **B** (klasy pochodnej) do klasy **A**, który będzie zawsze działać, ponieważ klasa **B** jest `private` i w związku z tym niedostępne. Zmiana dostępu **A** do **publicznego** rozwiąże ostrzeżenia.  
  
```  
// C4540.cpp  
// compile with: /W1  
  
struct A {   
   virtual void g() {}  
};  
  
struct B : private A {  
   virtual void g() {}  
};  
  
int main() {  
   B b;  
   A * ap = dynamic_cast<A*>(&b);   // C4540  
}  
```