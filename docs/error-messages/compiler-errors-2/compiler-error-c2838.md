---
title: C2838 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2838
dev_langs:
- C++
helpviewer_keywords:
- C2838
ms.assetid: 176b2ad6-7a84-4019-b97e-328866054457
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a170e869a2d8869424b23fb154cd23f0ed26c9fa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33248199"
---
# <a name="compiler-error-c2838"></a>C2838 błąd kompilatora
"członek": niedozwolona nazwa kwalifikowana w deklaracji elementu członkowskiego  
  
 Klasy, struktury lub związku korzysta w pełni kwalifikowana nazwa można ponownie zadeklarować członkiem innej klasy, struktury lub związku.  
  
 Poniższy przykład generuje C2838:  
  
```  
// C2838.cpp  
// compile with: /c  
class Bellini {  
public:  
    void Norma();  
};  
  
class Bottesini {  
   Bellini::Norma();  // C2838  
};  
```