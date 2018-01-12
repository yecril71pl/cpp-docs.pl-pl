---
title: "Listy zmiennych argumentów (...) (C + +/ CLI) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- variable argument lists
- parameter arrays
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b78b244a93bea0c669c37b5df32ec7146f7ac3b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="variable-argument-lists--ccli"></a>Listy zmiennych argumentów (...) (C++/CLI)
W tym przykładzie pokazano, jak używasz `...` składni w programie Visual C++ do implementacji funkcji, które mają różną liczbą argumentów.  
  
> [!NOTE]
>  Ten temat dotyczy C + +/ CLI. Aby uzyskać informacje o korzystaniu z `...` w ISO Standard C++, zobacz [wielokropki i szablony Wariadyczne](../cpp/ellipses-and-variadic-templates.md) i wielokropki i argumenty domyślne [wyrażenia przyrostków](../cpp/postfix-expressions.md).  
  
 Parametr, który używa `...` musi być ostatnim parametrem na liście parametrów.  
  
## <a name="example"></a>Przykład  
  
### <a name="code"></a>Kod  
  
```  
// mcppv2_paramarray.cpp  
// compile with: /clr  
using namespace System;  
double average( ... array<Int32>^ arr ) {  
   int i = arr->GetLength(0);  
   double answer = 0.0;  
  
   for (int j = 0 ; j < i ; j++)  
      answer += arr[j];  
  
   return answer / i;  
}  
  
int main() {  
   Console::WriteLine("{0}", average( 1, 2, 3, 6 ));  
}  
```  
  
### <a name="output"></a>Dane wyjściowe  
  
```  
3  
```  
  
## <a name="code-example"></a>Przykład kodu  
 Poniższy przykład przedstawia sposób wywołania w języku C#, Visual C++ funkcję ze zmienną liczbą argumentów.  
  
```  
// mcppv2_paramarray2.cpp  
// compile with: /clr:safe /LD  
using namespace System;  
  
public ref class C {  
public:   
   void f( ... array<String^>^ a ) {}  
};  
```  
  
 Funkcja `f` może zostać wywołana z C# lub Visual Basic, na przykład tak, jakby była funkcja, która może zająć zmienną liczbę argumentów.  
  
 W języku C#, argument, który jest przekazywany do `ParamArray` parametru może być wywoływany przez zmienną liczbę argumentów. Poniższy przykładowy kod jest w języku C#.  
  
```  
// mcppv2_paramarray3.cs  
// compile with: /r:mcppv2_paramarray2.dll  
// a C# program  
  
public class X {  
   public static void Main() {  
      // Visual C# will generate a String array to match the   
      // ParamArray attribute  
      C myc = new C();  
      myc.f("hello", "there", "world");  
   }  
}  
```  
  
 Wywołanie `f` w programie Visual C++ może przekazać zainicjowanej tablicy lub tablicę o zmiennej długości.  
  
```  
// mcpp_paramarray4.cpp  
// compile with: /clr  
using namespace System;  
  
public ref class C {  
public:   
   void f( ... array<String^>^ a ) {}  
};  
  
int main() {  
   C ^ myc = gcnew C();  
   myc->f("hello", "world", "!!!");  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tablice](../windows/arrays-cpp-component-extensions.md)