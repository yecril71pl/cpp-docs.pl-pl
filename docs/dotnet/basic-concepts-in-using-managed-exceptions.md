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
ms.openlocfilehash: 4eeec5db00ceca5429f4a3a270e1b249a8955249
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230925"
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>Podstawowe pojęcia związane z używaniem wyjątków zarządzanych

W tym temacie omówiono obsługę wyjątków w zarządzanych aplikacjach. Oznacza to, że aplikacja, która jest skompilowana przy użyciu opcji kompilatora **/CLR** .

## <a name="in-this-topic"></a>W tym temacie:

- [Zgłaszanie wyjątków z opcją/CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor1)

- [Bloki try/catch dla rozszerzeń CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor2)

## <a name="remarks"></a>Uwagi

W przypadku kompilowania z opcją **/CLR** można obsłużyć wyjątki CLR, <xref:System.Exception> a także Klasa standardowa zapewnia wiele przydatnych metod przetwarzania wyjątków CLR i jest zalecane jako klasa bazowa dla klas wyjątków zdefiniowanych przez użytkownika.

Przechwytywanie typów wyjątków pochodnych od interfejsu nie jest obsługiwane w przypadku opcji **/CLR**. Ponadto środowisko uruchomieniowe języka wspólnego nie pozwala na przechwytywanie wyjątków przepełnienia stosu. Wyjątek przepełnienia stosu zakończy proces.

Aby uzyskać więcej informacji o różnicach w obsłudze wyjątków w aplikacjach zarządzanych i niezarządzanych, zobacz [różnice w zachowaniu obsługi wyjątków w obszarze Managed Extensions for C++](../dotnet/differences-in-exception-handling-behavior-under-clr.md).

## <a name="throwing-exceptions-under-clr"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a>Zgłaszanie wyjątków z opcją/CLR

Wyrażenie throw języka C++ zostało rozszerzone, aby zgłosić dojście do typu CLR. Poniższy przykład tworzy niestandardowy typ wyjątku, a następnie zgłasza wystąpienie tego typu:

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

## <a name="trycatch-blocks-for-clr-extensions"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a>Bloki try/catch dla rozszerzeń CLR

Ta sama **`try`** / **`catch`** Struktura bloku może służyć do przechwytywania zarówno wyjątków CLR, jak i natywnych:

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

### <a name="order-of-unwinding-for-c-objects"></a>Kolejność odwinięcia dla obiektów C++

Rozwinięcia występuje dla wszystkich obiektów C++ z destruktorami, które mogą znajdować się w stosie czasu wykonywania między funkcją przerzucania a funkcją obsługi. Ponieważ typy CLR są przydzielane na stercie, odróżnianie nie ma zastosowania do nich.

Kolejność zdarzeń dla zgłoszonego wyjątku jest następująca:

1. Środowisko uruchomieniowe sprawdza stos szukający odpowiedniej klauzuli catch lub w przypadku SEH, z wyjątkiem filtru dla SEH, aby przechwytywać wyjątek. Klauzule catch są przeszukiwane najpierw w kolejności leksykalnej, a następnie dynamicznie w dół stosu wywołań.

1. Po znalezieniu prawidłowej procedury obsługi stos jest odłożony do tego punktu. Dla każdego wywołania funkcji na stosie, jego obiekty lokalne są destruktorne i __finally bloków są wykonywane od najbardziej zagnieżdżonej lokalizacji.

1. Po rozwróceniu stosu jest wykonywana klauzula catch.

### <a name="catching-unmanaged-types"></a>Przechwytywanie typów niezarządzanych

Gdy zostanie zgłoszony typ obiektu niezarządzanego, jest on opakowany jako wyjątek typu <xref:System.Runtime.InteropServices.SEHException> . Podczas wyszukiwania odpowiedniej klauzuli istnieją **`catch`** dwie możliwości.

- Jeśli zostanie napotkany natywny typ języka C++, wyjątek jest nieopakowany i porównywany z napotkanym typem. To porównanie umożliwia przechwycić natywny typ C++ w normalny sposób.

- Jednakże jeśli **`catch`** klauzula typu **SEHException —** lub dowolna z jej klas podstawowych jest analizowana jako pierwsza, klauzula przechwytuje wyjątek. W związku z tym należy umieścić wszystkie klauzule catch, które przechwytują natywne typy C++ przed wszelkimi klauzulami catch typów CLR.

Należy pamiętać, że

```
catch(Object^)
```

oraz

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
