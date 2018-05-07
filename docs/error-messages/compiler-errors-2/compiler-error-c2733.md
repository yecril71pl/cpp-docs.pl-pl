---
title: C2733 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2733
dev_langs:
- C++
helpviewer_keywords:
- C2733
ms.assetid: 67f83561-c633-407c-a2ee-f9fd16e165bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc1857cd800dd2d395754b9ae95094d9f57aad27
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2733"></a>C2733 błąd kompilatora
drugie powiązanie C przeciążonej funkcji "Funkcja" nie jest dozwolona  
  
 Więcej niż jeden przeciążonej funkcji jest zadeklarowana z powiązaniem C. Korzystając z powiązaniem C, tylko jeden formularz określona funkcja może być zewnętrzny. Ponieważ funkcji przeciążenia mają taką samą nazwę bez, nie można używać z C — programy.  
  
 Poniższy przykład generuje C2733:  
  
```  
// C2733.cpp  
extern "C" {  
   void F1(int);  
}  
  
extern "C" {  
   void F1();   // C2733  
   // try the following line instead  
   // void F2();  
}  
```