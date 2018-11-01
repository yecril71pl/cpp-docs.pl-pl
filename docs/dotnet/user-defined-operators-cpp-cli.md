---
title: Operatory zdefiniowane przez użytkownika (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- user-defined operators under /clr
ms.assetid: 42f93b4a-6de4-4e34-b07b-5a62ac014f2c
ms.openlocfilehash: 17f2f05ba6a8854a69fd2dd449a94d6b86a66d7b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480018"
---
# <a name="user-defined-operators-ccli"></a>Operatory zdefiniowane przez użytkownika (C++/CLI)

Operatory zdefiniowane przez użytkownika w typach zarządzanych są dozwolone jako elementy statyczne lub składowych wystąpienia lub w zakresie globalnym. Jednak tylko statyczne operatory są dostępne za pośrednictwem metadanych dla klientów, którzy są napisane w języku innym niż Visual C++.

W typ odwołania jeden z parametrów statyczne operatora zdefiniowanego przez użytkownika musi mieć jedną z tych:

- Dojście (`type` ^) do wystąpienia typu otaczającego.

- Operatory pośrednie odwołanie do typu (`type`^ & lub typ ^ %) do dojścia do wystąpienia typu otaczającego.

Utworzenie typu wartości jednego z parametrów statyczne operatora zdefiniowanego przez użytkownika muszą być jeden z nich:

- Tego samego typu co typ otaczający wartość.

- Bezpośredni typ wskaźnika (`type`^) na typ otaczający.

- Operatory pośrednie odwołanie do typu (`type`% lub `type`&) na typ otaczający.

- Operatory pośrednie odwołanie do typu (`type`^ % lub `type`^ &) do uchwytu.

Można zdefiniować następujące operatory:

|Operator|Formularze jedno/dwuargumentowy?|
|--------------|--------------------------|
|!|Jednoargumentowy|
|!=|plików binarnych|
|%|plików binarnych|
|&|Jednoargumentowy i danych binarnych|
|&&|plików binarnych|
|*|Jednoargumentowy i danych binarnych|
|+|Jednoargumentowy i danych binarnych|
|++|Jednoargumentowy|
|,|plików binarnych|
|-|Jednoargumentowy i danych binarnych|
|--|Jednoargumentowy|
|->|Jednoargumentowy|
|/|plików binarnych|
|<|plików binarnych|
|<<|plików binarnych|
|\<=|plików binarnych|
|=|plików binarnych|
|==|plików binarnych|
|>|plików binarnych|
|>=|plików binarnych|
|>>|plików binarnych|
|^|plików binarnych|
|false|Jednoargumentowy|
|true|Jednoargumentowy|
|&#124;|plików binarnych|
|&#124;&#124;|plików binarnych|
|~|Jednoargumentowy|

## <a name="example"></a>Przykład

```cpp
// mcppv2_user-defined_operators.cpp
// compile with: /clr
using namespace System;
public ref struct X {
   X(int i) : m_i(i) {}
   X() {}

   int m_i;

   // static, binary, user-defined operator
   static X ^ operator + (X^ me, int i) {
      return (gcnew X(me -> m_i + i));
   }

   // instance, binary, user-defined operator
   X^ operator -( int i ) {
      return gcnew X(this->m_i - i);
   }

   // instance, unary, user-defined pre-increment operator
   X^ operator ++() {
      return gcnew X(this->m_i++);
   }

   // instance, unary, user-defined post-increment operator
   X^ operator ++(int i) {
      return gcnew X(this->m_i++);
   }

   // static, unary user-defined pre- and post-increment operator
   static X^ operator-- (X^ me) {
      return (gcnew X(me -> m_i - 1));
   }
};

int main() {
   X ^hX = gcnew X(-5);
   System::Console::WriteLine(hX -> m_i);

   hX = hX + 1;
   System::Console::WriteLine(hX -> m_i);

   hX = hX - (-1);
   System::Console::WriteLine(hX -> m_i);

   ++hX;
   System::Console::WriteLine(hX -> m_i);

   hX++;
   System::Console::WriteLine(hX -> m_i);

   hX--;
   System::Console::WriteLine(hX -> m_i);

   --hX;
   System::Console::WriteLine(hX -> m_i);
}
```

```Output
-5
-4
-3
-2
-1
-2
-3
```

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano syntezy operatora, który jest dostępny tylko jeśli używasz **/CLR** do skompilowania. Syntezy operatora tworzy formularz przypisania operatora binarnego, jeśli nie jest zdefiniowany, gdzie po lewej stronie operatora przypisania ma typ CLR.

```cpp
// mcppv2_user-defined_operators_2.cpp
// compile with: /clr
ref struct A {
   A(int n) : m_n(n) {};
   static A^ operator + (A^ r1, A^ r2) {
      return gcnew A( r1->m_n + r2->m_n);
   };
   int m_n;
};

int main() {
   A^ a1 = gcnew A(10);
   A^ a2 = gcnew A(20);

   a1 += a2;   // a1 = a1 + a2   += not defined in source
   System::Console::WriteLine(a1->m_n);
}
```

```Output
30
```

## <a name="see-also"></a>Zobacz też

[Klasy i struktury](../windows/classes-and-structs-cpp-component-extensions.md)