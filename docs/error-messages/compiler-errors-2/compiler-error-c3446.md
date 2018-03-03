---
title: "C3446 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 07/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3446
dev_langs:
- C++
helpviewer_keywords:
- C3445
ms.assetid: 33064548-24e4-46f1-beb1-476e3c3b3fbf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 590f9b4012c7a00cb73a61b0d275ff9c5ee9cf9e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3446"></a>C3446 błąd kompilatora  
  
>"*klasy*": Inicjator elementu członkowskiego domyślnego nie jest dozwolona dla elementu członkowskiego klasy wartości  
  
W programie Visual Studio 2015 i starszych kompilator dozwolone, ale ignorowane inicjator elementu członkowskiego domyślnej dla elementu członkowskiego klasy wartości. Inicjowanie domyślnych klasy wartości zawsze zero inicjuje członków; domyślny konstruktor nie jest dozwolone. W programie Visual Studio 2017 r domyślny element członkowski inicjatory podnieść wystąpi błąd kompilatora w poniższym przykładzie:

## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3446 w programie Visual Studio 2017 lub nowszy:  
  
```cpp  
// C3446.cpp  
value struct V
{
       int i = 0; // error C3446: 'V::i': a default member initializer  
                  // is not allowed for a member of a value class
       int j {0}; // C3446           
};
```  
  
Aby rozwiązać problem, Usuń inicjatora:  
  
```cpp  
// C3446b.cpp  
value struct V
{
       int i;  
       int j;
};
```  
  
