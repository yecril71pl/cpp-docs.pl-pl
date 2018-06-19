---
title: C3075 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3075
dev_langs:
- C++
helpviewer_keywords:
- C3075
ms.assetid: f431daa9-e0fa-48f0-a5c3-f99be96b55e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c582c9907987fe9f015f3e639e2f3f2e362e0c82
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33255552"
---
# <a name="compiler-error-c3075"></a>C3075 błąd kompilatora
"instance": nie można osadzić wystąpienia typu referencyjnego "type" w typie wartości  
  
 Typ wartości nie może zawierać wystąpienia typu referencyjnego.  
  
 Aby uzyskać więcej informacji, zobacz [semantyka stosu C++ dla typów referencyjnych](../../dotnet/cpp-stack-semantics-for-reference-types.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3075.  
  
```  
// C3075.cpp  
// compile with: /clr /c  
ref struct U {};  
value struct X {  
   U y;   // C3075  
};  
  
ref struct Y {  
   U y;   // OK  
};  
```