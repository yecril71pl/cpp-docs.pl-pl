---
title: "Kompilatora (poziom 2) ostrzeżenie C4244 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4244
dev_langs: C++
helpviewer_keywords: C4244
ms.assetid: 2c19d157-21d1-42c2-a6c0-3f30f2ce3813
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7f2059d6b17d803740f70e0d640e212d15858705
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-2-c4244"></a>Kompilator C4244 ostrzegawcze (poziom 2)
"argument": konwersja z "type1" na "type2", możliwa utrata danych  
  
 A zmiennoprzecinkową typ punktu został skonwertowany do typu integer.  Może wystąpić możliwa utrata danych.  
  
 Jeśli otrzymasz C4244, należy albo zmień programu zgodne typy lub Dodaj logikę do kodu, aby upewnić się, możliwe wartości z zakresu zawsze będzie zgodny z typami, które są używane.  
  
 C4244 można również uruchomić na poziomie 3 i 4; zobacz [C4244 ostrzeżenie kompilatora (poziom 3 i 4)](../../error-messages/compiler-warnings/compiler-warning-levels-3-and-4-c4244.md) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4244:  
  
```  
// C4244_level2.cpp  
// compile with: /W2  
  
int f(int x){ return 0; }  
int main() {  
   double x = 10.1;  
   int i = 10;  
   return (f(x));   // C4244  
   // try the following line instead  
   // return (f(i));  
}  
```