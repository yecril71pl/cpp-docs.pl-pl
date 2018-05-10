---
title: Środowisko wykonawcze systemu Windows i zarządzane szablony (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: e9053b101428ac26e96446d9c6756ec5de35e06c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="windows-runtime-and-managed-templates-c-component-extensions"></a>Środowisko wykonawcze systemu Windows i zarządzane szablony (C++ Component Extensions)
Szablony umożliwiają zdefiniowanie prototyp środowiska wykonawczego systemu Windows lub typ środowiska uruchomieniowego języka wspólnego, a następnie wystąpienia zmian tego typu za pomocą parametrów typu szablonu.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 Można utworzyć szablony z typów wartości lub odwołania.  Aby uzyskać więcej informacji na temat tworzenia typów wartości lub odwołania, zobacz [klas i struktur](../windows/classes-and-structs-cpp-component-extensions.md).  
  
 Aby uzyskać więcej informacji dotyczących standardowych szablonów klas C++, zobacz [szablonów klas](../cpp/class-templates.md).  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 (Brak żadnych uwag dla tej funkcji języka, które są stosowane do środowiska uruchomieniowego systemu Windows.)  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania  
 Tworzenie szablonów klas z zarządzanego typów, które przedstawiono w poniższych przykładach kodu istnieją pewne ograniczenia.  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 Można utworzyć wystąpienia typu ogólnego z parametrem szablonu typu zarządzanego, ale nie można utworzyć wystąpienia zarządzanego szablonu z parametrem szablonu typu ogólnego.  Jest to spowodowane typy ogólne są rozpoznawane w czasie wykonywania.  Aby uzyskać więcej informacji, zobacz [typy ogólne i szablony (Visual C++)](../windows/generics-and-templates-visual-cpp.md).  
  
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
  
 **Przykład**  
  
 Typu ogólnego lub funkcji nie mogą być zagnieżdżone w szablonie zarządzanych.  
  
```cpp  
// managed_templates_2.cpp  
// compile with: /clr /c  
  
template<class T> public ref class R {  
   generic<class T> ref class W {};   // C2959  
};  
```  
  
 **Przykład**  
  
 Nie masz dostępu do szablonów zdefiniowane w przywoływanym zestawie z C + +/ składni języka interfejsu wiersza polecenia, ale można użyć odbicia.  Jeśli szablon nie zostanie uruchomiony, nie są emitowane w metadanych.  Jeśli szablon zostanie uruchomiony, tylko funkcje, do którego istnieje odwołanie elementu członkowskiego będą wyświetlane w metadanych.  
  
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
  
 **Przykład**  
  
 Możesz zmienić zarządzanych modyfikator klasy częściowej specjalizacji lub jawna specjalizacja szablonu klasy.  
  
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
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)