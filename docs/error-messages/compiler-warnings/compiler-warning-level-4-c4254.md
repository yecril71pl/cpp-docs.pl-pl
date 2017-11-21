---
title: "Kompilatora (poziom 4) ostrzeżenie C4254 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: c4254
dev_langs: C++
helpviewer_keywords: C4254
ms.assetid: c7dcef24-d535-4c98-bb41-fc3d2b88fd11
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 386ed491aab54fcfb94880f4f75e5a6e7c081a69
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4254"></a>Kompilator C4254 ostrzegawcze (poziom 4)
"operator": konwersja z "type1" na "type2", możliwa utrata danych  
  
 Większy pola bitowego został przypisany do pola bitowego mniejsze. Może być utrata danych.  
  
 To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.  
  
 Poniższy przykład generuje C4254:  
  
```  
// C4254.cpp  
// compile with: /W4  
#pragma warning(default: 4254)  
  
struct X {  
   int a : 20;  
   int b : 12;  
};  
  
int main() {  
   X *x = new X();  
   x->b = 10;  
   x->a = 4;  
   x->a = x->b;    // OK  
   x->b = x->a;    // C4254  
};  
```