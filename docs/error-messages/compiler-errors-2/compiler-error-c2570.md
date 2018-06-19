---
title: C2570 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2570
dev_langs:
- C++
helpviewer_keywords:
- C2570
ms.assetid: d65d0b32-2fac-464a-bcdf-0ebcedf3bf32
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b870ddd8bb162f4f65bd3200c397f912249304b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33228310"
---
# <a name="compiler-error-c2570"></a>C2570 błąd kompilatora
"identyfikator": union nie może mieć klas podstawowych  
  
 Unia pochodzi z klasy, struktury lub związku. Jest to niedozwolone. Zamiast tego zadeklarować typu pochodnego jako klasy lub struktury.  
  
 Poniższy przykład generuje C2570:  
  
```  
// C2570.cpp  
// compile with: /c  
class base {};  
union hasPubBase : public base {};   // C2570  
union hasNoBase {};   // OK  
```