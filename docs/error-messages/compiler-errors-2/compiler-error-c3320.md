---
title: C3320 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3320
dev_langs:
- C++
helpviewer_keywords:
- C3320
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08810d38b74081cfb8573d1e33ea3a8ec4dabd4c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33254579"
---
# <a name="compiler-error-c3320"></a>C3320 błąd kompilatora
'type': typ nie może mieć takiej samej nazwy jak właściwość modułu "name"  
  
Zdefiniowane przez użytkownika typu wyeksportowanego (UDT), który może być struktury, klasy, enum lub union, nie mają taką samą nazwę jak parametr przekazany do [modułu](../../windows/module-cpp.md) właściwości name atrybutu.  
  
## <a name="example"></a>Przykład  
Poniższy przykład generuje C3320:  
  
```cpp  
// C3320.cpp  
#include "unknwn.h"  
[module(name="xx")];  
  
[export] struct xx {   // C3320  
// Try the following line instead  
// [export] struct yy {  
   int i;  
};  
```