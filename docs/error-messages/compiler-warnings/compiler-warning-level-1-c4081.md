---
title: "Kompilatora (poziom 1) ostrzeżenie C4081 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4081
dev_langs: C++
helpviewer_keywords: C4081
ms.assetid: 6f656373-a080-4989-bbc9-e2f894b03293
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 228a279fa6d6b390a54b295586b57517e2f1a9bb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4081"></a>Kompilator C4081 ostrzegawcze (poziom 1)
Oczekiwano 'token1'; Znaleziono token2  
  
 Kompilator w tym kontekście oczekiwano inny token.  
  
## <a name="example"></a>Przykład  
  
```  
// C4081.cpp  
// compile with: /W1 /LD  
#pragma optimize) "l", on )   // C4081  
```