---
title: elementu AppDomain | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- appdomain_cpp
dev_langs:
- C++
helpviewer_keywords:
- appdomain __declspec keyword
- __declspec keyword [C++], appdomain
ms.assetid: 29d843cb-cb6b-4d1b-a48d-d928a877234d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 36df0066d3e460efceb130d257a1b6f87231dd4a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="appdomain"></a>appdomain
Określa, że w każdej domenie aplikacji zarządzanych aplikacji powinny mieć własną kopię zmiennej określonej globalne zmienna lub statyczny element członkowski. Zobacz [i domen aplikacji Visual C++](../dotnet/application-domains-and-visual-cpp.md) Aby uzyskać więcej informacji.  
  
 Wszystkich domen aplikacji ma własną kopię zmienną domeny appdomain. Konstruktor zmiennej elementu appdomain jest wykonywany, gdy zestaw jest ładowany do domeny aplikacji, a destruktor jest wykonywane, gdy domena aplikacji jest zwolniony.  
  
 Wszystkich domen aplikacji w ramach procesu w środowisku uruchomieniowym języka Aby udostępnić zmiennej globalnej, należy użyć `__declspec(process)` modyfikator. `__declspec(process)` jest włączona domyślnie w obszarze [/CLR](../build/reference/clr-common-language-runtime-compilation.md). **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015.  
  
 `__declspec(appdomain)` jest prawidłowa tylko gdy jeden z **/CLR** — opcje kompilatora jest używany. Tylko zmiennej globalnej, statycznym elementem członkowskim zmiennej lub statyczna zmienna lokalna może być oznaczony przez `__declspec(appdomain)`. Błąd, aby zastosować `__declspec(appdomain)` do statyczne elementy członkowskie typy zarządzane, ponieważ mają one zawsze to zachowanie.  
  
 Przy użyciu `__declspec(appdomain)` jest podobny do sposobu używania [wątku lokalnego magazynu (TLS)](../parallel/thread-local-storage-tls.md). Wątki mają własne magazynu, tak jak domen aplikacji. Przy użyciu `__declspec(appdomain)` zapewnia zmiennej globalnej ma własny magazyn w każdej domenie aplikacji utworzonych dla tej aplikacji.  
  
 Istnieją pewne ograniczenia mieszanie użycia dla poszczególnych procesów i zmiennych elementu appdomain; zobacz [procesu](../cpp/process.md) Aby uzyskać więcej informacji.  
  
 Na przykład podczas uruchamiania programu, są inicjowane wszystkie zmienne na proces, a następnie wszystkie domeny appdomain zmienne są inicjowane. W związku z tym po zainicjowaniu zmiennej na proces nie może zależeć na wartość zmiennej wszystkie domeny dla poszczególnych aplikacji. Zły rozwiązaniem łączyć użycie (przypisanie) dla poszczególnych appdomain i zmienne procesu jest.  
  
 Aby uzyskać informacje na temat sposobu wywołania funkcji w określonej domenie aplikacji, zobacz [call_in_appdomain — funkcja](../dotnet/call-in-appdomain-function.md).  
  
## <a name="example"></a>Przykład  
  
```  
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
 [__declspec](../cpp/declspec.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)