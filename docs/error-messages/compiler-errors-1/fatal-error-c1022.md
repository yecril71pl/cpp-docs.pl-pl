---
title: "Błąd krytyczny C1022 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1022
dev_langs: C++
helpviewer_keywords: C1022
ms.assetid: edada720-dc73-49bc-bd93-a7945a316312
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8215a0a505503c9a4040439629aea59926baf27e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1022"></a>Błąd krytyczny C1022
Oczekiwano #endif  
  
 `#if`, `#ifdef`, Lub `#ifndef` dyrektywy nie posiada odpowiadającego `#endif` dyrektywy. Należy się, że każdy `#if`, `#ifdef`, lub `#ifndef` ma pasujący `#endif`.  
  
 Poniższy przykład generuje C1022:  
  
```  
// C1022.cpp  
#define true 1  
  
#if (true)  
#else   
#else    // C1022  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C1022b.cpp  
// compile with: /c  
#define true 1  
  
#if (true)  
#else   
#endif  
```