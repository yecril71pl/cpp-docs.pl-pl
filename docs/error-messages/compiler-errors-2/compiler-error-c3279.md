---
title: "C3279 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3279
dev_langs: C++
helpviewer_keywords: C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 16bb13d226b6d4d5d5846f8302070bf0c9579cfb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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