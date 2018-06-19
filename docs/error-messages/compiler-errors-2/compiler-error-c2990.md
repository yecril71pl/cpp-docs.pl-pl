---
title: C2990 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2990
dev_langs:
- C++
helpviewer_keywords:
- C2990
ms.assetid: 674e9f6a-6743-4af0-a7ed-cbe11103a2f8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 669cfcd1e9a715b247c9264856e8877275d6407c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33243032"
---
# <a name="compiler-error-c2990"></a>C2990 błąd kompilatora
"class": typ innych niż klasa jak już został zadeklarowany jako typ klasy  
  
 Z systemem innym niż ogólne lub klasy szablonu ponownie definiuje klasę określono opcję ogólne lub szablonu. Sprawdź pliki nagłówkowe konflikty.  
  
 Poniższy przykład generuje C2990:  
  
```  
// C2990.cpp  
// compile with: /c  
template <class T>  
class C{};  
class C{};   // C2990  
```  
  
 C2990 może również wystąpić, gdy użycie typów ogólnych:  
  
```  
// C2990b.cpp  
// compile with: /clr /c  
generic <class T>  
ref struct GC;  
  
ref struct GC {};   // C2990  
```  
  
 C2990 może również wystąpić ze względu na istotne zmiany w kompilatorze języka Visual C++ dla Visual C++ 2005; Kompilator teraz wymaga wielu deklaracji dla tego samego typu identyczne względem specyfikacji szablonu.  
  
 Poniższy przykład generuje C2990:  
  
```  
// C2990c.cpp  
// compile with: /c  
template<class T>  
class A;  
  
template<class T>  
struct A2 {  
   friend class A;   // C2990  
};  
  
// OK  
template<class T>  
struct B {  
   template<class T>  
   friend class A;  
};  
```