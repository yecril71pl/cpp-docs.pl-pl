---
title: Typy ogólne i szablony (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generics [C++], vs. templates
- templates, C++
ms.assetid: 63adec79-b1dc-4a1a-a21d-b8a72a8fce31
ms.openlocfilehash: 567286ee24e9df968b2d352489fe12f2735854eb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172350"
---
# <a name="generics-and-templates-ccli"></a>Typy ogólne i szablony (C++/CLI)

Typy ogólne i szablony są funkcjami językowymi, które zapewniają obsługę typów sparametryzowanych. Są one jednak różne i mają różne zastosowania. Ten temat zawiera omówienie wielu różnic.

Aby uzyskać więcej informacji, zobacz [środowisko wykonawcze systemu Windows i szablony zarządzane](windows-runtime-and-managed-templates-cpp-component-extensions.md).

## <a name="comparing-templates-and-generics"></a>Porównywanie szablonów i typów ogólnych

Kluczowe różnice między typami ogólnymi C++ i szablonami:

- Typy ogólne są ogólne do momentu zastąpienia typów do nich w czasie wykonywania. Szablony są wyspecjalizowane w czasie kompilacji, więc nie są nadal sparametryzowane typy w czasie wykonywania

- Środowisko uruchomieniowe języka wspólnego obsługuje w specjalny sposób typy ogólne. Ze względu na to, że środowisko uruchomieniowe wie o typach ogólnych, podczas odwoływania się do zestawu zawierającego typ ogólny mogą zostać zastąpione określone typy. Szablony, w przeciwieństwie, rozpoznawanie zwykłych typów w czasie kompilacji, a typy powstające mogą nie być wyspecjalizowane w innych zestawach.

- Typy ogólne wyspecjalizowane w dwóch różnych zestawach z tymi samymi typami argumentów są tego samego typu. Szablony wyspecjalizowane w dwóch różnych zestawach z tymi samymi typami argumentów są uznawane za przez środowisko uruchomieniowe jako różne typy.

- Typy ogólne są generowane jako pojedynczy fragment kodu wykonywalnego, który jest używany dla wszystkich argumentów typu odwołania (nie jest to prawdziwe dla typów wartości, które mają unikatową implementację na typ wartości). Kompilator JIT wie o typach ogólnych i jest w stanie zoptymalizować kod dla typów referencyjnych lub wartości, które są używane jako argumenty typu. Szablony generują odrębny kod środowiska uruchomieniowego dla każdej specjalizacji.

- Typy ogólne nie zezwalają na parametry szablonu niebędącego typem, takie jak `template <int i> C {}`. Umożliwiają one korzystanie z szablonów.

- Typy ogólne nie umożliwiają jawnej specjalizacji (to jest implementacja niestandardowa szablonu dla określonego typu). Szablony.

- Typy ogólne nie zezwalają na częściową specjalizację (implementację niestandardową dla podzbioru argumentów typu). Szablony.

- Typy ogólne nie zezwalają na użycie parametru typu jako klasy bazowej dla typu ogólnego. Szablony.

- Szablony obsługują parametry szablonu szablonu (np. `template<template<class T> class X> class MyClass`), ale generyczne nie.

## <a name="combining-templates-and-generics"></a>Łączenie szablonów i typów ogólnych

Podstawowa różnica w typach ogólnych ma wpływ na tworzenie aplikacji, które łączą szablony i typy ogólne. Załóżmy na przykład, że masz klasę szablonu, dla której chcesz utworzyć otokę rodzajową, aby uwidocznić ten szablon w innych językach jako ogólny. Nie można utworzyć generycznego parametru typu Take, który następnie przechodzi do szablonu, ponieważ szablon musi mieć ten parametr typu w czasie kompilacji, ale generyczny nie będzie rozpoznawać parametru typu do czasu wykonania. Zagnieżdżanie szablonu wewnątrz generycznej nie będzie działać, ponieważ nie ma możliwości rozwinięcia szablonów w czasie kompilacji dla dowolnych typów ogólnych, które mogą zostać utworzone w czasie wykonywania.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład pokazuje prosty przykład użycia szablonów i rodzajowych. W tym przykładzie Klasa szablonu przekazuje swój parametr do typu ogólnego. Odwrócenie nie jest możliwe.

Tego idiom można użyć, gdy chcesz skompilować istniejący ogólny interfejs API z kodem szablonu, który jest lokalny dla zestawu C++/CLI, lub gdy musisz dodać dodatkową warstwę parametryzacja do typu ogólnego, aby skorzystać z pewnych funkcji szablonów nieobsługiwanych przez typy ogólne.

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

[Typy ogólne](generics-cpp-component-extensions.md)
