---
title: Obiekt AppDomain | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- appdomain_cpp
dev_langs:
- C++
helpviewer_keywords:
- appdomain __declspec keyword
- __declspec keyword [C++], appdomain
ms.assetid: 29d843cb-cb6b-4d1b-a48d-d928a877234d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f8ef06751e1c9e478c7119dbffb242581f432b9e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111774"
---
# <a name="appdomain"></a>appdomain

Określa, że każda domena aplikacji zarządzanych aplikacji powinny mieć własną kopię zmiennej określonej globalnego zmienna lub statyczna elementu członkowskiego. Zobacz [domeny aplikacji i programu Visual C++](../dotnet/application-domains-and-visual-cpp.md) Aby uzyskać więcej informacji.

W każdej domenie aplikacji jest własną kopię zmiennej dla domeny appdomain. Konstruktor obiektu appdomain zmiennej jest wykonywany, gdy zestaw jest ładowany do domeny aplikacji i destruktor jest wykonywany, gdy domena aplikacji jest zwalniana.

Jeśli chcesz, aby wszystkie domeny aplikacji w ramach procesu w środowisko uruchomieniowe języka wspólnego udostępnianie zmienną globalną, użyj `__declspec(process)` modyfikator. `__declspec(process)` obowiązuje domyślny w obszarze [/CLR](../build/reference/clr-common-language-runtime-compilation.md). **/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

`__declspec(appdomain)` jest prawidłowa tylko gdy jeden z **/CLR** opcje kompilatora jest używany. Tylko zmienną globalną, statyczny element członkowski, zmienna lub statyczna zmienna lokalna może być oznaczony za pomocą `__declspec(appdomain)`. Jest to błąd, aby zastosować `__declspec(appdomain)` do statycznych elementów członkowskich typy zarządzane, ponieważ mają one zawsze to zachowanie.

Za pomocą `__declspec(appdomain)` jest podobne do [wątku lokalnego magazynu (TLS)](../parallel/thread-local-storage-tls.md). Wątki mają własne magazynu, tak jak domeny aplikacji. Za pomocą `__declspec(appdomain)` zapewnia zmienna globalna ma własny magazyn, w każdej domenie aplikacji utworzonych dla tej aplikacji.

Istnieją ograniczenia dotyczące mieszania użytkowania według procesu i zmiennych domeny aplikacji; zobacz [procesu](../cpp/process.md) Aby uzyskać więcej informacji.

Na przykład podczas uruchamiania programu, są inicjowane wszystkie zmienne na proces, a następnie wszystkie zmienne dla domeny appdomain są inicjowane. W związku z tym podczas inicjowania zmiennej na proces nie może zależeć na wartość dowolnej zmiennej domeny na aplikację. Jest złym zwyczajem mieszać użytkowania (przypisanie) według domeny aplikacji i zmiennych procesów.

Aby uzyskać informacje na temat sposobu wywoływania funkcji w określonej domenie aplikacji, zobacz [call_in_appdomain, funkcja](../dotnet/call-in-appdomain-function.md).

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

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)