---
title: C2143 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2143
dev_langs:
- C++
helpviewer_keywords:
- C2143
ms.assetid: 1d8d1456-e031-4965-9240-09a6e33ba81c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 076f2ccb594edd5d9e627d8a4dcea2d9bb928890
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171643"
---
# <a name="compiler-error-c2143"></a>C2143 błąd kompilatora
Błąd składniowy: brakuje "token1" przed "token2"  
  
 Kompilator oczekiwany określony token (to znaczy elemencie języka innego niż biały znak) i zamiast tego znaleziono inny token.  
  
 Aby uzyskać informacje o tym błędzie Jeśli występuje on, korzystając z bloku try funkcji, zobacz [artykułu bazy wiedzy 241706](http://support.microsoft.com/kb/241706).  
  
 Sprawdź [dokumentacja języka C++](../../cpp/cpp-language-reference.md) ustalenie, gdy kod jest nieprawidłowy. Ponieważ kompilator może zgłosić ten błąd, po napotkaniu wiersza, który powoduje problem, sprawdź poprzedzających błąd kilka wierszy kodu.  
  
 C2143 mogą występować w różnych sytuacjach.  
  
 Może wystąpić, gdy operator, który można nazwy (`::`, `->`, i `.`) musi następować słowo kluczowe `template`w tym przykładzie:  
  
```cpp  
class MyClass  
{  
    template<class Ty, typename PropTy>  
    struct PutFuncType : public Ty::PutFuncType<Ty, PropTy> // error C2143  
    {  
    };  
};  
  
```  
  
 Domyślnie C++ zakłada się, że `Ty::PutFuncType` nie jest szablonem; w związku z tym następujące `<` jest interpretowana jako mniej-znaku.  Należy nakazuje kompilatorowi jawnie który `PutFuncType` jest to szablon, tak aby poprawnie może przeanalizować składni nawiasu ostrego. Aby rozwiązać ten problem, należy użyć `template` — słowo kluczowe w typie zależnym nazwy, jak pokazano poniżej:  
  
```cpp  
class MyClass  
{  
    template<class Ty, typename PropTy>  
    struct PutFuncType : public Ty::template PutFuncType<Ty, PropTy> // correct  
    {  
    };  
};  
  
```  
  
 C2143 może wystąpić, gdy **/CLR** jest używany i `using` dyrektywa zawiera błąd składniowy:  
  
```cpp  
// C2143a.cpp  
// compile with: /clr /c  
using namespace System.Reflection;   // C2143  
using namespace System::Reflection;  
```  
  
 Może również wystąpić, gdy chcesz skompilować pliku kodu źródłowego przy użyciu składni CLR bez także za pomocą **/CLR**:  
  
```cpp  
// C2143b.cpp  
ref struct A {   // C2143 error compile with /clr  
   void Test() {}  
};  
  
int main() {  
   A a;  
   a.Test();  
}  
```  
  
 Pierwszy znak odstępem, który następuje `if` instrukcja musi być nawias. Kompilator nie może dokonywać translacji dodatkowych czynności:  
  
```cpp  
// C2143c.cpp  
int main() {  
   int j = 0;  
  
   // OK  
   if (j < 25)  
      ;  
  
   if (j < 25)   // C2143  
}  
```  
  
 C2143 może wystąpić, gdy zamykający nawias klamrowy, nawiasy lub średnika brakuje wiersza, w których wykryto błąd lub jednego z wierszy po prostu powyżej:  
  
```cpp  
// C2143d.cpp  
// compile with: /c  
class X {  
   int member1;  
   int member2   // C2143  
} x;  
```  
  
 Lub jeśli w deklaracji klasy znajduje się nieprawidłowy tag:  
  
```cpp  
// C2143e.cpp  
class X {  
   int member;  
} x;  
  
class + {};   // C2143 + is an invalid tag name  
class ValidName {};   // OK  
```  
  
 Lub jeśli etykieta nie jest dołączony do instrukcji. Jeśli samodzielnie, należy umieścić etykietę, na przykład na końcu złożonej instrukcji, dołącz je do Instrukcja o wartości null:  
  
```cpp  
// C2143f.cpp  
// compile with: /c  
void func1() {  
   // OK  
   end1:  
      ;  
  
   end2:   // C2143  
}  
```  
  
 Ten błąd może wystąpić, gdy niekwalifikowane wywołanie do typu w standardowej bibliotece C++:  
  
```cpp  
// C2143g.cpp  
// compile with: /EHsc /c  
#include <vector>  
static vector<char> bad;   // C2143  
static std::vector<char> good;   // OK  
```  
  
 Lub brakuje `typename` — słowo kluczowe:  
  
```cpp  
// C2143h.cpp  
template <typename T>  
struct X {  
   struct Y {  
      int i;  
   };  
   Y memFunc();  
};  
template <typename T>  
X<T>::Y X<T>::memFunc() {   // C2143  
// try the following line instead  
// typename X<T>::Y X<T>::memFunc() {  
   return Y();  
}  
```  
  
 Lub jeśli podjęciem próby zdefiniowania jawne utworzenie wystąpienia:  
  
```cpp  
// C2143i.cpp  
// compile with: /EHsc /c  
// template definition  
template <class T>  
void PrintType(T i, T j) {}  
  
template void PrintType(float i, float j){}   // C2143  
template void PrintType(float i, float j);   // OK  
```  
  
 W programie C należy zadeklarować na początku funkcji i nie można zadeklarować po funkcja wykonuje instrukcje deklaracji z systemem innym niż.  
  
```C  
// C2143j.c  
int main()   
{  
    int i = 0;  
    i++;  
    int j = 0; // C2143  
}  
```  
