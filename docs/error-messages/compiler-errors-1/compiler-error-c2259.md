---
title: C2259 błąd kompilatora | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 1e5c415a7669a6e26ecba6ee8ce40f8a42d94a16
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2259"></a>C2259 błąd kompilatora
"class": nie można utworzyć wystąpienia klasy abstrakcyjnej  
  
 Kod deklaruje wystąpienia abstrakcyjnej klasy lub struktury.  
  
 Nie można utworzyć wystąpienia klasy lub struktury z co najmniej jeden czystych funkcji wirtualnych. Do tworzenia wystąpień obiektów klasy pochodnej, klasy pochodne muszą przesłaniać każdego czystej funkcji wirtualnej.  
  
 Aby uzyskać więcej informacji, zobacz [klasy niejawnie abstrakcyjne](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Implicitly_abstract_classes).  
  
 Poniższy przykład generuje C2259:  
  
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
  
 Za każdym razem pochodzi z interfejsu i implementuje metody interfejsu w klasie pochodnej z uprawnieniami dostępu do innych niż publicznego, może zostać wyświetlony C2259.  Dzieje się tak dlatego kompilator oczekuje metody interfejsu zaimplementowana w klasie pochodnej dostępu publicznego. Podczas implementowania funkcji elementów członkowskich interfejsu z bardziej restrykcyjne uprawnienia dostępu, kompilator nie należy wziąć pod uwagę do implementacji dla metody interfejsu zdefiniowane w interfejsie, co z kolei pozwala klasy pochodnej klasy abstrakcyjnej.  
  
 Istnieją dwa możliwe obejścia tego problemu:  
  
-   Udostępnić uprawnienia dostępu dla metod zaimplementowanych.  
  
-   Użyj operator rozpoznawania zakresów dla metody interfejsu zaimplementowana w klasie pochodnej nazwy implementowana metoda nazwą interfejsu.  
  
 C2259 może także wystąpić w wyniku pracy zgodności, które zostało wykonane w programie Visual C++ 2005, **/Zc:** jest teraz włączona domyślnie. W takiej sytuacji można rozwiązać, albo przez kompilowania przy użyciu C2599 **/Zc:wchar_t-**, aby uzyskać zachowanie z poprzednich wersji lub najlepiej, aktualizując z typów tak, aby były zgodne. Aby uzyskać więcej informacji, zobacz [/Zc: wchar_t (wchar_t jest typem natywnym)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md).  
  
 Poniższy przykład generuje C2259:  
  
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
  
 Poniższy przykład generuje C2259:  
  
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
