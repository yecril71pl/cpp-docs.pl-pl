---
title: "C2133 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2133
dev_langs: C++
helpviewer_keywords: C2133
ms.assetid: 8942f9e8-9818-468f-97db-09dbd124fcae
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c04452ec947adefa6b30928dc75de4edffc361fc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2133"></a>C2133 błąd kompilatora
'Identyfikator': nieznany rozmiar  
  
 Bez określonego rozmiaru tablicy jest zadeklarowany jako element członkowski klasy, struktury, Unią lub wyliczenia. Opcja /Za (ANSI C) nie zezwala na tablice bez określonego rozmiaru elementu członkowskiego.  
  
 Poniższy przykład generuje C2133:  
  
```  
// C2133.cpp  
// compile with: /Za  
struct X {  
   int a[0];   // C2133 unsized array  
};  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C2133b.cpp  
// compile with: /c  
struct X {  
   int a[0];   // no /Za  
};  
```