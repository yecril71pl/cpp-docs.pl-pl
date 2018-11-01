---
title: Typy ogólne i szablony (C + +/ CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generics [C++], vs. templates
- templates, C++
ms.assetid: 63adec79-b1dc-4a1a-a21d-b8a72a8fce31
ms.openlocfilehash: 81b2812faa2fcb7acfdc272474d22039afa24655
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660057"
---
# <a name="generics-and-templates-ccli"></a>Typy ogólne i szablony (C + +/ CLI)

Typy ogólne i szablony są obie funkcje językowe, pozwalające na obsługę typów sparametryzowanych. Jednak różnią się i mają różne sposoby zastosowania. W tym temacie omówiono wiele różnic.

Aby uzyskać więcej informacji, zobacz [środowisko wykonawcze Windows i zarządzane szablony](../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md).

## <a name="comparing-templates-and-generics"></a>Porównywanie szablonami i typami ogólnymi

Podstawowe różnice między typy ogólne i szablony języka C++:

- Typy ogólne są rodzajowe, dopóki typy są zastępowane dla nich w czasie wykonywania. Szablony są wyspecjalizowane w czasie kompilacji, więc nie są one nadal sparametryzowanych typów w czasie wykonywania

- Środowisko uruchomieniowe języka wspólnego obsługuje określone typy ogólne w kodzie MSIL. Ponieważ środowisko uruchomieniowe wie o ogólnych, można zastąpić określonych typów dla typów ogólnych o podczas odwoływania się do zestawu zawierającego typ ogólny. Szablony, natomiast rozwiązania do zwykłych typów w czasie kompilacji, a wynikowy typów może nie być specjalizujących się w innych zestawów.

- Typy ogólne specjalizujących się w dwóch różnych zestawów przy użyciu tego samego typu argumenty są tego samego typu. Szablony wyspecjalizowane w dwóch różnych zestawach za pomocą tego samego typu, który argumenty są uznawane za przez środowisko uruchomieniowe różnych typów.

- Typy ogólne są generowane jako pojedynczy kod wykonywalny, który jest używany dla wszystkich argumentów typu odwołania (nie jest to wartość true dla typów wartości, które mają unikatowy implementacji na typ wartości). Kompilator JIT zna typy ogólne i jest w stanie optymalizacji kodu dla typów odwołania lub wartość, które są używane jako argumenty typu. Szablony generować kod oddzielne środowiska uruchomieniowego dla każdej specjalizacji.

- Typy ogólne nie zezwalaj na parametrów szablonu bez typu, takie jak `template <int i> C {}`. Szablony umożliwiają je.

- Typy ogólne nie zezwalają na jawną specjalizacją (oznacza to, że implementacja niestandardowa szablonu dla określonego typu). Czy szablony.

- Typy ogólne nie zezwalają na częściowej specjalizacji (implementacja niestandardowa dla podzbioru argumentów typu). Czy szablony.

- Typy ogólne nie zezwalają na parametr typu ma być używany jako klasa bazowa dla typu ogólnego. Czy szablony.

- Szablony obsługują parametrów szablonu dla szablonu (np. `template<template<class T> class X> class MyClass`), ale nie typy ogólne.

## <a name="combining-templates-and-generics"></a>Łączenie z szablonami i typami ogólnymi

Podstawową różnicę w typach ogólnych ma wpływ na tworzenie aplikacji łączących się z szablonami i typami ogólnymi. Na przykład załóżmy, że masz klasą szablonu, który chcesz utworzyć otokę ogólny dla do udostępnienia tego szablonu do innych języków jako zwykły. Wypełnij ogólny nie może mieć parametr typu, który następnie przekazuje do szablonu, ponieważ szablon musi mieć parametr tego typu w czasie kompilacji, ale ogólnego rozwiąże parametr typu aż do czasu. Zagnieżdżanie wewnątrz ogólnego szablonu nie będą działać albo ponieważ nie istnieje żaden sposób rozwiń węzeł Szablony w czasie kompilacji dla dowolnych typów ogólnych, które mogła zostać utworzona w czasie wykonywania.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład pokazuje prosty przykład ze sobą przy użyciu szablonów i typy ogólne. W tym przykładzie klasa szablonu przekazuje parametr za pomocą typu ogólnego. Odwrotnej nie jest możliwe.

Tego idiomu można użyć, gdy chcesz skompilować na istniejące ogólnego interfejsu API za pomocą kodu szablonu, który jest lokalny dla C + +/ interfejsu wiersza polecenia zestawu, lub jeśli potrzebujesz dodać dodatkową warstwę parametryzacji do typu ogólnego, aby móc korzystać z niektórych funkcji szablonów nie obsługiwane b typy ogólne y.

### <a name="code"></a>Kod

```cpp
// templates_and_generics.cpp
// compile with: /clr
using namespace System;

generic <class ItemType>
ref class MyGeneric {
   ItemType m_item;

public:
   MyGeneric(ItemType item) : m_item(item) {}
   void F() {
      Console::WriteLine("F");
   }
};

template <class T>
public ref class MyRef {
MyGeneric<T>^ ig;

public:
   MyRef(T t) {
      ig = gcnew MyGeneric<T>(t);
      ig->F();
    }
};

int main() {
   // instantiate the template
   MyRef<int>^ mref = gcnew MyRef<int>(11);
}
```

```Output
F
```

## <a name="see-also"></a>Zobacz też

[Typy ogólne](../windows/generics-cpp-component-extensions.md)