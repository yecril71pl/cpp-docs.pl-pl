---
title: C3168 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3168
dev_langs:
- C++
helpviewer_keywords:
- C3168
ms.assetid: 4c36fcfb-c351-48ff-b4eb-78d2aa1b4d55
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83f0d6c6b35d863ee200798bd4c6a8bcd08d88ab
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3168"></a>C3168 błąd kompilatora
'type': niedozwolony typ podstawowy dla wyliczenia  
  
Podstawowy typ określony dla `enum` typu jest nieprawidłowa. Typ podstawowy musi być typem całkowitym C++ lub odpowiedni typ CLR.  
  
Poniższy przykład generuje C3168:  
  
```  
// C3168.cpp  
// compile with: /clr /c  
ref class G{};  
  
enum class E : G { e };   // C3168  
enum class F { f };   // OK  
```  
