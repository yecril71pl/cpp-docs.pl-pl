---
title: "w przypadku każdego w | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::foreach
- for
- each
- in
dev_langs: C++
helpviewer_keywords: for each keyword [C++]
ms.assetid: 0c3a364b-2747-43f3-bb8d-b7d3b7023f79
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a1d89552bd299edc778b06bd01ee185c275c45db
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="for-each-in"></a>for each, in
Wykonuje iterację przez tablicę lub kolekcję. To niestandardowe słowo kluczowe jest dostępne zarówno w projektach C++/CLI, jak i macierzystych projektach C++. Jego stosowanie nie jest jednak zalecane. Należy rozważyć użycie standardowego [opartej na zakresie — instrukcja (C++)](../cpp/range-based-for-statement-cpp.md) zamiast tego.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 **Składnia**  
  
```  
  
      for each (typeidentifierinexpression) {  
   statements  
}  
  
```  
  
 **Parametry**  
  
 `type`  
 Typ `identifier`.  
  
 `identifier`  
 Zmienna iteracyjna, która reprezentuje element kolekcji.  Gdy `identifier` jest [Operator odwołania śledzenia](../windows/tracking-reference-operator-cpp-component-extensions.md), można zmodyfikować elementu.  
  
 `expression`  
 Wyrażenie tablicy lub kolekcja. Element kolekcji musi być w taki sposób, że kompilator można przekonwertować go na `identifier` typu.  
  
 `statements`  
 Jedna lub więcej instrukcji do wykonania.  
  
 **Uwagi**  
  
 `for each` Instrukcji jest używany do iterowania po kolekcji. Możesz modyfikować elementy w kolekcji, ale nie możesz dodawać ani usuwać elementów.  
  
 *Instrukcje* są wykonywane dla każdego elementu w tablicy lub kolekcji. Po ukończeniu iteracji dla wszystkich elementów w kolekcji, sterowanie jest przekazywane do instrukcji następującej `for each` bloku.  
  
 `for each`i `in` są [kontekstowe słowa kluczowe](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
 Informacje dodatkowe:  
  
-   [Iterowanie za pomocą dla każdej instrukcji w kolekcji bibliotek. C++ Standard](../dotnet/iterating-over-stl-collection-by-using-for-each.md)  
  
-   [Porady: iterowanie przez tablice za pomocą instrukcji for each](../dotnet/how-to-iterate-over-arrays-with-for-each.md)  
  
-   [Porady: iterowanie przez kolekcję ogólną za pomocą instrukcji for each](../dotnet/how-to-iterate-over-a-generic-collection-with-for-each.md)  
  
-   [Porady: iterowanie przez kolekcję zdefiniowanych przez użytkownika za pomocą for each](../dotnet/how-to-iterate-over-a-user-defined-collection-with-for-each.md)  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
### <a name="example"></a>Przykład  
 Ten przykład przedstawia sposób użycia `for each` do iterowania po ciągu.  
  
```  
// for_each_string1.cpp  
// compile with: /ZW  
#include <stdio.h>  
using namespace Platform;  
  
ref struct MyClass {  
   property String^ MyStringProperty;  
};  
  
int main() {  
   String^ MyString = ref new String("abcd");  
  
   for each ( char c in MyString )  
      wprintf("%c", c);  
  
   wprintf("/n");  
  
   MyClass^ x = ref new MyClass();  
   x->MyStringProperty = "Testing";  
  
   for each( char c in x->MyStringProperty )  
      wprintf("%c", c);  
}  
```  
  
 **Dane wyjściowe**  
  
```Output  
abcd  
  
Testing  
```  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
 **Uwagi**  
  
 Składnia CLR jest taka sama jak **wszystkich środowisk uruchomieniowych** składni, z wyjątkiem w następujący sposób.  
  
 *wyrażenie*  
 Wyrażenie tablicy zarządzanej lub kolekcja. Element kolekcji musi być tak, aby przekonwertować ją z kompilatora <xref:System.Object> do *identyfikator* typu.  
  
 *wyrażenie* obliczane do typu, który implementuje <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, lub typu, który definiuje `GetEnumerator` implementującej metody albo zwraca wartość typu <xref:System.Collections.IEnumerator> lub deklaruje wszystkie metody, które są zdefiniowane w `IEnumerator`.  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="example"></a>Przykład  
 Ten przykład przedstawia sposób użycia `for each` do iterowania po ciągu.  
  
```  
// for_each_string2.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct MyClass {  
   property String ^ MyStringProperty;  
};  
  
int main() {  
   String ^ MyString = gcnew String("abcd");  
  
   for each ( Char c in MyString )  
      Console::Write(c);  
  
   Console::WriteLine();  
  
   MyClass ^ x = gcnew MyClass();  
   x->MyStringProperty = "Testing";  
  
   for each( Char c in x->MyStringProperty )  
      Console::Write(c);  
}  
```  
  
 **Dane wyjściowe**  
  
```Output  
abcd  
  
Testing   
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)