---
title: C2993 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2993
dev_langs:
- C++
helpviewer_keywords:
- C2993
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e25e70a9d16ee166772cf03ea1837afaf14cae29
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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