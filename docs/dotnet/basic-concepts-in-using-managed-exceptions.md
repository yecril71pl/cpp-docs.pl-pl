---
title: Podstawowe pojęcia związane z używaniem wyjątków zarządzanych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- try-catch exception handling, managed applications
- __finally keyword, managed exceptions
- exceptions, managed
- try-catch exception handling
- catch blocks
- throwing exceptions, managed exceptions
- Visual C++, handling managed exceptions
ms.assetid: 40ce8931-1ecc-491a-815f-733b23fcba35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 255a7d053228b73b2b0eb13f4732e9a7829549ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33114487"
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>Podstawowe pojęcia związane z używaniem wyjątków zarządzanych
W tym temacie omówiono obsługi wyjątków w zarządzanych aplikacji. Oznacza to, że aplikacja, która została skompilowana z **/CLR** — opcja kompilatora.  
  
## <a name="in-this-topic"></a>W tym temacie:  
  
-   [Wyrzucanie wyjątków w/CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor1)  
  
-   [Bloki try/Catch dla rozszerzeń CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor2)  
  
## <a name="remarks"></a>Uwagi  
 Jeśli kompilacji z **/CLR** opcji może obsłużyć wyjątki środowiska CLR, a także standard [C++, obsługa wyjątków](../cpp/cpp-exception-handling.md) i [Obsługa wyjątków strukturalnych](../cpp/structured-exception-handling-c-cpp.md) (SEH). Wyjątek CLR jest wyjątek przez typ zarządzany. [System::Exception](https://msdn.microsoft.com/en-us/library/system.exception.aspx) klasa udostępnia wiele metod przydatne do przetwarzania wyjątki środowiska CLR i jest zalecany jako klasę podstawową dla klasy wyjątków zdefiniowanych przez użytkownika.  
  
 Przechwytywanie typów wyjątków pochodzące z interfejsu nie jest obsługiwany w ramach **/CLR**. Ponadto środowisko uruchomieniowe języka wspólnego nie zezwalają na przechwytują wyjątki przepełnienie stosu; wyjątek witryny stack overflow spowoduje przerwanie procesu.  
  
 Aby uzyskać więcej informacji na temat różnic w Obsługa wyjątków w aplikacjach zarządzanych i niezarządzanych, zobacz [różnice w wyjątek obsługi zachowanie w obszarze rozszerzeń zarządzanych dla języka C++](../dotnet/differences-in-exception-handling-behavior-under-clr.md).  
  
##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a> Wyrzucanie wyjątków w/CLR  
 Wyrażenie throw C++ jest rozszerzony do throw dojścia do typu CLR. Poniższy przykład tworzy typu niestandardowego wyjątku i zgłasza wyjątek wystąpienia tego typu:  
  
```  
// clr_exception_handling.cpp  
// compile with: /clr /c  
ref struct MyStruct: public System::Exception {  
public:  
   int i;  
};  
  
void GlobalFunction() {  
   MyStruct^ pMyStruct = gcnew MyStruct;  
   throw pMyStruct;  
}  
```  
  
 Typ wartościowy musi zostać opakowany przed zgłaszane:  
  
```  
// clr_exception_handling_2.cpp  
// compile with: /clr /c  
value struct MyValueStruct {  
   int i;  
};  
  
void GlobalFunction() {  
   MyValueStruct v = {11};  
   throw (MyValueStruct ^)v;  
}  
```  
  
##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a> Bloki try/Catch dla rozszerzeń CLR  
 Taki sam **spróbuj**/**catch** struktury bloku może służyć do Przechwytywanie zarówno CLR, jak i natywny wyjątków:  
  
```  
// clr_exception_handling_3.cpp  
// compile with: /clr  
using namespace System;  
ref struct MyStruct : public Exception {  
public:  
   int i;  
};  
  
struct CMyClass {  
public:  
   double d;  
};  
  
void GlobalFunction() {  
   MyStruct^ pMyStruct = gcnew MyStruct;  
   pMyStruct->i = 11;  
   throw pMyStruct;  
}  
  
void GlobalFunction2() {  
   CMyClass c = {2.0};  
   throw c;  
}  
  
int main() {  
   for ( int i = 1; i >= 0; --i ) {  
      try {  
         if ( i == 1 )  
            GlobalFunction2();  
         if ( i == 0 )  
            GlobalFunction();  
      }  
      catch ( CMyClass& catchC ) {  
         Console::WriteLine( "In 'catch(CMyClass& catchC)'" );  
         Console::WriteLine( catchC.d );  
      }  
      catch ( MyStruct^ catchException ) {  
         Console::WriteLine( "In 'catch(MyStruct^ catchException)'" );  
         Console::WriteLine( catchException->i );  
      }  
   }  
}  
```  
  
### <a name="output"></a>Dane wyjściowe  
  
```  
In 'catch(CMyClass& catchC)'  
2  
In 'catch(MyStruct^ catchException)'  
11  
```  
  
### <a name="order-of-unwinding-for-c-objects"></a>Kolejność rozwinięcia dla obiektów C++  
 Odwijanie występuje dla obiektów C++ z destruktory, które mogą być na stosie środowiska wykonawczego między przerzucane funkcji i funkcji obsługi. Ponieważ typów CLR są przydzielone na stercie, odwijanie nie ma zastosowania do nich.  
  
 Kolejność zdarzeń dla zwrócony wyjątek jest następujący:  
  
1.  Środowisko uruchomieniowe przeprowadzi stosu wyszukiwania dla klauzuli catch odpowiednie lub w przypadku SEH, z wyjątkiem filtr dla SEH, aby przechwytywać elementu exception. Klauzule CATCH są najpierw wyszukiwane w kolejności leksykalne, a następnie dynamicznie w dół stosu wywołań.  
  
2.  Po znalezieniu poprawne obsługi stos jest oddzielić do danego punktu. Dla każdego wywołania funkcji na stosie, jego lokalne obiekty są niszczone i __finally bloki są wykonywane, od najbardziej zagnieżdżone na zewnątrz.  
  
3.  Po oddzielić stosu jest wykonywany w klauzuli catch.  
  
### <a name="catching-unmanaged-types"></a>Przechwytywanie typy Niezarządzanwe  
 Gdy typem niezarządzanym obiektu jest zgłaszany, jest on zawijany za pomocą wyjątku typu [System::Runtime.InteropServices::SEHException](https://msdn.microsoft.com/en-us/library/system.runtime.interopservices.sehexception.aspx). Podczas wyszukiwania odpowiednie **catch** klauzuli, istnieją dwie możliwości.  
  
-   W przypadku typu natywnego języka C++ wyjątek jest nie opakowanych i porównuje napotkano typ. To porównanie umożliwia natywnych typów języka C++ przechwycić w normalny sposób.  
  
-   Jednak jeśli **catch** klauzuli typu **sehexception —** lub jedną z jej klas podstawowych najpierw zbadane, klauzuli przechwytuje wyjątek. W związku z tym należy umieścić wszystkie klauzule catch, które przechwytują natywnych typów C++ najpierw przed żadnego catch klauzule typów CLR.  
  
 Należy pamiętać, że  
  
```  
catch(Object^)  
```  
  
 and  
  
```  
catch(...)  
```  
  
 będą zarówno catch dowolnego typu element zgłaszany, w tym wyjątki SEH.  
  
 Jeśli typem niezarządzanym jest objęte catch(Object^), nie spowoduje zniszczenia obiektu zgłoszenia.  
  
 Gdy trwa Zgłaszanie wyjątku lub przechwytywanie niezarządzane wyjątki, firma Microsoft zaleca użycie [/ehsc](../build/reference/eh-exception-handling-model.md) — opcja kompilatora zamiast **/EHS** lub **/eha**.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków](../windows/exception-handling-cpp-component-extensions.md)   
 [safe_cast](../windows/safe-cast-cpp-component-extensions.md)   
 [Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)