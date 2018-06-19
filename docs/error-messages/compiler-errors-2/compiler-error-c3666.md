---
title: C3666 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3666
dev_langs:
- C++
helpviewer_keywords:
- C3666
ms.assetid: 459e51dd-cefb-4346-99b3-644f2d8b65b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4672cad0f1c0b67b58233c6394e98324a9c32aaf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33264816"
---
# <a name="compiler-error-c3666"></a>C3666 błąd kompilatora
"konstruktora": specyfikator "— słowo kluczowe" nie jest dozwolony na konstruktorze przesłonięcia  
  
 Specyfikator przesłonięcia została użyta w konstruktorze, a nie jest dozwolone. Aby uzyskać więcej informacji, zobacz [specyfikatory Override](../../windows/override-specifiers-cpp-component-extensions.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3666.  
  
```  
// C3666.cpp  
// compile with: /clr /c  
ref struct R {  
   R() new {}   // C3666  
   R(int i) {}   // OK  
};  
```