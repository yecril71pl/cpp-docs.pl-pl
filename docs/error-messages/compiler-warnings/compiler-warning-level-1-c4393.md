---
title: Kompilatora (poziom 1) ostrzeżenie C4393 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4393
dev_langs:
- C++
helpviewer_keywords:
- C4393
ms.assetid: 353a0539-d1ea-4c1b-8849-c9b321ec9842
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 59a1022f54d22e97a11c0970cad6bcd8918c7190
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277943"
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