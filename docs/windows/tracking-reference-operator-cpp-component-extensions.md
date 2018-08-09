---
title: Operator odwołania (C++ Component Extensions) śledzenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- '%'
dev_langs:
- C++
helpviewer_keywords:
- tracking references
- '% tracking reference [C++]'
ms.assetid: 142a7269-ab69-4b54-a6d7-833bef06228f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e645d39a6373362a33e4efd25019d43cad348bbc
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651834"
---
# <a name="tracking-reference-operator-c-component-extensions"></a>Operator odwołania śledzenia (C++ Component Extensions)
A *odwołanie śledzenia* (`%`) zachowuje się jak zwykłe odniesienie C++ (`&`) z tą różnicą, że gdy obiekt jest przypisany do odwołania śledzenia, zwiększany jest licznik odwołań obiektu.  
  
## <a name="all-platforms"></a>Wszystkie platformy  
 Odwołanie śledzenia ma następujące cechy.  
  
-   Przypisanie obiektu do odwołania śledzenia powoduje, że licznik odwołań obiektu rośnie.  
  
-   Odwołanie natywne (`&`) jest wynikiem, gdy użytkownik cofnie odwołanie `*`. Odwołanie śledzenia (`%`) jest wynikiem, gdy użytkownik cofnie odwołanie `^`. Tak długo, jak masz `%` do obiektu, obiekt pozostanie w pamięci.  
  
-   Kropka (`.`) operator dostępu do elementu członkowskiego jest używany do uzyskania dostępu do członka obiektu.  
  
-   Śledzenie odwołań jest prawidłowe dla typów wartości i uchwytów (na przykład `String^`).  
  
-   Odwołanie śledzenia nie można przypisać wartości null lub **nullptr** wartości. Odwołanie śledzenia może zostać ponownie przypisane do innego prawidłowego obiektu dowolną liczbę razy.  
  
-   Odwołanie śledzenia nie można użyć jako operatora jednoargumentowego pobierania adresu.  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 Odwołanie śledzenia zachowuje się jak odniesienia standardowego języka C++, z tą różnicą, że % jest zliczonych odwołań. Poniższy fragment kodu pokazuje, jak przeprowadzać konwersję między % i ^ typów:  
  
```  
Foo^ spFoo = ref new Foo();  
Foo% srFoo = *spFoo;  
Foo^ spFoo2 = %srFoo;  
```  
  
 Poniższy przykład pokazuje, jak przekazać ^ do funkcji, która przyjmuje %.  
  
```  
ref class Foo sealed {};  
  
    // internal or private  
    void UseFooHelper(Foo% f)  
    {  
        auto x = %f;  
    }  
  
    // public method on ABI boundary  
    void UseFoo(Foo^ f)  
    {  
        if (f != nullptr) { UseFooHelper(*f); }  
    }  
```  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
 W języku C + +/ CLI, można użyć odwołania śledzenia do uchwytu wiążąc się obiekt typu CLR na stosie zebranych elementów bezużytecznych.  
  
 W cl, wartość odniesienia śledzenia zmienna jest aktualizowana automatycznie, gdy moduł odśmiecania pamięci przenosi przywoływanego obiektu.  
  
 Odwołanie śledzenia może być deklarowana tylko na stosie. Odwołanie śledzenia nie może być składową klasy.  
  
 Nie jest możliwe macierzyste odwołanie C++ do obiektu na stercie zebranych elementów bezużytecznych.  
  
 Aby uzyskać więcej informacji dotyczących śledzenia odwołań w języku C + +/ CLI, zobacz:  
  
-   [Instrukcje: korzystanie z odwołań śledzenia w języku C++/interfejsie wiersza polecenia](../dotnet/how-to-use-tracking-references-in-cpp-cli.md)
  
### <a name="examples"></a>Przykłady  
  
 Poniższy przykład dla C + +/ CLI pokazuje, jak używać śledzenia odwołania z typami macierzystym i zarządzanym.  
  
```cpp  
// tracking_reference_1.cpp  
// compile with: /clr  
ref class MyClass {  
public:  
   int i;  
};  
  
value struct MyStruct {  
   int k;  
};  
  
int main() {  
   MyClass ^ x = ref new MyClass;  
   MyClass ^% y = x;   // tracking reference handle to reference object   
  
   int %ti = x->i;   // tracking reference to member of reference type  
  
   int j = 0;  
   int %tj = j;   // tracking reference to object on the stack  
  
   int * pi = new int[2];  
   int % ti2 = pi[0];   // tracking reference to object on native heap  
  
   int *% tpi = pi;   // tracking reference to native pointer  
  
   MyStruct ^ x2 = ref new MyStruct;  
   MyStruct ^% y2 = x2;   // tracking reference to value object  
  
   MyStruct z;  
   int %tk = z.k;   // tracking reference to member of value type  
  
   delete[] pi;  
}  
```  
  
 Poniższy przykład dla C + +/ CLI pokazuje, jak powiązać śledzenie odwołania do tablicy.  
  
```cpp  
// tracking_reference_2.cpp  
// compile with: /clr  
using namespace System;  
  
int main() {  
   array<int> ^ a = ref new array<Int32>(5);  
   a[0] = 21;  
   Console::WriteLine(a[0]);  
   array<int> ^% arr = a;  
   arr[0] = 222;  
   Console::WriteLine(a[0]);  
}  
```  
  
 **Output**  
  
```Output  
21  
222  
```