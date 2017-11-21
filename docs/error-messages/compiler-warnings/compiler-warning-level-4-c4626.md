---
title: "Kompilatora (poziom 4) ostrzeżenie C4626 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4626
dev_langs: C++
helpviewer_keywords: C4626
ms.assetid: 7f822ff4-a4a3-4f17-b45b-e8b7b4659a14
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a280faadea23ced85c5b8256fd6b00c8d84370f1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4626"></a>Kompilator C4626 ostrzegawcze (poziom 4)
"pochodzi z klasy": operator przypisania został niejawnie zdefiniowany jako usunięty, ponieważ operator przypisania klasa podstawowa jest niedostępne lub zostały usunięte  
  
 Operator przypisania został usunięty lub nie jest dostępna w klasie podstawowej i dlatego nie został wygenerowany dla klasy pochodnej. Błąd kompilatora spowoduje, że wszelkie próby przypisać obiekty tego typu.  
  
 To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.  
  
 Poniższy przykład generuje C4626 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C4626  
// compile with: /W4  
#pragma warning(default : 4626)  
class B  
{  
// public:  
   B& operator = (const B&)  
   {  
      return *this;  
   }  
};  
  
class D : public B  
{  
  
}; // C4626 - to fix, make B's copy constructor public  
  
int main()  
{  
   D m;  
   D n;  
   // m = n;   // this line will cause an error  
}  
```