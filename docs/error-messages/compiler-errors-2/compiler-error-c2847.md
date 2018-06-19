---
title: C2847 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2847
dev_langs:
- C++
helpviewer_keywords:
- C2847
ms.assetid: 9ad9a0e0-8b16-49d9-a5be-f8eda2372aa9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd18d685649c5ad8f03e3fdbb8b375717227f4c2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33245978"
---
# <a name="compiler-error-c2847"></a>C2847 błąd kompilatora
Nie można zastosować operatora sizeof do zarządzanych lub typu WinRT "class"  
  
 [Sizeof](../../cpp/sizeof-operator.md) operator pobiera wartości obiektu w czasie kompilacji. Rozmiar zarządzanego lub klasy WinRT, interfejsem lub typ wartości jest dynamiczny i dlatego nie może być znane w czasie kompilacji.  
  
 Na przykład poniższy przykład generuje C2847:  
  
```  
// C2847.cpp  
// compile with: /clr  
ref class A {};  
  
int main() {  
   A ^ xA = gcnew A;  
   sizeof(*xA);   // C2847 cannot use sizeof on managed object  
}  
```  
