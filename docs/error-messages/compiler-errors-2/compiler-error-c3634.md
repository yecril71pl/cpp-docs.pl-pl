---
title: C3634 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3634
dev_langs:
- C++
helpviewer_keywords:
- C3634
ms.assetid: fd09f10c-f863-483b-9756-71c16b760b02
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc7b30f01923ec4757ad1254f6646bc374d3f1da
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33263788"
---
# <a name="compiler-error-c3634"></a>C3634 błąd kompilatora
"Funkcja": nie można definiować metody abstrakcyjnej zarządzanego lub WinRTclass  
  
 Metoda abstrakcyjna mogą być deklarowane w zarządzanych lub klasy WinRT, ale nie może być zdefiniowana.  
  
## <a name="example"></a>Przykład  
Poniższy przykład generuje C3634:  
  
```  
// C3634.cpp  
// compile with: /clr  
ref class C {  
   virtual void f() = 0;  
};  
  
void C::f() {   // C3634 - don't define managed class' pure virtual method  
}  
```  
