---
title: C3279 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3279
dev_langs:
- C++
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a86f3dd637f84901559c4be8443a81425347237
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3279"></a>C3279 błąd kompilatora
częściowe i jawne specjalizacje jak również jawne utworzenia wystąpień szablonów klasy zadeklarowany w przestrzeni nazw cli są niedozwolone.  
  
 `cli` Przestrzeń nazw jest zdefiniowana przez firmę Microsoft i zawiera pseudo-szablonów. Kompilator Visual C++ pozwala zdefiniowane przez użytkownika, częściowe i jawne specjalizacje i jawne utworzenia wystąpień szablonów klasy w tej przestrzeni nazw.  
  
 Poniższy przykład generuje C3279:  
  
```  
// C3279.cpp  
// compile with: /clr  
namespace cli {  
   template <> ref class array<int> {};   // C3279  
   template <typename T> ref class array<T, 2> {};   // C3279  
}  
```