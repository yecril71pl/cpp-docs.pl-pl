---
title: C3622 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3622
dev_langs:
- C++
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d8c7ab18bfba899c2df41becb457ed2e7725f81
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33260095"
---
# <a name="compiler-error-c3622"></a>C3622 błąd kompilatora
"class": klasy zadeklarowanej jako "— słowo kluczowe" nie można utworzyć wystąpienia  
  
Podjęto próbę utworzenia wystąpienia klasy oznaczonej jako [abstrakcyjny](../../windows/abstract-cpp-component-extensions.md). Klasa jest oznaczona jako `abstract` może być klasą podstawową, ale nie można utworzyć wystąpienia.  
  
## <a name="example"></a>Przykład  
Poniższy przykład generuje C3622.  
  
```  
// C3622.cpp  
// compile with: /clr  
ref class a abstract {};  
  
int main() {  
   a aa;   // C3622  
}  
```  
