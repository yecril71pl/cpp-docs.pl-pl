---
title: "C3084 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3084
dev_langs: C++
helpviewer_keywords: C3084
ms.assetid: 0362cb70-e24e-476f-a24d-8f5bb97c3afd
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a160c807bbc8a44c8073cc66ddacad7c8a398d53
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3084"></a>C3084 błąd kompilatora
"Funkcja": finalizator/destruktor nie może być "— słowo kluczowe"  
  
 Finalizator lub destruktor został niepoprawnie zadeklarowany.  
  
 Na przykład destruktor nie powinien być oznaczony jako sealed.  Destruktor będą niedostępne do typów pochodnych.  Aby uzyskać więcej informacji, zobacz [jawne zastąpienia](../../windows/explicit-overrides-cpp-component-extensions.md) i [destruktory i finalizatory w porady: Definiowanie oraz stosowanie klas i struktur (C + +/ CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3084.  
  
```  
// C3084.cpp  
// compile with: /clr /c  
ref struct R {  
protected:  
   !R() sealed;   // C3084  
   !R() abstract;   // C3084  
   !R();  
};  
```