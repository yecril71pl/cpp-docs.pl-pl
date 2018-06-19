---
title: Kompilatora (poziom 1) ostrzeżenie C4928 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4928
dev_langs:
- C++
helpviewer_keywords:
- C4928
ms.assetid: 77235d7f-9360-45cb-8348-d148c605c4a3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 625fbfd6bb67f1fc2636939ac7b05278c0bb26a8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33296279"
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