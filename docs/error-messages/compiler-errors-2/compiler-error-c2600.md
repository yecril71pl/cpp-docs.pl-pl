---
title: "C2600 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2600
dev_langs: C++
helpviewer_keywords: C2600
ms.assetid: cce11943-ea01-4bee-a7b0-b67d24ec6493
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1fe5383e17212b21c11394c6b987e92aacbe637e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2600"></a>C2600 błąd kompilatora
"Funkcja": nie można zdefiniować generowane przez kompilator specjalnej funkcji członkowskiej (musi być zadeklarowana w klasie najpierw)  
  
 Przed element członkowski, który funkcji, takich jak konstruktory i destruktory mogą być definiowane dla klasy musi zostać zadeklarowany w klasie. Kompilator może wygenerować domyślnych konstruktorów i destruktorów (nazywane specjalnych funkcji Członkowskich), jeśli nie został zadeklarowany w klasie. Jednak w przypadku definiowania jednej z tych funkcji bez odpowiadającą mu deklaracją klasy kompilator wykryje konflikt.  
  
 Aby naprawić ten błąd w deklaracji klasy, należy zadeklarować każdej funkcji elementu członkowskiego zdefiniowanego poza deklaracją klasy.  
  
 Poniższy przykład generuje C2600:  
  
```  
// C2600.cpp  
// compile with: /c  
class C {};  
C::~C() {}   // C2600  
  
class D {  
   D::~D();  
};  
  
D::~D() {}  
```