---
title: Funkcje ogólne (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- functions [C++], generic
- generic methods
- generics [C++], functions
- methods [C++], generic
- generic functions
ms.assetid: 8e409364-58f9-4360-b486-e7d555e0c218
ms.openlocfilehash: a4a1702c8b9902f5265a8a5f92316d7c82751609
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349570"
---
# <a name="generic-functions-ccli"></a>Funkcje ogólne (C++/CLI)

Funkcja ogólna jest funkcją, która jest zadeklarowana za pomocą parametrów typu. Gdy zostanie wywołana, rzeczywiste typy są używane zamiast parametrów typu.

## <a name="all-platforms"></a>Wszystkie platformy

### <a name="remarks"></a>Uwagi

Ta funkcja nie ma zastosowania do wszystkich platform.

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

### <a name="remarks"></a>Uwagi

Ta funkcja nie jest obsługiwana w środowisku uruchomieniowym Windows.

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

Funkcja ogólna jest funkcją, która jest zadeklarowana za pomocą parametrów typu. Gdy zostanie wywołana, rzeczywiste typy są używane zamiast parametrów typu.

### <a name="syntax"></a>Składnia

```cpp
[attributes] [modifiers]
return-type identifier<type-parameter identifier(s)>
[type-parameter-constraints clauses]

([formal-parameters])
{function-body}
```

### <a name="parameters"></a>Parametry

*Atrybuty*<br/>
(Opcjonalnie) Dodatkowe informacje deklaratywnego. Aby uzyskać więcej informacji o atrybuty i klasy atrybutów Zobacz atrybutów.

*Modyfikatory*<br/>
(Opcjonalnie) Modyfikator właściwy dla funkcji, takich jak statyczny.  **wirtualne** jest niedozwolona, ponieważ metody wirtualne nie może być ogólny.

*zwracany typ*<br/>
Typ zwracany przez metodę. Jeśli typ zwracany void, nie zwraca wartości jest wymagana.

*Identyfikator*<br/>
Nazwa funkcji.

*identyfikatory parametr typu*<br/>
Lista identyfikatorów rozdzielonych przecinkami.

*parametrów formalnych*<br/>
(Opcjonalnie) Lista parametrów.

*type-parameter-constraints-clauses*<br/>
To określa ograniczenia typów, które mogą być używane jako argumenty typu i ma postać określone w [ograniczenia dotyczące parametrów typu ogólnego (C++sposób niezamierzony)](constraints-on-generic-type-parameters-cpp-cli.md).

*treść funkcji*<br/>
Treść metody, która może odwoływać się do identyfikatorów parametru typu.

### <a name="remarks"></a>Uwagi

Funkcje ogólne są funkcje zadeklarowane za pomocą parametru typu ogólnego. Mogą one zostać metod w funkcjach klasy lub struktury lub autonomiczne. Jednej deklaracji ogólnej niejawnie deklaruje rodzinę funkcji, które różnią się tylko w celu zastąpienia inny typ rzeczywistego parametru typu ogólnego.

Konstruktor klasy lub struktury nie mogą być deklarowane przy użyciu parametrów typu genetycznego.

Gdy zostanie wywołana, parametr typu ogólnego jest zastępowany przez rzeczywisty typ. Rzeczywisty typ może być jawnie określona w nawiasach przy użyciu składni podobnej do wywołania funkcji szablonu. Jeśli wywołana bez parametrów typu, kompilator spróbuje ustalić rzeczywisty typ z parametry podane w wywołaniu funkcji. Jeśli argument zamierzony typu nie można wywnioskować z parametrów użytych, kompilator zgłosi błąd.

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

W poniższym przykładzie kodu pokazano funkcja ogólna.

```cpp
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

Funkcje ogólne mogą być przeciążane na podstawie podpisu lub argumentów, liczba parametrów typu dla funkcji. Ponadto ogólne funkcje mogą być przeciążone funkcje nieogólnego o takiej samej nazwie, tak długo, jak funkcje różnią się w niektórych parametrach typu. Na przykład mogą być przeciążone następujące funkcje:

```cpp
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

W poniższym przykładzie użyto funkcja ogólna, można znaleźć pierwszego elementu w tablicy. Deklaruje `MyClass`, który dziedziczy z klasy bazowej `MyBaseClass`. `MyClass` zawiera funkcję ogólną `MyFunction`, która wywołuje inną funkcję ogólny, `MyBaseClassFunction`, w ramach klasy bazowej. W `main`, funkcja ogólna `MyFunction`, jest wywoływana przy użyciu różnych typów argumentów.

```cpp
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

```Output
My function returned an int: 2003
My function returned a string: Hello generic functions!
```

## <a name="see-also"></a>Zobacz także

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)<br/>
[Typy ogólne](generics-cpp-component-extensions.md)
