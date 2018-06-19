---
title: C3194 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3194
dev_langs:
- C++
helpviewer_keywords:
- C3194
ms.assetid: 49d3ffc6-eff6-4b46-865b-18811692a8bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd6fad304dc4e400d6ca25c7e835b2d0a6935117
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33247803"
---
# <a name="compiler-error-c3194"></a>C3194 błąd kompilatora
"członek": typ wartościowy nie może mieć operatora przypisania  
  
 Specjalne funkcje Członkowskie wymagające automatycznego wywołania przez kompilator, takich jak Konstruktor kopiujący lub kopia operatora przypisania nie są obsługiwane w klasie wartości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3194.  
  
```  
// C3194.cpp  
// compile with: /clr /c  
value struct MyStruct {  
   MyStruct& operator= (const MyStruct& i) { return *this; }   // C3194  
};  
  
ref struct MyStruct2 {  
   MyStruct2% operator= (const MyStruct2% i) { return *this; }   // OK  
};  
```