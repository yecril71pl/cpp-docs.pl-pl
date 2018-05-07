---
title: C3163 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3163
dev_langs:
- C++
helpviewer_keywords:
- C3163
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e7be8fbba29cf82070d6fd96c76f810bda961489
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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