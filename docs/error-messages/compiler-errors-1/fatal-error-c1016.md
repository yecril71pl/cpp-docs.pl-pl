---
title: Błąd krytyczny C1016 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1016
dev_langs:
- C++
helpviewer_keywords:
- C1016
ms.assetid: 33f45c3e-2d8f-43ad-a445-c412d1d54ce1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8a07f1fc36293b483772087b3325c7e0d0529e1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226137"
---
# <a name="fatal-error-c1016"></a>Błąd krytyczny C1016
\#ifdef oczekuje się, że identyfikator #ifndef Oczekiwano identyfikatora  
  
 Dyrektywa kompilacji warunkowej ([#ifdef](../../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md) lub `#ifndef`) ma identyfikator nie można obliczyć wartości. Aby rozwiązać problem, określ identyfikator.  
  
 Poniższy przykład generuje C1016:  
  
```  
// C1016.cpp  
#ifdef   // C1016  
#define FC1016  
#endif  
  
int main() {}  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C1016b.cpp  
#ifdef X  
#define FC1016  
#endif  
  
int main() {}  
```