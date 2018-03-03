---
title: "C3222 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3222
dev_langs:
- C++
helpviewer_keywords:
- C3222
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0028b9540127433bdbd17b01f1a5a3dfd9361558
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
