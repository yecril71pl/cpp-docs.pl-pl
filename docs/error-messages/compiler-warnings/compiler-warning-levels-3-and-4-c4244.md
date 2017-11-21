---
title: "Kompilatora (poziom 3 i 4) ostrzeżenie C4244 | Dokumentacja firmy Microsoft"
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
ms.assetid: f116bb09-c479-4b4e-a647-fe629a1383f6
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bbcbe9d1c37827a28ce07849d909d58f5784a5a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-levels-3-and-4-c4244"></a>Kompilator C4244 ostrzegawcze (poziom 3 i 4)
Konwersja "konwersji" z "type1" na "type2", możliwa utrata danych  
  
 Integer — typ jest konwertowana na mniejszy typ całkowity. Jeśli to jest ostrzeżenie poziom 4 *type1* jest `int` i *type2* jest mniejszy niż `int`. W przeciwnym razie jest to poziom 3 (przypisane wartości typu [__int64](../../cpp/int8-int16-int32-int64.md) do zmiennej typu `unsigned int`). Może wystąpić możliwa utrata danych.  
  
 Jeśli otrzymasz C4244, należy albo zmień programu zgodne typy lub Dodaj logikę do kodu, aby upewnić się, możliwe wartości z zakresu zawsze będzie zgodny z typami, które są używane.  
  
 C4244 można również uruchomić na poziomie 2; zobacz [C4244 ostrzeżenie kompilatora (poziom 2)](../../error-messages/compiler-warnings/compiler-warning-level-2-c4244.md) Aby uzyskać więcej informacji.  
  
 Konwersja może być problem z powodu niejawną konwersję.  
  
 Poniższy przykład generuje C4244:  
  
```  
// C4244_level4.cpp  
// compile with: /W4  
int aa;  
unsigned short bb;  
int main() {  
   int b = 0, c = 0;  
   short a = b + c;   // C4244  
  
   bb += c;   // C4244  
   bb = bb + c;   // C4244  
   bb += (unsigned short)aa;   // C4244  
   bb = bb + (unsigned short)aa;   // OK  
}  
```  
  
 Aby uzyskać więcej informacji, zobacz [popularne konwersje arytmetyczne](../../c-language/usual-arithmetic-conversions.md).  
  
```  
// C4244_level3.cpp  
// compile with: /W3  
int main() {  
   __int64 i = 8;  
   unsigned int ii = i;   // C4244  
}  
```  
  
 Ostrzeżenie C4244 może wystąpić, gdy tworzenia kodu dla celów 64-bitowym, który nie generuje ostrzeżenie podczas kompilowania dla celów 32-bitowych. Na przykład różnica wskaźników jest ilość 32-bitowych na platformach 32-bitowych, ale ilość 64-bitowych na platformach 64-bitowych.  
  
 Poniższy przykład generuje C4244 podczas kompilacji dla celów 64-bitowe:  
  
```  
// C4244_level3_b.cpp  
// compile with: /W3   
int main() {  
   char* p1 = 0;  
   char* p2 = 0;  
   int x = p2 - p1;   // C4244  
}  
```