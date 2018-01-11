---
title: "C3199 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3199
dev_langs: C++
helpviewer_keywords: C3199
ms.assetid: e7a478d3-115a-40a3-991b-c7454fd2e28e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1f32d42123a64d14ee04a6af7cdebd79ad19b809
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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