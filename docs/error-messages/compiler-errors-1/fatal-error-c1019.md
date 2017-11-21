---
title: "Błąd krytyczny C1019 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1019
dev_langs: C++
helpviewer_keywords: C1019
ms.assetid: c4f8968b-bc62-4200-b3ca-69d06c163236
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 90d826ded9ebd8fdc2b304900af523b7ffe8b395
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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