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
ms.openlocfilehash: cf241d4e599ad58c2e39680d8ed4e4e250b42b18
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988549"
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>Podstawowe pojęcia związane z używaniem wyjątków zarządzanych

W tym temacie omówiono obsługę wyjątków w zarządzanych aplikacjach. Oznacza to, że aplikacja, która jest skompilowana przy użyciu opcji kompilatora **/CLR** .

## <a name="in-this-topic"></a>W tym temacie

- [Zgłaszanie wyjątków z opcją/CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor1)

- [Bloki try/catch dla rozszerzeń CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor2)

## <a name="remarks"></a>Uwagi

W przypadku kompilowania przy użyciu opcji **/CLR** można obsłużyć wyjątki CLR, a także klasę <xref:System.Exception> standardowa zapewnia wiele przydatnych metod przetwarzania wyjątków CLR i jest zalecane jako klasa bazowa dla klas wyjątków zdefiniowanych przez użytkownika.

Przechwytywanie typów wyjątków pochodnych od interfejsu nie jest obsługiwane w przypadku opcji **/CLR**. Ponadto środowisko uruchomieniowe języka wspólnego nie pozwala na przechwytywanie wyjątków przepełnienia stosu. Wyjątek przepełnienia stosu zakończy proces.

Aby uzyskać więcej informacji o różnicach w obsłudze wyjątków w aplikacjach zarządzanych i niezarządzanych, zobacz [różnice w zachowaniu obsługi C++wyjątków w obszarze rozszerzenia zarządzane dla programu ](../dotnet/differences-in-exception-handling-behavior-under-clr.md).

##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a>Zgłaszanie wyjątków z opcją/CLR

Wyrażenie C++ throw zostało rozszerzone, aby zgłosić dojście do typu CLR. Poniższy przykład tworzy niestandardowy typ wyjątku, a następnie zgłasza wystąpienie tego typu:

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

Typ wartości musi być opakowany przed zgłoszeniem:

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

##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a>Bloki try/catch dla rozszerzeń CLR

**Ta sama struktura** bloku **catch**/może służyć do przechwytywania wyjątków CLR i natywnych:

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

### <a name="order-of-unwinding-for-c-objects"></a>Kolejność odwinięcia C++ obiektów

Rozwinięcia występuje dla wszystkich C++ obiektów z destruktorami, które mogą znajdować się w stosie czasu wykonywania między funkcją przerzucania a funkcją obsługi. Ponieważ typy CLR są przydzielane na stercie, odróżnianie nie ma zastosowania do nich.

Kolejność zdarzeń dla zgłoszonego wyjątku jest następująca:

1. Środowisko uruchomieniowe sprawdza stos szukający odpowiedniej klauzuli catch lub w przypadku SEH, z wyjątkiem filtru dla SEH, aby przechwytywać wyjątek. Klauzule catch są przeszukiwane najpierw w kolejności leksykalnej, a następnie dynamicznie w dół stosu wywołań.

1. Po znalezieniu prawidłowej procedury obsługi stos jest odłożony do tego punktu. Dla każdego wywołania funkcji na stosie, jego obiekty lokalne są destruktorne i __finally bloków są wykonywane od najbardziej zagnieżdżonej lokalizacji.

1. Po rozwróceniu stosu jest wykonywana klauzula catch.

### <a name="catching-unmanaged-types"></a>Przechwytywanie typów niezarządzanych

Gdy zgłaszany jest typ obiektu niezarządzanego, jest opakowany z wyjątkiem typu <xref:System.Runtime.InteropServices.SEHException>. Podczas wyszukiwania odpowiedniej klauzuli **catch** istnieją dwie możliwości.

- Jeśli zostanie napotkany typ natywny C++ , wyjątek jest nieopakowany i porównywany z napotkanym typem. To porównanie umożliwia przechwycić C++ typ natywny w normalny sposób.

- Jednakże jeśli klauzula **catch** typu **SEHException —** lub dowolna z jej klas podstawowych jest analizowana jako pierwsza, klauzula przechwytuje wyjątek. W związku z tym należy umieścić wszystkie klauzule catch, C++ które przechwytują typy natywne przed wszystkimi klauzulami catch typów CLR.

Należy pamiętać o następujących kwestiach:

```
catch(Object^)
```

and

```
catch(...)
```

przechwytuje wszystkie zgłoszone typy, w tym wyjątki SEH.

Jeśli typ niezarządzany zostanie przechwycony przez catch (Object ^), nie spowoduje to zniszczenia zgłoszonego obiektu.

W przypadku zgłaszania lub przechwytywania wyjątków niezarządzanych zalecamy użycie opcji kompilatora [/EHsc](../build/reference/eh-exception-handling-model.md) zamiast **/EHS** lub **/EHa**.

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md)
