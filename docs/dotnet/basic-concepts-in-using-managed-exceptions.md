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
ms.openlocfilehash: 6bc1e9c6d40599ae9a821179dcf56dbb7e21bf10
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372525"
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>Podstawowe pojęcia związane z używaniem wyjątków zarządzanych

W tym temacie omówiono obsługę wyjątków w aplikacjach zarządzanych. Oznacza to, że aplikacja, która jest skompilowana za pomocą opcji kompilatora **/clr.**

## <a name="in-this-topic"></a>W tym temacie:

- [Zgłaszanie wyjątków w obszarze /clr](#vcconbasicconceptsinusingmanagedexceptionsanchor1)

- [Try/Catch Bloki dla rozszerzeń CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor2)

## <a name="remarks"></a>Uwagi

Jeśli kompilujesz z **/clr** opcji, można obsługiwać wyjątki <xref:System.Exception> CLR, a także klasy standardowej zawiera wiele przydatnych metod przetwarzania wyjątków CLR i jest zalecane jako klasa podstawowa dla klas wyjątków zdefiniowanych przez użytkownika.

Przechwytywanie typów wyjątków pochodzących z interfejsu nie jest obsługiwane w **obszarze /clr**. Ponadto środowisko uruchomieniowe języka wspólnego nie pozwala na catch wyjątki przepełnienia stosu; wyjątek przepełnienia stosu zakończy proces.

Aby uzyskać więcej informacji na temat różnic w obsłudze wyjątków w aplikacjach zarządzanych i niezarządzanych, zobacz [Różnice w zachowaniu obsługi wyjątków w obszarze Rozszerzenia zarządzane dla języka C++](../dotnet/differences-in-exception-handling-behavior-under-clr.md).

## <a name="throwing-exceptions-under-clr"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a>Zgłaszanie wyjątków w obszarze /clr

Wyrażenie throw języka C++ jest rozszerzone, aby rzucić dojście do typu CLR. Poniższy przykład tworzy niestandardowy typ wyjątku, a następnie zgłasza wystąpienie tego typu:

```cpp
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

Typ wartości musi być zapakowany przed wyrzuceniem:

```cpp
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

## <a name="trycatch-blocks-for-clr-extensions"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a>Try/Catch Bloki dla rozszerzeń CLR

Ta sama struktura bloku **try**/**catch** może służyć do przechwytywania zarówno CLR i wyjątków natywnych:

```cpp
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

### <a name="order-of-unwinding-for-c-objects"></a>Kolejność odwijania dla obiektów języka C++

Odwijanie występuje dla wszystkich obiektów C++ z destruktorami, które mogą znajdować się na stosie w czasie wykonywania między funkcją rzucania a funkcją obsługi. Ponieważ typy CLR są przydzielane na stercie, odwijanie nie ma zastosowania do nich.

Kolejność zdarzeń dla wyjątku zaniechanego jest następująca:

1. Środowisko uruchomieniowe przechodzi stosu szuka klauzuli catch odpowiednie lub w przypadku SEH, z wyjątkiem filtru dla SEH, aby przechwyć wyjątek. Catch klauzule są przeszukiwane najpierw w kolejności leksykalne, a następnie dynamicznie w dół stosu wywołań.

1. Po znalezieniu poprawnego programu obsługi stos jest odwijanie do tego punktu. Dla każdego wywołania funkcji na stosie jego obiekty lokalne są zniszczone i __finally bloki są wykonywane, z większości zagnieżdżonych na zewnątrz.

1. Po rozwiń stosu, catch klauzuli jest wykonywany.

### <a name="catching-unmanaged-types"></a>Łapanie typów niezarządzanych

Gdy zgłaszany jest niezarządzany typ obiektu, jest <xref:System.Runtime.InteropServices.SEHException>on zawijany z wyjątkiem typu . Podczas wyszukiwania odpowiedniej klauzuli **catch,** istnieją dwie możliwości.

- Jeśli napotkany jest natywny typ C++, wyjątek jest rozpakowany i porównywany do napotkanego typu. To porównanie umożliwia natywnego typu C++ zostać przechwycone w normalny sposób.

- Jednak jeśli **catch** klauzuli typu **SEHException** lub któregokolwiek z jego klas podstawowych jest analizowany pierwszy, klauzula przechwytuje wyjątek. W związku z tym należy umieścić wszystkie catch klauzule, które przechwytują natywne typy C++ pierwszy przed wszelkie catch klauzule typów CLR.

Należy pamiętać, że

```
catch(Object^)
```

i

```
catch(...)
```

zł wyłapuje każdy zgłoszony typ, w tym wyjątki SEH.

Jeśli typ niezarządzany zostanie przechwycony przez catch(Object^), nie zniszczy wyrzucanego obiektu.

Podczas zgłaszania lub wychwytowywania niezarządzanych wyjątków zaleca się użycie opcji kompilatora [/EHsc](../build/reference/eh-exception-handling-model.md) zamiast **/EHs** lub **/EHa**.

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)
