---
title: C2814 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2814
dev_langs:
- C++
helpviewer_keywords:
- C2814
ms.assetid: 7d165136-a08b-4497-a76d-60a21bb19404
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75215a0df53606c8807cc275e86616c1ae8c6b42
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33237156"
---
# <a name="compiler-error-c2814"></a>C2814 błąd kompilatora
"członek": typ natywny nie może być zagnieżdżone w obrębie zarządzanego lub WinRT "typu"  
  
## <a name="example"></a>Przykład  
 Typ macierzysty nie mogą być zagnieżdżone w typie CLR lub WinRT. Poniższy przykład generuje C2814 i pokazuje, jak go naprawić.  
  
```  
// C2814.cpp  
// compile with: /clr /c  
ref class A {  
   class B {};   // C2814  
   ref class C {};   // OK  
};  
```  
