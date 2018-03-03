---
title: "Operatory zdefiniowane przez użytkownika (C + +/ CLI) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- user-defined operators under /clr
ms.assetid: 42f93b4a-6de4-4e34-b07b-5a62ac014f2c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b02d6806abedb407d1c53ec8022e92983ce21d28
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="user-defined-operators-ccli"></a>Operatory zdefiniowane przez użytkownika (C++/CLI)
Operatory zdefiniowane przez użytkownika w typach zarządzanych są dozwolone jako statyczne elementy Członkowskie lub elementy członkowskie wystąpień lub w zakresie globalnym. Jednak tylko statyczne operatory są dostępne za pośrednictwem metadanych do klientów, którzy są napisane w języku innym niż Visual C++.  
  
 W typu odwołania jeden z parametrów statycznych operatora zdefiniowanej przez użytkownika musi być jedną z nich:  
  
-   Uchwyt (`type` ^) do wystąpienia typu otaczającego.  
  
-   Pośredni typu odwołanie (`type`^ & lub typ ^ %) do dojścia do wystąpienia typu otaczającego.  
  
 W typie wartości jednego z parametrów statycznych operatora zdefiniowanej przez użytkownika musi być jeden z nich:  
  
-   Z tego samego typu co typ otaczający wartość.  
  
-   Pośredni typu wskaźnika (`type`^) do typu otaczającego.  
  
-   Pośredni typu odwołanie (`type`% lub `type`&) do typu otaczającego.  
  
-   Pośredni typu odwołanie (`type`^ % lub `type`^ &) do uchwytu.  
  
 Można zdefiniować następujące operatory:  
  
|Operator|Formularze jedno/dwuargumentowy?|  
|--------------|--------------------------|  
|!|Jednoargumentowe|  
|!=|plików binarnych|  
|%|plików binarnych|  
|&|Jednoargumentowy i danych binarnych|  
|&&|plików binarnych|  
|*|Jednoargumentowy i danych binarnych|  
|+|Jednoargumentowy i danych binarnych|  
|++|Jednoargumentowe|  
|,|plików binarnych|  
|-|Jednoargumentowy i danych binarnych|  
|--|Jednoargumentowe|  
|->|Jednoargumentowe|  
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
|false|Jednoargumentowe|  
|true|Jednoargumentowe|  
|&#124;|plików binarnych|  
|&#124;&#124;|plików binarnych|  
|~|Jednoargumentowe|  
  
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
 W poniższym przykładzie pokazano syntezy operatora, który jest dostępny tylko gdy używasz **/CLR** do skompilowania. Syntezy operatora tworzy formularz przypisania operatora binarnego, jeśli nie jest zdefiniowany, gdzie po lewej stronie operatora przypisania ma typ CLR.  
  
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