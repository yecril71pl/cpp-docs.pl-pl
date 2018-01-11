---
title: "C2861 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2861
dev_langs: C++
helpviewer_keywords: C2861
ms.assetid: 012bb44d-6c9b-4def-b54e-b19f1f8ddd1b
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 927c1fb7e80da9d3a2dd221cb5bab3bb17abb109
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2861"></a>C2861 błąd kompilatora
"Nazwa funkcji": funkcja członkowska interfejsu nie może być zdefiniowana  
  
 Kompilator napotkał interfejs — słowo kluczowe lub ustalona struktury jako interfejs, ale można odnaleźć członka definicji funkcji.  Interfejs nie może zawierać definicji funkcji członkowskiej.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2861:  
  
```  
// C2861.cpp  
// compile with: /c  
#include <objbase.h>   // required for IUnknown definition  
[ object, uuid("00000000-0000-0000-0000-000000000001") ]  
__interface IMyInterface : IUnknown {  
   HRESULT mf(int a);  
};  
  
HRESULT IMyInterface::mf(int a) {}   // C2861  
  
```