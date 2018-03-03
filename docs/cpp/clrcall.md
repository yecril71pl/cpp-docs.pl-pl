---
title: __clrcall | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __clrcall_cpp
dev_langs:
- C++
helpviewer_keywords:
- __clrcall keyword [C++]
ms.assetid: 92096695-683a-40ed-bf65-0c8443572152
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d11211e90f0517c11213d7bdd2815c2f937fc79a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="clrcall"></a>__clrcall
**Dotyczące firmy Microsoft**  
  
 Określa, że funkcja może być wywoływana tylko z kodu zarządzanego.  Użyj `__clrcall` dla wszystkich funkcji wirtualnych, które będą wywoływane tylko z kodu zarządzanego. Jednak ta Konwencja wywoływania nie może służyć do funkcji, które będą wywoływane z kodu macierzystego.  
  
 Użyj `__clrcall` do zwiększenia wydajności podczas wywoływania metody z funkcją zarządzaną do funkcji wirtualnych zarządzanych lub zarządzanych funkcja funkcji zarządzanych za pomocą wskaźnika.  
  
 Punkty wejścia ma oddzielny, generowane przez kompilator funkcji. Jeśli funkcja oba punkty wejścia natywnego i zarządzanego, jeden z nich będzie rzeczywista funkcja z implementacją funkcji. Innych funkcji będzie oddzielne funkcji (thunk), która wywołuje funkcję rzeczywiste i umożliwia środowisko uruchomieniowe języka wspólnego wykonania funkcji PInvoke. Gdy funkcja jako oznaczenie `__clrcall`, wskazać implementacja funkcji musi być MSIL i funkcję punktu wejścia macierzysty nie zostanie wygenerowany.  
  
 Jeśli pobieranie adresu funkcji macierzystej, jeśli `__clrcall` nie zostanie określony, kompilator używa punktu wejścia macierzystego. `__clrcall`Wskazuje, że funkcja jest zarządzany i istnieje, nie trzeba przechodzić przez przejście od zarządzanych do kodu natywnego. W takim przypadku kompilator używa zarządzany punkt wejścia.  
  
 Podczas **/CLR** (nie **/CLR: pure** lub **/CLR: Safe**) jest używany i `__clrcall` jest nie jest używany, pobieranie adresu funkcji zawsze zwraca adres natywnego wpisu wskaż funkcji. Gdy `__clrcall` jest używana, funkcję punktu wejścia natywnego nie jest tworzony, dzięki czemu możesz uzyskać adresu funkcji zarządzanego, nie funkcję punktu wejścia thunk. Aby uzyskać więcej informacji, zobacz [podwójna konwersja bitowa adresów](../dotnet/double-thunking-cpp.md). **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015.  
  
 [/ CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md) oznacza, że wszystkie funkcje i wskaźniki funkcji są `__clrcall` i kompilator nie będzie zezwalać funkcja wewnątrz compiland może być oznaczony cokolwiek innego niż `__clrcall`. Gdy **/CLR: pure** jest używana, `__clrcall` można określić tylko dla wskaźników funkcji i deklaracje zewnętrzne.  
  
 Można bezpośrednio wywołać `__clrcall` funkcji z istniejącego kodu C++, który został skompilowany przy użyciu **/CLR** tak długo, jak ta funkcja ma implementację MSIL. `__clrcall`Nie można wywołać funkcji bezpośrednio z funkcji, które wbudowanego asm i wywołać intrinisics specyficznych dla procesora CPU, na przykład, nawet jeśli te funkcje są kompilowane przy użyciu **/CLR**.  
  
 `__clrcall`wskaźniki funkcji są przeznaczone tylko do użycia w domenie aplikacji, w którym zostały utworzone.  Zamiast przekazywanie `__clrcall` funkcji wskaźniki między domenami aplikacji, użyj <xref:System.CrossAppDomainDelegate>. Aby uzyskać więcej informacji, zobacz [i domen aplikacji Visual C++](../dotnet/application-domains-and-visual-cpp.md).  
  
## <a name="example"></a>Przykład  
 Należy pamiętać, że gdy funkcja zadeklarowana ze `__clrcall`, zostanie wygenerowany kod w razie potrzeby; na przykład, gdy jest wywoływana funkcja.  
  
```  
// clrcall2.cpp  
// compile with: /clr  
using namespace System;  
int __clrcall Func1() {  
   Console::WriteLine("in Func1");  
   return 0;  
}  
  
// Func1 hasn't been used at this point (code has not been generated),   
// so runtime returns the adddress of a stub to the function  
int (__clrcall *pf)() = &Func1;  
  
// code calls the function, code generated at difference address  
int i = pf();   // comment this line and comparison will pass  
  
int main() {  
   if (&Func1 == pf)  
      Console::WriteLine("&Func1 == pf, comparison succeeds");  
   else   
      Console::WriteLine("&Func1 != pf, comparison fails");  
  
   // even though comparison fails, stub and function call are correct  
   pf();  
   Func1();  
}  
```  
  
```Output  
in Func1  
&Func1 != pf, comparison fails  
in Func1  
in Func1  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, że wskaźnik funkcji, można zdefiniować tak, aby zadeklarować, że funkcja wskaźnik będzie można wywołać tylko z kodu zarządzanego. Dzięki temu kompilatora bezpośrednio wywołać funkcję zarządzanych i uniknąć punktu wejścia natywnego (podwójna konwersja bitowa problem).  
  
```  
// clrcall3.cpp  
// compile with: /clr  
void Test() {  
   System::Console::WriteLine("in Test");  
}  
  
int main() {  
   void (*pTest)() = &Test;  
   (*pTest)();  
  
   void (__clrcall *pTest2)() = &Test;  
   (*pTest2)();  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)