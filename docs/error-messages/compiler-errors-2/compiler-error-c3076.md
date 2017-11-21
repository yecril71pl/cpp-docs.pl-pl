---
title: "C3076 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3076
dev_langs: C++
helpviewer_keywords: C3076
ms.assetid: 8a87b3e4-2c17-4b87-9622-ef0962d6a34e
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: eb4668f69ca7d8680620c85b7a37b70c2c58c96b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3076"></a>C3076 błąd kompilatora
"instance": nie można osadzić wystąpienia typu referencyjnego "type" w typie natywnym  
  
 Typ natywny nie może zawierać wystąpienia typu CLR.  
  
 Aby uzyskać więcej informacji, zobacz [semantyka stosu C++ dla typów referencyjnych](../../dotnet/cpp-stack-semantics-for-reference-types.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3076.  
  
```  
// C3076.cpp  
// compile with: /clr /c  
ref struct U {};  
  
struct V {  
   U y;   // C3076  
};  
  
ref struct W {  
   U y;   // OK  
};  
```