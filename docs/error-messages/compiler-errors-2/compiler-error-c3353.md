---
title: "C3353 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3353
dev_langs: C++
helpviewer_keywords: C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 47a0231a161a2502c26786fceeb1b3634b236eaf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3353"></a>C3353 błąd kompilatora
"delegowanie": delegat można tworzyć tylko z globalnej funkcji lub funkcja członkowska zarządzanego lub typu WinRT  
  
 Delegatów, zadeklarowana z [delegować](../../windows/delegate-cpp-component-extensions.md) — słowo kluczowe, mogą być deklarowane tylko w zakresie globalnym.  
  
 Poniższy przykład generuje C3353:  
  
```  
// C3353.cpp  
// compile with: /clr  
delegate int f;   // C3353  
```