---
title: "Operator odwołania (C++ Component Extensions) śledzenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '%'
dev_langs:
- C++
helpviewer_keywords:
- tracking references
- '% tracking reference [C++]'
ms.assetid: 142a7269-ab69-4b54-a6d7-833bef06228f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 71389a622b02d5c0379b2be1a91783e8235077bb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="tracking-reference-operator-c-component-extensions"></a>Operator odwołania śledzenia (C++ Component Extensions)
A *odwołanie śledzące* (`%`) zachowuje się jak zwykłe odwołanie C++ (`&`) z tą różnicą, że gdy obiekt jest przypisany do odwołaniem śledzącym, liczba odwołań obiektu jest zwiększany.  
  
## <a name="all-platforms"></a>Wszystkie platformy  
 Odwołanie śledzące ma następujące właściwości.  
  
-   Przypisania obiektu odwołaniem śledzącym powoduje, że liczba odwołanie obiektu do jest zwiększany.  
  
-   Odwołanie do natywnego (&) jest wynikiem, gdy należy usunąć odwołania do *. Odwołania śledzenia (%) jest wynikiem, gdy należy usunąć odwołania do ^. Jak długo ma % do obiektu, obiekt pozostanie w pamięci.  
  
-   Kropka (`.`) umożliwia uzyskiwanie dostępu do członka obiektu operatora dostępu do elementu członkowskiego.  
  
-   Odwołania śledzenia są prawidłowe dla typów wartości i uchwytów (na przykład `String^`).  
  
-   Odwołanie śledzenia nie można przypisać wartość null lub `nullptr` wartość. Odwołanie śledzące mogą być przypisane do inny prawidłowy obiekt dowolną liczbę razy.  
  
-   Odwołanie śledzenia nie można użyć jako operatora jednoargumentowego wykonaj adres.  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 Odwołanie śledzące zachowuje się jak standardowe odwołanie C++ z tą różnicą, że % jest liczony odwołania. Poniższy fragment kodu przedstawia sposób konwersja między % i ^ typów:  
  
```  
Foo^ spFoo = ref new Foo();  
Foo% srFoo = *spFoo;  
Foo^ spFoo2 = %srFoo;  
```  
  
 Poniższy przykład przedstawia sposób przekazywania ^ funkcji, które przyjmuje %.  
  
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
 W języku C + +/ CLI, użyciem odwołanie śledzące do uchwytu powiązać obiektu typu CLR na stercie zbierane pamięci.  
  
 W środowisku CLR, wartość odwołania do śledzenia zmiennej jest automatycznie aktualizowany w każdym przypadku, gdy moduł garbage collector przenosi odwołuje się do obiektu.  
  
 Odwołanie śledzące mogą być deklarowane tylko na stosie. Odwołanie śledzące nie może być elementem członkowskim klasy.  
  
 Nie jest możliwe na stercie zbierane odzyskiwanie natywnego języka C++ odwołanie do obiektu.  
  
 Aby uzyskać więcej informacji na temat śledzenia odwołań w języku C + +/ CLI, zobacz:  
  
-   [Instrukcje: korzystanie z odwołań śledzenia w języku C++/interfejsie wiersza polecenia](../dotnet/how-to-use-tracking-references-in-cpp-cli.md)
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 Poniższy przykład C + +/ CLI przedstawia sposób użycia odwołaniem śledzącym o typach natywnych i zarządzanych.  
  
```  
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
  
 **Przykład**  
  
 Poniższy przykład C + +/ CLI pokazano, jak można powiązać odwołanie śledzące do tablicy.  
  
```  
// tracking_reference_2.cpp  
// compile with: /clr  
using namespace System;  
  
int main() {  
   array<int> ^ a = ref new array< Int32 >(5);  
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