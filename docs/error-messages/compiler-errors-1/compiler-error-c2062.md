---
title: C2062 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2062
dev_langs:
- C++
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d11151a8e842796e4a5a8d45956782421daa1c70
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33168662"
---
# <a name="compiler-error-c2062"></a>C2062 błąd kompilatora
Typ 'type' nieoczekiwany  
  
 Kompilator nie Oczekiwano nazwy typu.  
  
 Poniższy przykład generuje C2062:  
  
```  
// C2062.cpp  
// compile with: /c  
struct A {  : int l; };   // C2062  
struct B { private: int l; };   // OK  
```  
  
 C2062 może również wystąpić ze względu na sposób kompilator typy Niezdefiniowany dojść w liście parametrów konstruktora. Jeśli kompilator napotka niezdefiniowanego typu (błędnie?), zakłada konstruktora to wyrażenie, a następnie generuje C2062. Aby rozwiązać, należy używać tylko zdefiniowanych typów, na liście parametrów konstruktora.