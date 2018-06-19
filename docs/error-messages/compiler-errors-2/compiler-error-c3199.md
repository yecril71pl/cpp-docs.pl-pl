---
title: C3199 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3199
dev_langs:
- C++
helpviewer_keywords:
- C3199
ms.assetid: e7a478d3-115a-40a3-991b-c7454fd2e28e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cddad2218e81603f59cad51e3a684303e144171e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246574"
---
# <a name="compiler-error-c3199"></a>C3199 błąd kompilatora
Nieprawidłowe użycie zmiennoprzecinkowych pragm: wyjątki nie są obsługiwane w trybie ścisłym  
  
 [Float_control](../../preprocessor/float-control.md) pragma został użyty do określenia model zmiennoprzecinkowych wyjątków w ramach [/FP](../../build/reference/fp-specify-floating-point-behavior.md) inne niż ustawienie **/FP: precise**.  
  
 Poniższy przykład generuje C3199:  
  
```  
// C3199.cpp  
// compile with: /fp:fast  
#pragma float_control(except, on)   // C3199  
```