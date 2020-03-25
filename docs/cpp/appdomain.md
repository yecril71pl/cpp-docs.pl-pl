---
title: appdomain
ms.date: 11/04/2016
f1_keywords:
- appdomain_cpp
helpviewer_keywords:
- appdomain __declspec keyword
- __declspec keyword [C++], appdomain
ms.assetid: 29d843cb-cb6b-4d1b-a48d-d928a877234d
ms.openlocfilehash: 7ac74e8774204b316712a15975f7af3fb8835a9e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181489"
---
# <a name="appdomain"></a>appdomain

Określa, że każda domena aplikacji zarządzanej powinna mieć własną kopię określonej zmiennej globalnej lub statycznej zmiennej członkowskiej. Aby uzyskać więcej informacji [, C++ Zobacz domeny aplikacji i wizualizację](../dotnet/application-domains-and-visual-cpp.md) .

Każda domena aplikacji ma własną kopię zmiennej dla elementu AppDomain. Konstruktor zmiennej AppDomain jest wykonywany, gdy zestaw jest ładowany do domeny aplikacji, a destruktor jest wykonywany, gdy domena aplikacji jest zwolniona.

Jeśli chcesz, aby wszystkie domeny aplikacji w ramach procesu w środowisku uruchomieniowym języka wspólnego współużytkują zmienną globalną, użyj modyfikatora `__declspec(process)`. `__declspec(process)` jest domyślnie włączona w opcji [/CLR](../build/reference/clr-common-language-runtime-compilation.md). **/CLR: Pure** i **/CLR:** opcje kompilatora bezpiecznego są przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017.

`__declspec(appdomain)` jest prawidłowy tylko wtedy, gdy jest używana jedna z opcji kompilatora **/CLR** . Tylko zmienna globalna, statyczna zmienna członkowska lub statyczna zmienna lokalna może być oznaczona `__declspec(appdomain)`. Wystąpił błąd, aby zastosować `__declspec(appdomain)` do statycznych elementów członkowskich typów zarządzanych, ponieważ zawsze mają one takie zachowanie.

Używanie `__declspec(appdomain)` jest podobne do używania [lokalnego magazynu wątków (TLS)](../parallel/thread-local-storage-tls.md). Wątki mają własny magazyn, jako domeny aplikacji. Użycie `__declspec(appdomain)` zapewnia, że zmienna globalna ma własny magazyn w każdej domenie aplikacji utworzonej dla tej aplikacji.

Istnieją ograniczenia związane z mieszaniem użycia poszczególnych procesów i zmiennych dla domeny AppDomain; Aby uzyskać więcej informacji, zobacz [proces](../cpp/process.md) .

Na przykład w przypadku uruchamiania programu wszystkie zmienne dla poszczególnych procesów są inicjowane, a następnie zostaną zainicjowane wszystkie zmienne dla poszczególnych domen. W związku z tym, gdy zmienna dla procesu jest inicjowana, nie może zależeć od wartości żadnej zmiennej domeny dla aplikacji. Zastosowanie (przypisanie) dla poszczególnych domen i dla poszczególnych procesów nie jest właściwe.

Aby uzyskać informacje o sposobie wywoływania funkcji w określonej domenie aplikacji, zobacz [Call_in_appdomain funkcji](../dotnet/call-in-appdomain-function.md).

## <a name="example"></a>Przykład

```cpp
// declspec_appdomain.cpp
// compile with: /clr
#include <stdio.h>
using namespace System;

class CGlobal {
public:
   CGlobal(bool bProcess) {
      Counter = 10;
      m_bProcess = bProcess;
      Console::WriteLine("__declspec({0}) CGlobal::CGlobal constructor", m_bProcess ? (String^)"process" : (String^)"appdomain");
   }

   ~CGlobal() {
      Console::WriteLine("__declspec({0}) CGlobal::~CGlobal destructor", m_bProcess ? (String^)"process" : (String^)"appdomain");
   }

   int Counter;

private:
   bool m_bProcess;
};

__declspec(process) CGlobal process_global = CGlobal(true);
__declspec(appdomain) CGlobal appdomain_global = CGlobal(false);

value class Functions {
public:
   static void change() {
      ++appdomain_global.Counter;
   }

   static void display() {
      Console::WriteLine("process_global value in appdomain '{0}': {1}",
         AppDomain::CurrentDomain->FriendlyName,
         process_global.Counter);

      Console::WriteLine("appdomain_global value in appdomain '{0}': {1}",
         AppDomain::CurrentDomain->FriendlyName,
         appdomain_global.Counter);
   }
};

int main() {
   AppDomain^ defaultDomain = AppDomain::CurrentDomain;
   AppDomain^ domain = AppDomain::CreateDomain("Domain 1");
   AppDomain^ domain2 = AppDomain::CreateDomain("Domain 2");
   CrossAppDomainDelegate^ changeDelegate = gcnew CrossAppDomainDelegate(&Functions::change);
   CrossAppDomainDelegate^ displayDelegate = gcnew CrossAppDomainDelegate(&Functions::display);

   // Print the initial values of appdomain_global in all appdomains.
   Console::WriteLine("Initial value");
   defaultDomain->DoCallBack(displayDelegate);
   domain->DoCallBack(displayDelegate);
   domain2->DoCallBack(displayDelegate);

   // Changing the value of appdomain_global in the domain and domain2
   // appdomain_global value in "default" appdomain remain unchanged
   process_global.Counter = 20;
   domain->DoCallBack(changeDelegate);
   domain2->DoCallBack(changeDelegate);
   domain2->DoCallBack(changeDelegate);

   // Print values again
   Console::WriteLine("Changed value");
   defaultDomain->DoCallBack(displayDelegate);
   domain->DoCallBack(displayDelegate);
   domain2->DoCallBack(displayDelegate);

   AppDomain::Unload(domain);
   AppDomain::Unload(domain2);
}
```

```Output
__declspec(process) CGlobal::CGlobal constructor
__declspec(appdomain) CGlobal::CGlobal constructor
Initial value
process_global value in appdomain 'declspec_appdomain.exe': 10
appdomain_global value in appdomain 'declspec_appdomain.exe': 10
__declspec(appdomain) CGlobal::CGlobal constructor
process_global value in appdomain 'Domain 1': 10
appdomain_global value in appdomain 'Domain 1': 10
__declspec(appdomain) CGlobal::CGlobal constructor
process_global value in appdomain 'Domain 2': 10
appdomain_global value in appdomain 'Domain 2': 10
Changed value
process_global value in appdomain 'declspec_appdomain.exe': 20
appdomain_global value in appdomain 'declspec_appdomain.exe': 10
process_global value in appdomain 'Domain 1': 20
appdomain_global value in appdomain 'Domain 1': 11
process_global value in appdomain 'Domain 2': 20
appdomain_global value in appdomain 'Domain 2': 12
__declspec(appdomain) CGlobal::~CGlobal destructor
__declspec(appdomain) CGlobal::~CGlobal destructor
__declspec(appdomain) CGlobal::~CGlobal destructor
__declspec(process) CGlobal::~CGlobal destructor
```

## <a name="see-also"></a>Zobacz też

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
