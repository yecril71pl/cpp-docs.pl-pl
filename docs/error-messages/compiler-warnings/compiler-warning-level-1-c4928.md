---
title: "Kompilatora (poziom 1) ostrzeżenie C4928 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4928
dev_langs: C++
helpviewer_keywords: C4928
ms.assetid: 77235d7f-9360-45cb-8348-d148c605c4a3
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1e5f096ada450818f8175a8807d074b407afd2d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4928"></a>Kompilator C4928 ostrzegawcze (poziom 1)
nieprawidłowe inicjowanie kopiowania; niejawnie zastosowano więcej niż jedną konwersję zdefiniowaną przez użytkownika  
  
 Znaleziono więcej niż jeden procedury konwersji zdefiniowanej przez użytkownika. Kompilator wykonać kod w wszystkich tych procedur.  
  
 To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.  
  
 Poniższy przykład generuje C4928:  
  
```  
// C4928.cpp  
// compile with: /W1  
#pragma warning(default: 4928)  
  
struct I  
{  
};  
  
struct I1 : I  
{  
};  
  
struct I2 : I  
{  
};  
  
template <class T>  
struct Ptr  
{  
   operator T*()  
   {  
      return 0;  
   }  
  
   Ptr()  
   {  
   }  
  
   Ptr(I*)  
   {  
   }  
};  
  
int main()  
{  
   Ptr<I1> p1;  
   Ptr<I2> p2 = p1;   // C4928  
   // try one of the following two lines to resolve this error  
   // Ptr<I2> p2(p1);  
   // Ptr<I2> p2 = (I1*) p1;  
}  
```