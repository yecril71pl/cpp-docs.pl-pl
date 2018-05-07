---
title: Błąd krytyczny C1019 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1019
dev_langs:
- C++
helpviewer_keywords:
- C1019
ms.assetid: c4f8968b-bc62-4200-b3ca-69d06c163236
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 119ff2df1554467762c0b960e80ad4c241517628
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1019"></a>Błąd krytyczny C1019
Nieoczekiwany #else  
  
 `#else` Dyrektywy znajduje się poza `#if`, `#ifdef`, lub `#ifndef` utworzenia. Użyj `#else` tylko w jednej z tych konstrukcji.  
  
 Poniższy przykład generuje C1019:  
  
```  
// C1019.cpp  
#else   // C1019  
#endif  
  
int main() {}  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C1019b.cpp  
#if 1  
#else  
#endif  
  
int main() {}  
```