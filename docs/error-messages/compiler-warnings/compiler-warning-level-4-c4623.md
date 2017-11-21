---
title: "Kompilatora (poziom 4) ostrzeżenie C4623 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4623
dev_langs: C++
helpviewer_keywords: C4623
ms.assetid: e630d8d0-f6ea-469c-a74f-07b027587225
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a8d2827c32f38025611a65657395860fbb19e440
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4623"></a>Kompilator C4623 ostrzegawcze (poziom 4)
"`derived class`": Konstruktor domyślny został niejawnie zdefiniowany jako usunięty, ponieważ domyślny konstruktor klasy podstawowej jest niedostępne lub zostały usunięte  
  
 Konstruktor nie jest dostępna w klasie podstawowej i nie został wygenerowany dla klasy pochodnej. Błąd kompilatora spowoduje, że każda próba utworzenia obiektu tego typu na stosie.  
  
 To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4623.  
  
```  
// C4623.cpp  
// compile with: /W4  
#pragma warning(default : 4623)  
class B {  
   B();  
};  
  
class C {  
public:  
   C();  
};  
  
class D : public B {};   // C4623 - to fix, make B's constructor public  
class E : public C {};   // OK - class C constructor is public  
  
int main() {  
   // D d;  will cause an error  
}  
```