---
title: "Kompilatora (poziom 4) ostrzeżenie C4625 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4625
dev_langs: C++
helpviewer_keywords: C4625
ms.assetid: 4cc99e50-846c-4784-97da-48b977067851
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c4b1cc20ea5f2ef03b2f2ebefa7a4b2c373d796f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4625"></a>Kompilator C4625 ostrzegawcze (poziom 4)
"pochodzi z klasy": Konstruktor kopiujący został niejawnie zdefiniowany jako usunięty, ponieważ Konstruktor kopiujący klasa podstawowa jest niedostępne lub zostały usunięte  
  
 Konstruktor kopiujący został usunięty lub nie jest dostępna w klasie podstawowej i dlatego nie został wygenerowany dla klasy pochodnej. Błąd kompilatora spowoduje, że każda próba kopiowanie obiektu tego typu.  
  
 To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4625 i pokazuje, jak go naprawić.  
  
```  
// C4625.cpp  
// compile with: /W4 /c  
#pragma warning(default : 4625)  
  
struct A {  
   A() {}  
  
private:  
   A(const A&) {}  
};  
  
struct C : private virtual A {};  
struct B :  C {};   // C4625 no copy constructor  
  
struct D : A {};  
struct E :  D {};   // OK  
```