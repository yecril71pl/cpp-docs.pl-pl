---
title: C2458 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2458
dev_langs:
- C++
helpviewer_keywords:
- C2458
ms.assetid: ed21901f-1067-42f5-b275-19b480decf5c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0822c12e109cd5a89a8e1050197367b12a24efa9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2458"></a>C2458 błąd kompilatora
"identyfikator": ponowna definicja w ramach definicji  
  
 Klasy, struktury, Unią lub wyliczenie zostało ponownie zdefiniowane w jego własnej deklaracji.  
  
 Poniższy przykład generuje C2458:  
  
```  
// C2458.cpp  
class C {  
   enum i { C };   // C2458  
};  
```