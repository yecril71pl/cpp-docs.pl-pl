---
title: C2500 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2500
dev_langs:
- C++
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c05ffd59e415375dd3c7f94ae9bc377c0fc2b9e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229225"
---
# <a name="compiler-error-c2500"></a>C2500 błąd kompilatora
"identifier1": "identifier2" jest już bezpośredniej klasie podstawowej  
  
 Klasy lub struktury występuje więcej niż raz na liście klas podstawowych.  
  
 Bezpośrednie podstawowy jest jednym wymienionych na liście podstawowej. Pośrednie podstawowy jest klasą podstawową dla jednej z klas w liście podstawowych.  
  
 Klasa nie można określić jako bezpośredniej klasie podstawowej więcej niż raz. Klasa może służyć jako pośredniej klasy podstawowej więcej niż raz.  
  
 Poniższy przykład generuje C2500:  
  
```  
// C2500.cpp  
// compile with: /c  
class A {};  
class B : public A, public A {};    // C2500  
  
// OK  
class C : public A {};  
class D : public A {};  
class E : public C, public D {};  
```