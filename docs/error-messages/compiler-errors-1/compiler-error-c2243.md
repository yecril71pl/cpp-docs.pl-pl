---
title: "C2243 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2243
dev_langs:
- C++
helpviewer_keywords:
- C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8ae7349cce7e824af5621fba121e762aeccffa9e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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