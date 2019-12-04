---
title: Błąd kompilatora C2259
ms.date: 11/04/2016
f1_keywords:
- C2259
helpviewer_keywords:
- C2259
ms.assetid: e458236f-bdea-4786-9aa6-a98d8bffa5f4
ms.openlocfilehash: 403d674eae696eb42a837aef9d6e97c4b5b8f6c2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758791"
---
# <a name="compiler-error-c2259"></a>Błąd kompilatora C2259

"Class": nie można utworzyć wystąpienia klasy abstrakcyjnej

Kod deklaruje wystąpienie klasy abstrakcyjnej lub struktury.

Nie można utworzyć wystąpienia klasy lub struktury przy użyciu co najmniej jednej czystej funkcji wirtualnej. Aby utworzyć wystąpienie obiektów klasy pochodnej, Klasa pochodna musi zastępować każdą czystą funkcję wirtualną.

Aby uzyskać więcej informacji, zobacz [klasy abstrakcyjne niejawnie](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Implicitly_abstract_classes).

Poniższy przykład generuje C2259:

```cpp
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

Za każdym razem, gdy pochodzą z interfejsu i Implementuj metody interfejsu w klasie pochodnej z uprawnieniami dostępu innym niż Public, może się pojawić C2259.  Dzieje się tak, ponieważ kompilator oczekuje, że metody interfejsu zaimplementowane w klasie pochodnej mają dostęp publiczny. Po zaimplementowaniu funkcji Członkowskich dla interfejsu z bardziej restrykcyjnymi uprawnieniami dostępu kompilator nie uważa ich za implementacje dla metod interfejsu zdefiniowanych w interfejsie, co z kolei powoduje, że Klasa pochodna jest klasą abstrakcyjną.

Istnieją dwa możliwe obejście problemu:

- Udostępnij uprawnienia dostępu publicznie dla zaimplementowanych metod.

- Użyj operatora rozpoznawania zakresu dla metod interfejsu zaimplementowanych w klasie pochodnej, aby zakwalifikować zaimplementowaną nazwę metody z nazwą interfejsu.

C2259 może również wystąpić w wyniku zgodności z zadaniami, które zostały wykonane w programie Visual Studio 2005, **/Zc: wchar_t** jest teraz domyślnie włączone. W takiej sytuacji C2599 można rozwiązać przez skompilowanie z **/Zc: wchar_t-** , aby uzyskać zachowanie z poprzednich wersji lub raczej przez zaktualizowanie typów, aby były zgodne. Aby uzyskać więcej informacji, zobacz [/Zc: wchar_t (Wchar_t jest typem natywnym)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

Poniższy przykład generuje C2259:

```cpp
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

Poniższy przykład generuje C2259:

```cpp
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
