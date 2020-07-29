---
title: safe_cast (C++/CLI i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- safe_cast
- safe_cast_cpp
- stdcli::language::safe_cast
helpviewer_keywords:
- safe_cast keyword [C++]
ms.assetid: 4fa688bf-a8ec-49bc-a4c5-f48134efa4f7
ms.openlocfilehash: 2eb09680ef6e7d1ee90b62eee8c8971fb4963212
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225127"
---
# <a name="safe_cast-ccli-and-ccx"></a>safe_cast (C++/CLI i C++/CX)

Operacja **safe_cast** zwraca określone wyrażenie jako określony typ, jeśli pomyślne; w przeciwnym razie zgłasza `InvalidCastException` .

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

(Nie ma żadnych uwag dla tej funkcji języka, które mają zastosowanie do wszystkich środowisk uruchomieniowych).

### <a name="syntax"></a>Składnia

```cpp
[default]:: safe_cast< type-id >( expression )
```

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

**safe_cast** pozwala zmienić typ określonego wyrażenia. W sytuacjach, w których w pełni oczekuje się, że zmienna lub parametr mają być konwertowane do pewnego typu, można użyć **safe_cast** bez bloku **try-catch** do wykrywania błędów programistycznych podczas opracowywania. Aby uzyskać więcej informacji, zobacz [rzutowanie (C++/CX)](../cppcx/casting-c-cx.md).

### <a name="syntax"></a>Składnia

```cpp
[default]:: safe_cast< type-id >( expression )
```

### <a name="parameters"></a>Parametry

*Identyfikator typu*<br/>
Typ, do którego ma zostać przekształcone *wyrażenie* . Dojście do typu odwołania lub wartości, typ wartości lub odwołanie śledzące do typu odwołania lub wartości.

*wyrażenia*<br/>
Wyrażenie, które oblicza do dojścia do typu odwołania lub wartości, typu wartości lub odwołania śledzenia do typu odwołania lub wartości.

### <a name="remarks"></a>Uwagi

**safe_cast** zgłasza `InvalidCastException` , jeśli nie można przekonwertować *wyrażenia* na typ określony przez *Identyfikator typu*. Aby przechwytywać `InvalidCastException` , określ opcję kompilatora [/EH (model obsługi wyjątków)](../build/reference/eh-exception-handling-model.md) i użyj instrukcji **try/catch** .

### <a name="requirements"></a>Wymagania

Opcja kompilatora:`/ZW`

### <a name="examples"></a>Przykłady

Poniższy przykład kodu demonstruje, jak używać **safe_cast** z środowisko wykonawcze systemu Windows.

```cpp
// safe_cast_ZW.cpp
// compile with: /ZW /EHsc

using namespace default;
using namespace Platform;

interface class I1 {};
interface class I2 {};
interface class I3 {};

ref class X : public I1, public I2 {};

int main(Array<String^>^ args) {
   I1^ i1 = ref new X;
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead
   try {
      I3^ i4 = safe_cast<I3^>(i1);   // Fails because i1 is not derived from I3.
   }
   catch(InvalidCastException^ ic) {
   wprintf(L"Caught expected exception: %s\n", ic->Message);
   }
}
```

```Output
Caught expected exception: InvalidCastException
```

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

**safe_cast** pozwala zmienić typ wyrażenia i wygenerować zweryfikowany kod MSIL.

### <a name="syntax"></a>Składnia

```cpp
[cli]:: safe_cast< type-id >( expression )
```

### <a name="parameters"></a>Parametry

*Identyfikator typu*<br/>
Dojście do typu odwołania lub wartości, typ wartości lub odwołanie śledzące do typu odwołania lub wartości.

*wyrażenia*<br/>
Wyrażenie, które oblicza do dojścia do typu odwołania lub wartości, typu wartości lub odwołania śledzenia do typu odwołania lub wartości.

### <a name="remarks"></a>Uwagi

Wyrażenie `safe_cast<` *identyfikatora typu*wyrażenia `>(` *expression* `)` konwertuje *wyrażenie* operandu na obiekt typu Type *-ID*.

Kompilator przyjmie [static_cast](../cpp/static-cast-operator.md) w większości przypadków, gdy zostanie zaakceptowany **safe_cast**.  Niemniej jednak **safe_cast** ma na celu wygenerowanie zweryfikowanego MSIL, gdzie **`static_cast`** może utworzyć niemożliwy do sprawdzenia MSIL.  Aby uzyskać więcej informacji na temat kodu możliwego do zweryfikowania, zobacz [czysty i możliwy do zweryfikowania kod (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md) i [Peverify.exe (narzędzie PEVerify)](/dotnet/framework/tools/peverify-exe-peverify-tool) .

Podobnie **`static_cast`** jak **safe_cast** wywołuje konwersje zdefiniowane przez użytkownika.

Aby uzyskać więcej informacji na temat rzutowania, zobacz [Operatory rzutowania](../cpp/casting-operators.md).

**safe_cast** nie ma zastosowania a **`const_cast`** (odłożenie **`const`** ).

**safe_cast** znajduje się w przestrzeni nazw interfejsu wiersza polecenia.  Aby uzyskać więcej informacji [, zobacz przestrzenie nazw platform, Default i CLI](platform-default-and-cli-namespaces-cpp-component-extensions.md) .

Aby uzyskać więcej informacji na temat **safe_cast**, zobacz:

- [Rzutowania w stylu C i kompilator /clr (C++/CLI)](c-style-casts-with-clr-cpp-cli.md)

- [Instrukcje: Korzystanie z polecenia safe_cast w języku C++/interfejsie wiersza polecenia](../dotnet/how-to-use-safe-cast-in-cpp-cli.md)

### <a name="requirements"></a>Wymagania

Opcja kompilatora:`/clr`

### <a name="examples"></a>Przykłady

Przykład, w którym kompilator nie akceptuje, **`static_cast`** ale akceptuje **safe_cast** jest dla rzutowania między niepowiązanymi typami interfejsów.  W przypadku **safe_cast**kompilator nie będzie wystawiał błędu konwersji i wykona sprawdzenie w czasie wykonywania, aby sprawdzić, czy Rzutowanie jest możliwe

```cpp
// safe_cast.cpp
// compile with: /clr
using namespace System;

interface class I1 {};
interface class I2 {};
interface class I3 {};

ref class X : public I1, public I2 {};

int main() {
   I1^ i1 = gcnew X;
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead
   try {
      I3^ i4 = safe_cast<I3^>(i1);   // fail at runtime, no common type
   }
   catch(InvalidCastException^) {
      Console::WriteLine("Caught expected exception");
   }
}
```

```Output
Caught expected exception
```

## <a name="see-also"></a>Zobacz także

[Rozszerzenia składników dla platform .NET i platformy UWP](component-extensions-for-runtime-platforms.md)
