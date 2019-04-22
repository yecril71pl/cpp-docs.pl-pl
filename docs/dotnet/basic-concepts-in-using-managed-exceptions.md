---
title: Podstawowe pojęcia związane z używaniem wyjątków zarządzanych
ms.date: 11/04/2016
helpviewer_keywords:
- try-catch exception handling, managed applications
- __finally keyword, managed exceptions
- exceptions, managed
- try-catch exception handling
- catch blocks
- throwing exceptions, managed exceptions
- Visual C++, handling managed exceptions
ms.assetid: 40ce8931-1ecc-491a-815f-733b23fcba35
ms.openlocfilehash: e2aed98d9131b3d7b96cdc3e3297823d69d0ad38
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58781539"
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>Podstawowe pojęcia związane z używaniem wyjątków zarządzanych

W tym temacie omówiono obsługi wyjątków w aplikacjach zarządzanych. Oznacza to, że aplikacja, która została skompilowana z **/CLR** — opcja kompilatora.

## <a name="in-this-topic"></a>W tym temacie:

- [Zgłaszanie wyjątków w ramach/CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor1)

- [Bloki try/Catch dla rozszerzeń środowiska CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor2)

## <a name="remarks"></a>Uwagi

Jeśli kompilujesz z opcją **/CLR** opcji może obsługiwać wyjątki środowiska CLR, a także standard <xref:System.Exception> klasy zawiera wiele użytecznych metod do przetwarzania wyjątki środowiska CLR i jest zalecana jako klasa bazowa dla wyjątków zdefiniowanych przez użytkownika klasy.

Przechwytywanie typów wyjątków pochodzących z interfejsu nie jest obsługiwany w ramach **/CLR**. Ponadto środowisko uruchomieniowe języka wspólnego pozwala na przechwytywać wyjątków przepełnienia stosu; Wyjątek przepełnienia stosu zakończy proces.

Aby uzyskać więcej informacji na temat różnic w obsłudze wyjątków w aplikacjach zarządzanych i niezarządzanych, zobacz [różnice w wyjątek Obsługa zachowania w ramach zarządzanych rozszerzeń dla C++](../dotnet/differences-in-exception-handling-behavior-under-clr.md).

##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a> Zgłaszanie wyjątków w ramach/CLR

Wyrażenie throw C++ jest rozszerzony do zgłoszenia dojścia do typu CLR. Poniższy przykład tworzy typ niestandardowy wyjątek i następnie zgłasza wystąpienia tego typu:

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

##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a> Bloki try/Catch dla rozszerzeń środowiska CLR

Taki sam **spróbuj**/**catch** strukturze bloku mogą służyć do Przechwytywanie CLR i natywnych wyjątków:

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

### <a name="order-of-unwinding-for-c-objects"></a>Kolejność Odwijanie obiektów języka C++

Odwijanie występuje dla obiektów języka C++ z destruktorami, które mogą znajdować się na stosie środowiska wykonawczego pomiędzy zgłaszanie funkcji i funkcji obsługi. Ponieważ typy CLR są przydzielane na stosie, odwijanie nie ma zastosowania do nich.

Kolejność zdarzeń zgłoszonego wyjątku jest następująca:

1. Środowisko uruchomieniowe przedstawia stos wyszukiwania dla klauzuli catch odpowiednie lub w przypadku SEH, z wyjątkiem filtr dla SEH, aby przechwycić wyjątek. Klauzule catch przeszukiwany w pierwszej kolejności w kolejności leksykalne i dynamicznie i w dół stosu wywołań.

1. Po znalezieniu poprawne obsługi stos jest odwijany do tego punktu. Dla każdego wywołania funkcji na stosie, jego lokalne obiekty są niszczone __finally bloki są one wykonywane, od najbardziej zagnieżdżone na zewnątrz.

1. Gdy stos jest odwijany, jest wykonywany klauzuli "catch".

### <a name="catching-unmanaged-types"></a>Przechwytywanie typy Niezarządzanwe

Gdy typ obiektu niezarządzanego jest zgłaszany, jest ujęte w nawiasy wyjątek typu <xref:System.Runtime.InteropServices.SEHException>. Podczas wyszukiwania odpowiednie **catch** klauzuli, istnieją dwie możliwości.

- Jeśli okaże się typem natywnym języku C++, wyjątek jest nieopakowanych i w porównaniu do typu napotkano. To porównanie umożliwia typu natywnego języka C++ można przechwycić w normalny sposób.

- Jednak jeśli **catch** klauzuli typu **sehexception —** lub dowolny z jej klas bazowych jest badany najpierw, klauzuli przechwytuje wyjątek. W związku z tym należy umieścić wszystkie klauzule catch, które przechwytują najpierw typów natywnych języka C++, zanim dowolny catch klauzule typy CLR.

Należy pamiętać, że

```
catch(Object^)
```

and

```
catch(...)
```

będzie przechwytywać zarówno dowolnego zgłoszonego typu, w tym wyjątki SEH.

Jeśli niezarządzany typ zostanie przechwycony przez catch(Object^), nie spowoduje zniszczenie co wyrzucony obiekt.

Podczas zgłaszania lub przechwytywanie niezarządzane wyjątki, firma Microsoft zaleca użycie [/ehsc](../build/reference/eh-exception-handling-model.md) — opcja kompilatora zamiast **/EHS** lub **/eha**.

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)
