---
title: Środowisko wykonawcze Windows i zarządzane szablony (C + +/ CLI i C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- templates, with CLR types
ms.assetid: cf59d16b-5514-448b-9a95-e0b4fcb616a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b83aa54b9f9697fddbefc6da29e7cf99d497cc12
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328301"
---
# <a name="windows-runtime-and-managed-templates-ccli-and-ccx"></a>Środowisko wykonawcze Windows i zarządzane szablony (C + +/ CLI i C + +/ CX)

Szablony umożliwiają definiowanie prototyp Windows Runtime lub typ środowiska uruchomieniowego języka wspólnego i, tworzy zmian tego typu za pomocą parametrów typu inny szablon.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

Można tworzyć szablony od typów wartości lub odwołania.  Aby uzyskać więcej informacji na temat tworzenia typów wartości lub odwołania, zobacz [klas i struktur](../windows/classes-and-structs-cpp-component-extensions.md).

Aby uzyskać więcej informacji na temat standardowych szablonów klasy języka C++, zobacz [szablony klas](../cpp/class-templates.md).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

(Nie ma żadnych uwag dla tej funkcji języka, które dotyczą tylko środowiska uruchomieniowego Windows).

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

Istnieją pewne ograniczenia dotyczące tworzenia szablonów klas z typami zarządzanymi, które zostały przedstawione w poniższych przykładach kodu.

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

Istnieje możliwość utworzenia wystąpienia typu ogólnego z parametrem szablonu typu zarządzanego, ale nie można utworzyć wystąpienia zarządzanego szablonu z parametrem szablonu typu ogólnego. Jest to spowodowane typy ogólne są rozwiązywane w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [typy ogólne i szablony (C + +/ CLI)](../windows/generics-and-templates-visual-cpp.md).

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

Typ ogólny lub funkcji nie mogą być zagnieżdżone w szablonie zarządzanych.

```cpp
// managed_templates_2.cpp
// compile with: /clr /c

template<class T> public ref class R {
   generic<class T> ref class W {};   // C2959
};
```

Nie masz dostępu do szablonów zdefiniowane w przywoływanym zestawie za pomocą C + +/ składni języka interfejsu wiersza polecenia, ale można używać odbicia. Jeśli szablon nie zostanie uruchomiony, nie jest emitowane w metadanych. Jeśli zostanie utworzone wystąpienie szablonu, tylko funkcje składowe odwołania pojawi się w metadanych.

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

Możesz zmienić zarządzanych modyfikator klasy częściowej specjalizacji lub jawnej specjalizacji szablonu klasy.

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

[Component Extensions dla platformy .NET i platformy uniwersalnej systemu Windows](../windows/component-extensions-for-runtime-platforms.md)