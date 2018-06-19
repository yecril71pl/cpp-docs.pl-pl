---
title: Błąd krytyczny C1018 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1018
dev_langs:
- C++
helpviewer_keywords:
- C1018
ms.assetid: 2ceb8a99-30b2-4b80-bf42-e9f3305b3c52
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 121ec73658527ff03e3cbc4871db78a5d00b50d1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226434"
---
# <a name="fatal-error-c1018"></a>Błąd krytyczny C1018
Nieoczekiwany #elif  
  
 `#elif` Dyrektywy znajduje się poza `#if`, `#ifdef`, lub `#ifndef` utworzenia. Użyj `#elif` tylko w jednej z tych konstrukcji.  
  
 Poniższy przykład generuje C1018:  
  
```  
// C1018.cpp  
#elif      // C1018  
#endif  
  
int main() {}  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C1018b.cpp  
#if 1  
#elif  
#endif  
  
int main() {}  
```