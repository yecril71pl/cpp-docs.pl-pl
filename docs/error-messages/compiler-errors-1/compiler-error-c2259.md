---
title: Błąd kompilatora C2259 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2259
dev_langs:
- C++
helpviewer_keywords:
- C2259
ms.assetid: e458236f-bdea-4786-9aa6-a98d8bffa5f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0f64d61d30e8e805aae4ec1f9343de4dc817f66b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101595"
---
# <a name="compiler-error-c2259"></a>Błąd kompilatora C2259

"class": nie można utworzyć wystąpienia klasy abstrakcyjnej

Kod deklaruje wystąpienia abstrakcyjnej klasy lub struktury.

Nie można utworzyć wystąpienia klasy lub struktury z co najmniej jeden czystych funkcji wirtualnych. Do tworzenia wystąpień obiektów klasy pochodnej, klasy pochodne muszą przesłaniać każdego czystą funkcję wirtualną.

Aby uzyskać więcej informacji, zobacz [klasy niejawnie abstrakcyjne](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Implicitly_abstract_classes).

Poniższy przykład spowoduje wygenerowanie C2259:

```
// C2259.cpp
// compile with: /c
class V {
public:
   void virtual func() = 0;
};
class A : public V {};
class B : public V {
public:
   void func();
};
V v;  // C2259, V is an abstract class
A a;  // C2259, A inherits func() as pure virtual
B b;  // OK, B defines func()
```

Za każdym razem pochodzi z interfejsu i implementować metody interfejsu w klasie pochodnej z uprawnieniami dostępu do innych niż publicznego, może pojawić się C2259.  Dzieje się tak, ponieważ kompilator oczekuje metod interfejsu zaimplementowana w klasie pochodnej, aby mieć dostęp publiczny. Podczas implementowania funkcji elementów członkowskich w przypadku interfejsu o bardziej restrykcyjne uprawnienia dostępu kompilator nie bierze pod uwagę stawiany implementacje dla metody interfejsu zdefiniowane w interfejsie, co z kolei sprawia, że klasy pochodnej klasy abstrakcyjnej.

Istnieją dwa możliwe obejścia tego problemu:

- Upublicznić uprawnienia dostępu dla metody implementowane.

- Użyj operatora rozpoznawania zakresu dla metod interfejsu zaimplementowana w klasie pochodnej nazwy metody implementowane za pomocą nazwy interfejsu.

C2259 może również wystąpić w wyniku pracy zgodności, która została wykonana w programie Visual C++ 2005, **/Zc:** jest teraz domyślnie włączona. W takiej sytuacji można rozwiązać, albo przez kompilowanie za pomocą C2599 **/Zc:wchar_t-**, aby uzyskać zachowanie z poprzednich wersji, lub najlepiej, aktualizując typów, dzięki czemu są one zgodne. Aby uzyskać więcej informacji, zobacz [/Zc: wchar_t (wchar_t jest typem natywnym)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

Poniższy przykład spowoduje wygenerowanie C2259:

```
// C2259b.cpp
// compile with: /c
#include <windows.h>

class MyClass {
public:
   // WCHAR now typedef'ed to wchar_t
   virtual void func(WCHAR*) = 0;
};

class MyClass2 : MyClass {
public:
   void func(unsigned short*);
};

MyClass2 x;   // C2259

// OK
class MyClass3 {
public:
   virtual void func(WCHAR*) = 0;
   virtual void func2(wchar_t*) = 0;
   virtual void func3(unsigned short*) = 0;
};

class MyClass4 : MyClass3 {
public:
   void func(WCHAR*) {}
   void func2(wchar_t*) {}
   void func3(unsigned short*) {}
};

MyClass4 y;
```

Poniższy przykład spowoduje wygenerowanie C2259:

```
// C2259c.cpp
// compile with: /clr
interface class MyInterface {
   void MyMethod();
};

ref class MyDerivedClass: public MyInterface {
private:
   // Uncomment the following line to resolve.
   // public:
   void MyMethod(){}
   // or the following line
   // void MyInterface::MyMethod() {};
};

int main() {
   MyDerivedClass^ instance = gcnew MyDerivedClass; // C2259
}
```
