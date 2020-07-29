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
ms.openlocfilehash: 3d648a23176786985a7ca1e22165c7c5a695e601
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216014"
---
# <a name="generic-functions-ccli"></a>Funkcje ogólne (C++/CLI)

Funkcja generyczna jest funkcją zadeklarowaną z parametrami typu. Po wywołaniu, zamiast parametrów typu są używane rzeczywiste typy.

## <a name="all-platforms"></a>Wszystkie platformy

### <a name="remarks"></a>Uwagi

Ta funkcja nie ma zastosowania do wszystkich platform.

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

### <a name="remarks"></a>Uwagi

Ta funkcja nie jest obsługiwana w środowisko wykonawcze systemu Windows.

### <a name="requirements"></a>Wymagania

Opcja kompilatora:`/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

Funkcja generyczna jest funkcją zadeklarowaną z parametrami typu. Po wywołaniu, zamiast parametrów typu są używane rzeczywiste typy.

### <a name="syntax"></a>Składnia

```cpp
[attributes] [modifiers]
return-type identifier<type-parameter identifier(s)>
[type-parameter-constraints clauses]

([formal-parameters])
{function-body}
```

### <a name="parameters"></a>Parametry

*Attributes*<br/>
Obowiązkowe Dodatkowe informacje deklaratywne. Aby uzyskać więcej informacji na temat atrybutów i klas atrybutów, zobacz atrybuty.

*Modyfikatory*<br/>
Obowiązkowe Modyfikator funkcji, np. static.  **`virtual`** nie jest dozwolone, ponieważ metody wirtualne nie mogą być ogólne.

*Typ zwracany*<br/>
Typ zwracany przez metodę. Jeśli zwracanym typem jest void, nie jest wymagana żadna wartość zwracana.

*identyfikatora*<br/>
Nazwa funkcji.

*identyfikatory parametrów typu*<br/>
Lista identyfikatorów rozdzielonych przecinkami.

*parametry formalne*<br/>
Obowiązkowe Lista parametrów.

*ograniczenia parametrów typu-Parameter-klauzule*<br/>
Określa ograniczenia dotyczące typów, które mogą być używane jako argumenty typu, i przyjmuje formularz określony w [ograniczeniach dla parametrów typu ogólnego (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md).

*treść funkcji*<br/>
Treść metody, która może odwoływać się do identyfikatorów parametrów typu.

### <a name="remarks"></a>Uwagi

Funkcje ogólne to funkcje zadeklarowane za pomocą parametru typu ogólnego. Mogą być metodami w klasie lub strukturze lub funkcjach autonomicznych. Pojedyncza deklaracja generyczna niejawnie deklaruje rodzinę funkcji, które różnią się tylko zastępowaniem innego rzeczywistego typu dla parametru typu ogólnego.

Nie można zadeklarować klasy lub konstruktora struktury przy użyciu parametrów typu ogólnego.

Gdy jest wywoływana, parametr typu ogólnego jest zastępowany rzeczywistym typem. Rzeczywisty typ może być jawnie określony w nawiasach ostrych przy użyciu składni podobnej do wywołania funkcji szablonu. Jeśli wywoływana bez parametrów typu, kompilator podejmie próbę ustalenia rzeczywistego typu z parametrów dostarczonych w wywołaniu funkcji. Jeśli odpowiedni argument typu nie może zostać wywnioskowany na podstawie używanych parametrów, kompilator zgłosi błąd.

### <a name="requirements"></a>Wymagania

Opcja kompilatora:`/clr`

### <a name="examples"></a>Przykłady

Poniższy przykład kodu demonstruje funkcję ogólną.

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

Funkcje generyczne mogą być przeciążone na podstawie podpisu lub liczby argumentów, liczby parametrów typu w funkcji. Ponadto funkcje generyczne mogą być przeciążone przy użyciu funkcji innych niż ogólne o tej samej nazwie, o ile funkcje te różnią się w niektórych parametrach typu. Na przykład następujące funkcje mogą być przeciążone:

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

Poniższy przykład używa funkcji generycznej, aby znaleźć pierwszy element w tablicy. Deklaruje `MyClass` , że dziedziczy z klasy bazowej `MyBaseClass` . `MyClass`zawiera funkcję generyczną, `MyFunction` która wywołuje inną funkcję rodzajową, `MyBaseClassFunction` w ramach klasy bazowej. W programie `main` Funkcja generyczna `MyFunction` jest wywoływana przy użyciu różnych argumentów typu.

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

[Rozszerzenia składników dla platform .NET i platformy UWP](component-extensions-for-runtime-platforms.md)<br/>
[Typy ogólne](generics-cpp-component-extensions.md)
