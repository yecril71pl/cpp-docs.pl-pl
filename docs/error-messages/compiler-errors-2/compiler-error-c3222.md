---
title: C3222 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3222
dev_langs:
- C++
helpviewer_keywords:
- C3222
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 424c0f1011d984dff59d3d952347ad4f7b90f515
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3222"></a>C3222 błąd kompilatora
"parametr": nie można zadeklarować domyślnych argumentów dla elementu członkowskiego, funkcji zarządzanego lub typu WinRT lub funkcji generycznych  
  
Zadeklarować parametr metody z domyślnym argumentem nie jest dozwolone. Formularz przeciążonej metody jest jednym ze sposobów obejścia tego problemu. Oznacza to zdefiniować metody o tej samej nazwie bez parametrów, a następnie zainicjuj zmiennej w treści metody.  
  
Poniższy przykład generuje C3222:  
  
```  
// C3222_2.cpp  
// compile with: /clr  
public ref class G {  
   void f( int n = 0 );   // C3222  
};  
```  
