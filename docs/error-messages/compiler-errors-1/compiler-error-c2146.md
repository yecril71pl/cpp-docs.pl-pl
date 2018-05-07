---
title: C2146 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2146
dev_langs:
- C++
helpviewer_keywords:
- C2146
ms.assetid: 6bfb7de6-6723-4486-9350-c66ef88d7a64
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73367284a8c13316d344a4cff87ccae4ee7c832d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2146"></a>C2146 błąd kompilatora
Błąd składni: Brak tokenu, przed identyfikatorem 'Identyfikator'  
  
 Kompilator Oczekiwano `token` i znaleźć `identifier` zamiast tego.  Możliwe przyczyny:  
  
1.  Błąd pisowni lub wielkość liter.  
  
2.  Brak specyfikatora typu w deklaracji identyfikatora.  
  
 Przyczyną tego błędu może być błąd typograficzny. Błąd [C2065](../../error-messages/compiler-errors-1/compiler-error-c2065.md) poprzedza zazwyczaj ten błąd.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2146.  
  
```  
// C2146.cpp  
class CDeclaredClass {};  
  
class CMyClass {  
   CUndeclared m_myClass;   // C2146  
   CDeclaredClass m_myClass2;   // OK  
};  
  
int main() {  
   int x;  
   int t x;   // C2146 : missing semicolon before 'x'  
}  
```  
  
## <a name="example"></a>Przykład  
 Ten błąd może być również generowany w wyniku pracy zgodność kompilatora, która została wykonana dla programu Visual Studio .NET 2003: Brak `typename` — słowo kluczowe.  
  
 Poniższy przykład kompiluje w Visual Studio .NET 2002, ale nie w Visual Studio .NET 2003:  
  
```  
// C2146b.cpp  
// compile with: /c  
template <typename T>  
struct X {  
   struct Y {  
      int i;  
   };  
   Y memFunc();  
};  
  
template <typename T>  
X<T>::Y func() { }   // C2146  
  
// OK  
template <typename T>  
typename X<T>::Y func() { }  
```  
  
## <a name="example"></a>Przykład  
 Można również wyświetlić ten błąd w wyniku pracy zgodność kompilatora, która została wykonana dla programu Visual Studio .NET 2003: jawne specjalizacje nie jest już Znajdź parametry szablonu z szablonu podstawowego.  
  
 Korzystanie z `T` z podstawowego szablonu nie jest dozwolona w jawnej specjalizacji. Kod identyfikator był prawidłowy w wersjach programu Visual Studio .NET 2003 i Visual Studio .NET Visual C++ należy zastąpić wszystkie wystąpienia parametru szablonu w specjalizacji jawnie specjalistyczną odmianą.  
  
 Poniższy przykład kompiluje w programie Visual Studio .NET, ale nie w Visual Studio .NET 2003:  
  
```  
// C2146_c.cpp  
// compile with: /c  
template <class T>   
struct S;  
  
template <>   
struct S<int> {  
   T m_t;   // C2146  
   int m_t2;   // OK  
};  
```