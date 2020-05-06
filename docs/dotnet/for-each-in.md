---
title: for each, in
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::foreach
- for
- each
- in
helpviewer_keywords:
- for each keyword [C++]
ms.assetid: 0c3a364b-2747-43f3-bb8d-b7d3b7023f79
ms.openlocfilehash: f1f5523eb22bd8a839da9b3f73dd6c3718b4fd63
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825798"
---
# <a name="for-each-in"></a>for each, in

Wykonuje iterację przez tablicę lub kolekcję. To niestandardowe słowo kluczowe jest dostępne zarówno w projektach C++/CLI, jak i macierzystych projektach C++. Jego stosowanie nie jest jednak zalecane. Rozważ użycie w zamian standardowego [zakresu dla instrukcji (C++)](../cpp/range-based-for-statement-cpp.md) .

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

### <a name="syntax"></a>Składnia

> **for each (** *type* *Identyfikator* **typu w** *wyrażeniu* **) {**\
> &nbsp;&nbsp;&nbsp;&nbsp;*zatwierdzeni*\
> **}**

### <a name="parameters"></a>Parametry

*Wprowadź*<br/>
Typ `identifier`.

*identyfikatora*<br/>
Zmienna iteracyjna, która reprezentuje element kolekcji.  Gdy `identifier` jest [operatorem odwołania śledzącego](../extensions/tracking-reference-operator-cpp-component-extensions.md), można zmodyfikować element.

*wyrażenia*<br/>
Wyrażenie tablicy lub kolekcja. Element kolekcji musi być taki, aby kompilator mógł przekonwertować go na `identifier` typ.

*zatwierdzeni*<br/>
Jedna lub więcej instrukcji do wykonania.

### <a name="remarks"></a>Uwagi

`for each` Instrukcja służy do iteracji w kolekcji. Możesz modyfikować elementy w kolekcji, ale nie możesz dodawać ani usuwać elementów.

*Instrukcje* są wykonywane dla każdego elementu w tablicy lub kolekcji. Po ukończeniu iteracji dla wszystkich elementów w kolekcji, sterowanie jest przekazywane do instrukcji, która następuje po `for each` bloku.

`for each`i `in` są [kontekstowymi słowami kluczowymi](../extensions/context-sensitive-keywords-cpp-component-extensions.md).

Więcej informacji:

- [Iterowanie przez standardową kolekcję bibliotek C++ za pomocą instrukcji for each](../dotnet/iterating-over-stl-collection-by-using-for-each.md)

- [Instrukcje: iterowanie przez tablice za pomocą instrukcji for each](../dotnet/how-to-iterate-over-arrays-with-for-each.md)

- [Instrukcje: iterowanie przez kolekcję ogólną za pomocą instrukcji for each](../dotnet/how-to-iterate-over-a-generic-collection-with-for-each.md)

- [Instrukcje: iterowanie przez kolekcję zdefiniowaną przez użytkownika za pomocą instrukcji for each](../dotnet/how-to-iterate-over-a-user-defined-collection-with-for-each.md)

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

**Dane wyjściowe**

```Output
abcd

Testing
```

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

**Uwagi**

Składnia CLR jest taka sama jak składnia **wszystkie środowiska uruchomieniowe** , chyba że jest to podano poniżej.

*wyrażenia*<br/>
Wyrażenie tablicy zarządzanej lub kolekcja. Element kolekcji musi być taki, aby kompilator mógł go konwertować z <xref:System.Object> do typu *identyfikatora* .

*wyrażenie* daje w wyniku typ, który implementuje <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>lub typ, który definiuje `GetEnumerator` metodę, która zwraca typ, który implementuje <xref:System.Collections.IEnumerator> lub deklaruje wszystkie metody, które są zdefiniowane w. `IEnumerator`

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

**Dane wyjściowe**

```Output
abcd

Testing
```

## <a name="see-also"></a>Zobacz także

[Component Extensions dla platform środowiska uruchomieniowego](../extensions/component-extensions-for-runtime-platforms.md)
