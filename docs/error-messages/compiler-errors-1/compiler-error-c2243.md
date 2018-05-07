---
title: C2243 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2243
dev_langs:
- C++
helpviewer_keywords:
- C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16bc95540488b0723869c735b7fc80b15f6e763b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2243"></a>C2243 błąd kompilatora
Konwersja "konwersji typu" z "type1" na "type2" istnieje, ale jest niedostępna  
  
 Dostęp do ochrony (`protected` lub `private`) uniemożliwił konwersja ze wskaźnika do klasy pochodnej na wskaźnik do klasy podstawowej.  
  
 Poniższy przykład generuje C2243:  
  
```  
// C2243.cpp  
// compile with: /c  
class B {};  
class D : private B {};  
class E : public B {};  
  
D d;  
B *p = &d;   // C2243  
  
E e;  
B *p2 = &e;  
```  
  
 Podstawowa klasy z `protected` lub `private` dostępu nie są dostępne dla klientów klasy pochodnej. Te poziomy kontroli dostępu są używane do wskazania, że klasa podstawowa jest szczegółów implementacji, które powinny być widoczne dla klientów. Użyj publicznego pochodnym, jeśli klienci klasy pochodnej mają mieć dostęp do niejawna konwersja wskaźnika klasy pochodnej na wskaźnik do klasy podstawowej.