---
title: "Kompilatora (poziom 1) ostrzeżenie C4393 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4393
dev_langs: C++
helpviewer_keywords: C4393
ms.assetid: 353a0539-d1ea-4c1b-8849-c9b321ec9842
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 76c29081f2423464f235e7ff15b76b7bdcb35d3a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4393"></a>Kompilator C4393 ostrzegawcze (poziom 1)
"var": const nie ma wpływu na literał elementu członkowskiego danych; ignorowane  
  
 A [literału](../../windows/literal-cpp-component-extensions.md) również element członkowski danych został określony jako stała.  Ponieważ literał elementu członkowskiego danych wskazuje const, nie trzeba dodać do deklaracji const.  
  
 Poniższy przykład generuje C4393:  
  
```  
// C4393.cpp  
// compile with: /clr /W1 /c  
ref struct Y1 {  
   literal const int staticConst = 10;   // C4393  
   literal int staticConst2 = 10;   // OK  
};  
```