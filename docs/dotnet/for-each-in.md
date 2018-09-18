---
title: w przypadku każdego w | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::foreach
- for
- each
- in
dev_langs:
- C++
helpviewer_keywords:
- for each keyword [C++]
ms.assetid: 0c3a364b-2747-43f3-bb8d-b7d3b7023f79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a55425c891999142fe32ae08125cce22728daffa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040699"
---
# <a name="for-each-in"></a>for each, in
Wykonuje iterację przez tablicę lub kolekcję. To niestandardowe słowo kluczowe jest dostępne zarówno w projektach C++/CLI, jak i macierzystych projektach C++. Jego stosowanie nie jest jednak zalecane. Rozważ użycie standardowego [Range-based for Statement (C++)](../cpp/range-based-for-statement-cpp.md) zamiast tego.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 **Składnia**  
  
```  
  
      for each (typeidentifierinexpression) {  
   statements  
}  
  
```  
  
 **Parametry**  
  
*Typ*<br/>
Typ `identifier`.  
  
*Identyfikator*<br/>
Zmienna iteracyjna, która reprezentuje element kolekcji.  Gdy `identifier` jest [Tracking Reference Operator](../windows/tracking-reference-operator-cpp-component-extensions.md), można zmodyfikować element.  
  
*Wyrażenie*<br/>
Wyrażenie tablicy lub kolekcja. Element kolekcji musi być tak, aby kompilator mógł go konwertować do `identifier` typu.  
  
*Instrukcje*<br/>
Jedna lub więcej instrukcji do wykonania.  
  
 **Uwagi**  
  
 `for each` Instrukcja jest używane do iterowania po kolekcji. Możesz modyfikować elementy w kolekcji, ale nie możesz dodawać ani usuwać elementów.  
  
 *Instrukcji* są wykonywane dla każdego elementu w tablicy lub kolekcji. Po zakończeniu iteracji wszystkich elementów w kolekcji formant jest przekazywany do kolejnej instrukcji `for each` bloku.  
  
 `for each` i `in` są [kontekstowymi słowami kluczowymi](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
 Informacje dodatkowe:  
  
-   [Iterowanie przez standardową kolekcję bibliotek C++ za pomocą instrukcji for each](../dotnet/iterating-over-stl-collection-by-using-for-each.md)  
  
-   [Instrukcje: iterowanie przez tablice za pomocą instrukcji for each](../dotnet/how-to-iterate-over-arrays-with-for-each.md)  
  
-   [Instrukcje: iterowanie przez kolekcję ogólną za pomocą instrukcji for each](../dotnet/how-to-iterate-over-a-generic-collection-with-for-each.md)  
  
-   [Instrukcje: iterowanie przez kolekcję zdefiniowaną przez użytkownika za pomocą instrukcji for each](../dotnet/how-to-iterate-over-a-user-defined-collection-with-for-each.md)  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
### <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak używać `for each` do iteracji przez ciąg.  
  
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
  
 **Output**  
  
```Output  
abcd  
  
Testing  
```  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
 **Uwagi**  
  
 Składnia CLR jest taka sama jak **wszystkie środowiska wykonawcze** składnię, z wyjątkiem w następujący sposób.  
  
 *Wyrażenie*  
 Wyrażenie tablicy zarządzanej lub kolekcja. Element kolekcji musi być tak, aby kompilator mógł go skonwertować z <xref:System.Object> do *identyfikator* typu.  
  
 *wyrażenie* daje w wyniku typ implementujący <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, lub typ, który definiuje `GetEnumerator` metody, która albo zwraca typ, który implementuje <xref:System.Collections.IEnumerator> albo deklaruje wszystkie metody, które są zdefiniowane w `IEnumerator`.  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak używać `for each` do iteracji przez ciąg.  
  
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
  
 **Output**  
  
```Output  
abcd  
  
Testing   
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)