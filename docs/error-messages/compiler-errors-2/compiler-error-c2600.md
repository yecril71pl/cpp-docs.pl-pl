---
title: C2600 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2600
dev_langs:
- C++
helpviewer_keywords:
- C2600
ms.assetid: cce11943-ea01-4bee-a7b0-b67d24ec6493
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13b4cdf15dca9b3978f8c7855a5f1b07cc86f0b8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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