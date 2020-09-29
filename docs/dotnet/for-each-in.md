---
title: for each, in
description: C++/CLI for each, w opisach i przykładach instrukcji.
ms.date: 09/25/2020
ms.topic: reference
f1_keywords:
- cliext::foreach
- for
- each
- in
helpviewer_keywords:
- for each keyword [C++]
ms.assetid: 0c3a364b-2747-43f3-bb8d-b7d3b7023f79
ms.openlocfilehash: 7f228a773dfcbe791e26ea3e1bd8cfba7f3ab028
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413922"
---
# <a name="for-each-in"></a>for each, in

Wykonuje iterację przez tablicę lub kolekcję. To niestandardowe słowo kluczowe jest dostępne zarówno w projektach C++/CLI, jak i macierzystych projektach C++. Jednak jego użycie nie jest zalecane. Rozważ użycie w zamian standardowego [zakresu dla instrukcji (C++)](../cpp/range-based-for-statement-cpp.md) .

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

### <a name="syntax"></a>Składnia

> **for each (** *type* *Identyfikator* **typu w** *wyrażeniu* **) {**\
> &nbsp;&nbsp;&nbsp;&nbsp;*zatwierdzeni*\
> **}**

### <a name="parameters"></a>Parametry

*Wprowadź*<br/>
Typ `identifier` .

*identyfikatora*<br/>
Zmienna iteracyjna, która reprezentuje element kolekcji.  Gdy `identifier` jest [operatorem odwołania śledzącego](../extensions/tracking-reference-operator-cpp-component-extensions.md), można zmodyfikować element.

*wyrażenia*<br/>
Wyrażenie tablicy lub kolekcja. Element kolekcji musi być taki, aby kompilator mógł przekonwertować go na `identifier` Typ.

*zatwierdzeni*<br/>
Jedna lub więcej instrukcji do wykonania.

### <a name="remarks"></a>Uwagi

`for each`Instrukcja służy do iteracji w kolekcji. Można modyfikować elementy w kolekcji, ale nie można dodawać ani usuwać elementów.

*Instrukcje* są wykonywane dla każdego elementu w tablicy lub kolekcji. Po ukończeniu iteracji dla wszystkich elementów w kolekcji, sterowanie jest przekazywane do instrukcji, która następuje po `for each` bloku.

`for each` i `in` są [kontekstowymi słowami kluczowymi](../extensions/context-sensitive-keywords-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

### <a name="requirements"></a>Wymagania

Opcja kompilatora: **/zw**

### <a name="example"></a>Przykład

Ten przykład pokazuje, jak używać `for each` do iterowania przez ciąg.

```cpp
// for_each_string1.cpp
// compile with: /ZW
#include <stdio.h>
using namespace Platform;

ref struct MyClass {
   property String^ MyStringProperty;
};

int main() {
   String^ MyString = ref new String("abcd");

   for each ( char c in MyString )
      wprintf("%c", c);

   wprintf("/n");

   MyClass^ x = ref new MyClass();
   x->MyStringProperty = "Testing";

   for each( char c in x->MyStringProperty )
      wprintf("%c", c);
}
```

```Output
abcd

Testing
```

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

### <a name="remarks"></a>Uwagi

Składnia CLR jest taka sama jak składnia **wszystkie środowiska uruchomieniowe** , chyba że jest to podano poniżej.

*wyrażenia*<br/>
Wyrażenie tablicy zarządzanej lub kolekcja. Element kolekcji musi być taki, aby kompilator mógł go konwertować z <xref:System.Object> do typu *identyfikatora* .

*wyrażenie* daje w wyniku typ, który implementuje <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> lub typ, który definiuje `GetEnumerator` metodę, która zwraca typ, który implementuje <xref:System.Collections.IEnumerator> lub deklaruje wszystkie metody, które są zdefiniowane w `IEnumerator` .

### <a name="requirements"></a>Wymagania

Opcja kompilatora: **/CLR**

### <a name="example"></a>Przykład

Ten przykład pokazuje, jak używać `for each` do iterowania przez ciąg.

```cpp
// for_each_string2.cpp
// compile with: /clr
using namespace System;

ref struct MyClass {
   property String ^ MyStringProperty;
};

int main() {
   String ^ MyString = gcnew String("abcd");

   for each ( Char c in MyString )
      Console::Write(c);

   Console::WriteLine();

   MyClass ^ x = gcnew MyClass();
   x->MyStringProperty = "Testing";

   for each( Char c in x->MyStringProperty )
      Console::Write(c);
}
```

```Output
abcd

Testing
```

## <a name="see-also"></a>Zobacz także

[Rozszerzenia składników dla platform środowiska uruchomieniowego](../extensions/component-extensions-for-runtime-platforms.md)\
[Oparta na zakresie for — instrukcja (C++)](../cpp/range-based-for-statement-cpp.md)
