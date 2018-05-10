---
title: Funkcje ogólne (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], generic
- generic methods
- generics [C++], functions
- methods [C++], generic
- generic functions
ms.assetid: 8e409364-58f9-4360-b486-e7d555e0c218
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 66eb27b28a1b18942c0a8a9a77a877a2f0b2ef8c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="generic-functions-ccli"></a>Funkcje ogólne (C++/CLI)
Funkcja generyczna jest funkcja, która jest zadeklarowana za pomocą parametrów typu. Po wywołaniu, rzeczywiste typy są używane zamiast parametrów typu.  
  
## <a name="all-platforms"></a>Wszystkie platformy  
 **Uwagi**  
  
 Ta funkcja nie ma zastosowania do wszystkich platform.  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 **Uwagi**  
  
 Ta funkcja nie jest obsługiwana w środowisku wykonawczym systemu Windows.  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
 Funkcja generyczna jest funkcja, która jest zadeklarowana za pomocą parametrów typu. Po wywołaniu, rzeczywiste typy są używane zamiast parametrów typu.  
  
 **Składnia**  
  
```  
[attributes] [modifiers]  
return-type identifier<type-parameter identifier(s)>  
[type-parameter-constraints clauses]  
  
([formal-parameters])  
{function-body}  
```  
  
 **Parametry**  
  
 *atrybuty* (opcjonalnie)  
 Dodatkowe informacje deklaratywne. Aby uzyskać więcej informacji na atrybuty i klasy atrybutów Zobacz atrybutów.  
  
 *Modyfikatory* (opcjonalnie)  
 Modyfikator dla funkcji, np. static.  `virtual` nie jest dozwolona, ponieważ metody wirtualne nie może być rodzajowy.  
  
 *zwracanego typu*  
 Typ zwracany przez metodę. Jeśli typem zwracanym jest void, brak wartości zwracanej jest wymagany.  
  
 *Identyfikator*  
 Nazwa funkcji.  
  
 *identyfikatory parametr typu*  
 Lista identyfikatorów rozdzielonych przecinkami.  
  
 *parametrów formalnych* (opcjonalnie)  
 Lista parametrów.  
  
 *Typ — parametr ograniczenia — klauzule*  
 To określa ograniczenia dotyczące typów, które mogą być używane jako argumentów typu i ma postać określone w [ograniczenia dotyczące parametrów typu ogólnego (C + +/ CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md).  
  
 *treść funkcji*  
 Treść metody, która może odwoływać się do identyfikatorów parametru typu.  
  
 **Uwagi**  
  
 Funkcje ogólne są funkcje zadeklarowany z parametrem typu ogólnego. Mogą być metod w funkcje klasy lub struktury lub autonomiczne. Pojedyncza deklaracja ogólnego niejawnie deklaruje element rodziny funkcji, które różnią się tylko w celu zastąpienia innego typu rzeczywistego parametru typu ogólnego.  
  
 W programie Visual C++ nie można zadeklarować klasy lub struktury konstruktorów z parametrami typu ogólnego.  
  
 Wywołuje się, parametr typu ogólnego jest zamieniana rzeczywistego typu. Rzeczywisty typ może być jawnie określona w nawiasach, używając składni podobnej do wywołania funkcji szablonu. Jeśli wywoływana bez parametrów typu, kompilator będzie podejmować próby ustalenia typu rzeczywistego z parametry podane w wywołaniu funkcji. Jeśli argument danego typu nie można wywnioskować z parametrów użytych, kompilator zgłosi błąd.  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 Poniższy przykładowy kod przedstawia ogólny funkcji.  
  
```  
// generics_generic_function_1.cpp  
// compile with: /clr  
generic <typename ItemType>  
void G(int i) {}  
  
ref struct A {  
   generic <typename ItemType>  
   void G(ItemType) {}  
  
   generic <typename ItemType>  
   static void H(int i) {}  
};  
  
int main() {  
   A myObject;  
  
   // generic function call  
   myObject.G<int>(10);  
  
   // generic function call with type parameters deduced  
   myObject.G(10);  
  
   // static generic function call  
   A::H<int>(10);  
  
   // global generic function call  
   G<int>(10);  
}  
```  
  
 **Przykład**  
  
 Funkcje ogólne może być przeciążony oparte na podpis lub argumentów, liczba parametrów typu w funkcji. Ponadto funkcje ogólne można przeciążać z funkcjami nieogólnego o takiej samej nazwie, tak długo, jak w niektórych parametrów typu są różne funkcje. Na przykład można przeciążać, następujące funkcje:  
  
```  
// generics_generic_function_2.cpp  
// compile with: /clr /c  
ref struct MyClass {  
   void MyMythod(int i) {}  
  
   generic <class T>   
   void MyMythod(int i) {}  
  
   generic <class T, class V>   
   void MyMythod(int i) {}  
};  
```  
  
 **Przykład**  
  
 W poniższym przykładzie użyto funkcji ogólne do znajdowania pierwszego elementu w tablicy. Deklaruje `MyClass`, który dziedziczy z klasy podstawowej `MyBaseClass`. `MyClass` Zawiera ogólne funkcję `MyFunction`, które wywołuje innej funkcji ogólnego, `MyBaseClassFunction`, w obrębie klasy podstawowej. W **głównego**, ogólna funkcja `MyFunction`, jest wywoływana przy użyciu argumentów innego typu.  
  
```  
// generics_generic_function_3.cpp  
// compile with: /clr  
using namespace System;  
  
ref class MyBaseClass {  
protected:  
   generic <class ItemType>  
   ItemType MyBaseClassFunction(ItemType item) {  
      return item;  
   }  
};  
  
ref class MyClass: public MyBaseClass {  
public:  
   generic <class ItemType>  
   ItemType MyFunction(ItemType item) {  
      return MyBaseClass::MyBaseClassFunction<ItemType>(item);  
   }  
};  
  
int main() {  
   MyClass^ myObj = gcnew MyClass();  
  
   // Call MyFunction using an int.  
   Console::WriteLine("My function returned an int: {0}",  
                           myObj->MyFunction<int>(2003));  
  
   // Call MyFunction using a string.  
   Console::WriteLine("My function returned a string: {0}",  
   myObj->MyFunction<String^>("Hello generic functions!"));  
}  
```  
  
 **Output**  
  
```Output  
My function returned an int: 2003  
My function returned a string: Hello generic functions!  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)   
 [Typy ogólne](../windows/generics-cpp-component-extensions.md)