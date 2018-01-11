---
title: "C2993 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2993
dev_langs: C++
helpviewer_keywords: C2993
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3715e2183c8194fe7bcf2613cbee3a0052588385
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2993"></a>C2993 błąd kompilatora
"identyfikator": niedozwolony typ dla parametru szablonu bez typu "parameter"  
  
 Nie można zadeklarować struktury lub Unii argumentu szablonu. Użycie wskaźników do przekazania struktur i Unii jako parametry szablonu.  
  
 Poniższy przykład generuje C2993:  
  
```  
// C2993.cpp  
// compile with: /c  
// C2993 expected  
struct MyStruct {  
   int a;char b;  
};  
  
template <class T, struct MyStruct S>   // C2993  
  
// try the following line instead  
// template <class T, struct MyStruct * S>  
class CMyClass {};  
```  
  
 Ten błąd zostanie również wygenerowany wyniku pracy zgodność kompilatora, która została wykonana w Visual Studio .NET 2003: zmiennoprzecinkowa parametrów szablonu bez typu nie jest dozwolone. C++ standard nie zezwala na zmiennoprzecinkowej parametrów szablonu bez typu.  
  
 Jeśli jest to funkcja szablon, użyj argumentu funkcji, aby przekazać wartość zmiennoprzecinkowa punktu parametru szablonu bez typu (ten kod będzie prawidłowy w wersjach programu Visual Studio .NET 2003 i Visual Studio .NET Visual C++). Jeśli szablon klasy, nie istnieje obejście łatwe.  
  
```  
// C2993b.cpp  
// compile with: /c  
template<class T, float f> void func(T) {}   // C2993  
  
// OK  
template<class T>   void func2(T, float) {}  
```