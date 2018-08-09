---
title: Listy zmiennych argumentów (...) (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- variable argument lists
- parameter arrays
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 93cd229e93c4da36004c212cef0f09463926a0e5
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015959"
---
# <a name="variable-argument-lists--ccli"></a>Listy zmiennych argumentów (...) (C++/CLI)
W tym przykładzie pokazano, jak za pomocą `...` składni w Visual C++ do implementacji funkcji, które mają zmienną liczbę argumentów.  
  
> [!NOTE]
>  Ten temat dotyczy C + +/ interfejsu wiersza polecenia. Aby uzyskać informacje o korzystaniu z `...` w ISO Standard C++, zobacz [wielokropki i szablony Wariadyczne](../cpp/ellipses-and-variadic-templates.md) i wielokropki i argumenty domyślne w [wyrażenia przyrostków](../cpp/postfix-expressions.md).  
  
 Parametr, który używa `...` musi być ostatnim parametrem na liście parametrów.  
  
## <a name="example"></a>Przykład  
  
### <a name="code"></a>Kod  
  
```cpp  
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
  
```Output  
3  
```  
  
## <a name="code-example"></a>Przykład kodu  
 Poniższy przykład pokazuje sposób wywoływania z kodu C# funkcji Visual C++, która przyjmuje zmienną liczbę argumentów.  
  
```cpp  
// mcppv2_paramarray2.cpp  
// compile with: /clr:safe /LD  
using namespace System;  
  
public ref class C {  
public:   
   void f( ... array<String^>^ a ) {}  
};  
```  
  
 Funkcja `f` może być wywoływana z języka C# lub Visual Basic, na przykład tak, jakby była to funkcja, która może przyjąć zmienną liczbę argumentów.  
  
 W języku C# argument, który jest przekazywany do `ParamArray` parametru może być wywoływany przez zmienną liczbę argumentów. Poniższy przykładowy kod jest w języku C#.  
  
```cs  
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
  
 Wywołanie `f` w programie Visual C++ można przekazać zainicjowanej tablicy lub tablicy o zmiennej długości.  
  
```cpp  
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