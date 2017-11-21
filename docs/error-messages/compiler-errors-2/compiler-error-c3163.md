---
title: "C3163 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3163
dev_langs: C++
helpviewer_keywords: C3163
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 95fb254036d2883b6efe6b81bda54864d533c2a8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3163"></a>C3163 błąd kompilatora
"skonstruować": atrybuty niespójne z poprzednią deklaracją  
  
 Atrybuty, które są stosowane do definicji w konflikcie z atrybutów, które są stosowane do deklaracji.  
  
 Jednym ze sposobów rozwiązania C3163 jest wyeliminowanie atrybuty deklaracja przekazująca dalej. Wszelkie atrybuty deklaracja przekazująca dalej powinna być mniejsza niż atrybuty w definicji lub, co najwyżej równa do nich.  
  
 Możliwe przyczyny błędu C3163 obejmuje Microsoft język kodu źródłowego adnotacji (SAL). Makra SAL zwiększa się, chyba że Kompilowanie projektu przy użyciu **/ analyze** flagi. Program, który kompiluje prawidłowo bez / analyze może zgłosić C3163, jeśli użytkownik spróbuje ponownie go skompilować / analyze — opcja. Aby uzyskać więcej informacji na temat SAL, zobacz [adnotacji SAL](../../c-runtime-library/sal-annotations.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3163.  
  
```  
// C3163.cpp  
// compile with: /clr /c  
using namespace System;  
  
[CLSCompliant(true)] void f();  
[CLSCompliant(false)] void f() {}   // C3163  
// try the following line instead  
// [CLSCompliant(true)] void f() {}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Adnotacje SAL](../../c-runtime-library/sal-annotations.md)