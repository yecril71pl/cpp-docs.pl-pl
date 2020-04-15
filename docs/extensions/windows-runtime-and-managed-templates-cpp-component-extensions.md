---
title: Środowisko wykonawcze systemu Windows i zarządzane szablony (C++/CLI i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- templates, with CLR types
ms.assetid: cf59d16b-5514-448b-9a95-e0b4fcb616a6
ms.openlocfilehash: 5765370e611e5822b3b2d156d2eee5d21e5b453d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376306"
---
# <a name="windows-runtime-and-managed-templates-ccli-and-ccx"></a>Środowisko wykonawcze systemu Windows i zarządzane szablony (C++/CLI i C++/CX)

Szablony umożliwiają zdefiniowanie prototypu środowiska wykonawczego systemu Windows lub typ środowiska wykonawczego języka wspólnego, a następnie tworzenie wystąpienia odmian tego typu przy użyciu różnych parametrów typu szablonu.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

Można tworzyć szablony na podstawie wartości lub typów odwołań.  Aby uzyskać więcej informacji na temat tworzenia typów wartości lub odwołań, zobacz [Klasy i struktury](classes-and-structs-cpp-component-extensions.md).

Aby uzyskać więcej informacji na temat standardowych szablonów klas języka C++, zobacz [Szablony klas](../cpp/class-templates.md).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

(Nie ma żadnych uwag dotyczących tej funkcji języka, które dotyczą tylko środowiska wykonawczego systemu Windows).

### <a name="requirements"></a>Wymagania

Opcja kompilatora:`/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

Istnieją pewne ograniczenia tworzenia szablonów klas z typów zarządzanych, które są przedstawione w poniższych przykładach kodu.

### <a name="requirements"></a>Wymagania

Opcja kompilatora:`/clr`

### <a name="examples"></a>Przykłady

Istnieje możliwość wystąpienia typu ogólnego z parametrem szablonu typu zarządzanego, ale nie można utworzyć wystąpienia szablonu zarządzanego z parametrem szablonu typu ogólnego. Jest tak, ponieważ typy ogólne są rozpoznawane w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Ogólne i szablony (C++/CLI)](generics-and-templates-visual-cpp.md).

```cpp
// managed_templates.cpp
// compile with: /clr /c

generic<class T>
ref class R;

template<class T>
ref class Z {
   // Instantiate a generic with a template parameter.
   R<T>^ r;    // OK
};

generic<class T>
ref class R {
   // Cannot instantiate a template with a generic parameter.
   Z<T>^ z;   // C3231
};
```

Typ lub funkcja rodzajowa nie może być zagnieżdżona w szablonie zarządzanym.

```cpp
// managed_templates_2.cpp
// compile with: /clr /c

template<class T> public ref class R {
   generic<class T> ref class W {};   // C2959
};
```

Nie można uzyskać dostępu do szablonów zdefiniowanych w zestawie odniesienia ze składnią języka C++/CLI, ale można użyć odbicia. Jeśli szablon nie jest tworzone, nie jest emitowany w metadanych. Jeśli szablon jest wystąpienia, tylko funkcje członkowskie odniesienia będą wyświetlane w metadanych.

```cpp
// managed_templates_3.cpp
// compile with: /clr

// Will not appear in metadata.
template<class T> public ref class A {};

// Will appear in metadata as a specialized type.
template<class T> public ref class R {
public:
   // Test is referenced, will appear in metadata
   void Test() {}

   // Test2 is not referenced, will not appear in metadata
   void Test2() {}
};

// Will appear in metadata.
generic<class T> public ref class G { };

public ref class S { };

int main() {
   R<int>^ r = gcnew R<int>;
   r->Test();
}
```

Można zmienić modyfikator zarządzany klasy w częściowej specjalizacji lub jawnej specjalizacji szablonu klasy.

```cpp
// managed_templates_4.cpp
// compile with: /clr /c

// class template
// ref class
template <class T>
ref class A {};

// partial template specialization
// value type
template <class T>
value class A <T *> {};

// partial template specialization
// interface
template <class T>
interface class A<T%> {};

// explicit template specialization
// native class
template <>
class A <int> {};
```

## <a name="see-also"></a>Zobacz też

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)
