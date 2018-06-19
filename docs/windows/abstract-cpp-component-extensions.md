---
title: abstract (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- abstract
- abstract_cpp
dev_langs:
- C++
helpviewer_keywords:
- abstract keyword [C++]
ms.assetid: cbae3408-0378-4ac8-b70d-c016b381a6d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dcaef98df96b54025cd44a52a2e27a7bc5a83545
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857558"
---
# <a name="abstract--c-component-extensions"></a>abstract (C++ Component Extensions)
`abstract` — Słowo kluczowe deklaruje albo:  
  
-   Typem może służyć jako typu podstawowego, ale nie można utworzyć wystąpienia samego typu.  
  
-   Funkcja członkowska typu można zdefiniować tylko w typie pochodnym.  
  
## <a name="all-platforms"></a>Wszystkie platformy  
 **Składnia**  
  
```  
  
      class-declaration  
      class-identifier  
      abstract {}  
virtualreturn-typemember-function-identifier() abstract ;  
  
```  
  
 **Uwagi**  
  
 Pierwszy przykładowej składni deklaruje klasę, aby być abstrakcyjne. *Deklaracji klasy* składnik może być natywna deklaracja C++ (`class` lub `struct`), lub deklaracji rozszerzenia języka C++ (`ref class` lub `ref struct`) Jeśli **/ZW** lub **/CLR** określono opcję kompilatora.  
  
 Druga Przykładowa składnia deklaruje funkcję wirtualny element członkowski jako abstrakcyjny. Deklarowanie abstrakcyjna funkcja jest taka sama jak deklarowanie go czystej funkcji wirtualnej. Deklarowanie abstrakcyjna funkcja elementu członkowskiego powoduje także, że otaczającej klasy, która ma być zadeklarowany jako abstrakcyjny.  
  
 `abstract` — Słowo kluczowe jest obsługiwana w kodu natywnego i specyficzne dla platformy; oznacza to, może zostać skompilowany bez **/ZW** lub **/CLR** — opcja kompilatora.  
  
 Można wykrywać w czasie kompilacji, jeśli typ jest abstrakcyjny z `__is_abstract(type)` typu cechy. Aby uzyskać więcej informacji, zobacz [Obsługa cech typu w kompilatorze](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
 `abstract` — Słowo kluczowe jest specyfikator override kontekstowa. Aby uzyskać więcej informacji na temat kontekstowe słowa kluczowe, zobacz [słowa kluczowe Context-Sensitive](../windows/context-sensitive-keywords-cpp-component-extensions.md). Aby uzyskać więcej informacji na temat specyfikatorów zastąpienia, zobacz [porady: deklarowanie specyfikatorów zastąpienia w kompilacjach macierzystych](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 Aby uzyskać więcej informacji, zobacz [Ref klas i struktur](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx).  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 Poniższy przykład kodu generuje błąd, ponieważ klasa `X` jest oznaczony jako `abstract`.  
  
```  
// abstract_keyword.cpp  
// compile with: /clr  
ref class X abstract {  
public:  
   virtual void f() {}  
};  
  
int main() {  
   X ^ MyX = gcnew X;   // C3622  
}  
```  
  
 **Przykład**  
  
 Poniższy przykład kodu generuje błąd, ponieważ metoda tworzy natywnego klasy, która jest oznaczony jako `abstract`. Ten błąd wystąpi z lub bez **/CLR** — opcja kompilatora.  
  
```  
// abstract_keyword_2.cpp  
class X abstract {  
public:  
   virtual void f() {}  
};  
  
int main() {  
   X * MyX = new X; // C3622: 'X': a class declared as 'abstract'  
                    // cannot be instantiated. See declaration of 'X'}  
  
```  
  
 **Przykład**  
  
 Poniższy przykład kodu generuje błąd, ponieważ funkcja `f` obejmuje definicję, ale jest oznaczony jako `abstract`. Końcowej instrukcji w tym przykładzie pokazuje, że deklarowania funkcji wirtualnych abstrakcyjnej odpowiednikiem deklarowanie czystej funkcji wirtualnej.  
  
```  
// abstract_keyword_3.cpp  
// compile with: /clr  
ref class X {  
public:  
   virtual void f() abstract {}   // C3634  
   virtual void g() = 0 {}   // C3634  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)