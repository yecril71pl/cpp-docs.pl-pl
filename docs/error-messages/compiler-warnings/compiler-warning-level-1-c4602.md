---
title: Kompilatora (poziom 1) ostrzeżenie C4602 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4602
dev_langs:
- C++
helpviewer_keywords:
- C4602
ms.assetid: c1f0300f-e2a2-4c9e-a7c3-4c7318d10509
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b2c25fd983f1ac7cebcc568a0b47c06c4d8e23a9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279530"
---
# <a name="compiler-warning-level-1-c4602"></a>Kompilator C4602 ostrzegawcze (poziom 1)
\#pragma pop_macro: "Nazwa makra" nie poprzedniej dyrektywy #pragma push_macro dla tego identyfikatora  
  
 Jeśli używasz [pop_macro](../../preprocessor/pop-macro.md) dla konkretnego makra, należy najpierw przekazanego nazwy tego makra do [dyrektywy push_macro](../../preprocessor/push-macro.md). Na przykład poniższy przykład generuje C4602:  
  
```  
// C4602.cpp  
// compile with: /W1  
int main()  
{  
   #pragma pop_macro("x")   // C4602 x is not on the stack  
}  
```