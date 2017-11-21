---
title: "C3550 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3550
dev_langs: C++
helpviewer_keywords: C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 52b3e3323bac9ad55ff10481b3504e4e054ba874
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3550"></a>C3550 błąd kompilatora
w tym kontekście dozwolone jest tylko zwykły element "decltype(auto)"  
  
 Jeśli `decltype(auto)` jest używany jako symbol zastępczy dla zwracanego typu funkcji musi być używany przez samego siebie. Nie można użyć jako część deklaracji wskaźnika (`decltype(auto*)`), deklaracja odwołania (`decltype(auto&)`), lub inne takie kwalifikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Automatycznie](../../cpp/auto-cpp.md)