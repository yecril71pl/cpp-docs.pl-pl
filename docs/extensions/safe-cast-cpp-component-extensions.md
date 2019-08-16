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
ms.openlocfilehash: 42e141caed720aa29cf918a2bdf69d9a2c4203dc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509548"
---
# <a name="safe_cast-ccli-and-ccx"></a>safe_cast (C++/CLI i C++/CX)

Operacja **safe_cast** zwraca określone wyrażenie jako określony typ, jeśli pomyślne; w przeciwnym razie `InvalidCastException`zgłasza.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

(Nie ma żadnych uwag dla tej funkcji języka, które mają zastosowanie do wszystkich środowisk uruchomieniowych).

### <a name="syntax"></a>Składnia

```cpp
[default]:: safe_cast< type-id >( expression )
```

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

**safe_cast** umożliwia zmianę typu określonego wyrażenia. W sytuacjach, gdy w pełni oczekujesz, że zmienna lub parametr mają być konwertowane do określonego typu, możesz użyć **safe_cast** bez bloku **try-catch** , aby wykryć błędy programowania podczas opracowywania. Aby uzyskać więcej informacji, zobacz [rzutowanieC++(/CX)](../cppcx/casting-c-cx.md).

### <a name="syntax"></a>Składnia

```cpp
[default]:: safe_cast< type-id >( expression )
```

### <a name="parameters"></a>Parametry

*Identyfikator typu*<br/>
Typ, do którego ma zostać przekształcone *wyrażenie* . Dojście do typu odwołania lub wartości, typ wartości lub odwołanie śledzące do typu odwołania lub wartości.

*expression*<br/>
Wyrażenie, które oblicza do dojścia do typu odwołania lub wartości, typu wartości lub odwołania śledzenia do typu odwołania lub wartości.

### <a name="remarks"></a>Uwagi

**safe_cast** zgłasza `InvalidCastException` , jeśli nie można przekonwertować *wyrażenia* na typ określony przez *Identyfikator typu*. Aby przechwytywać `InvalidCastException`, określ opcję kompilatora [/EH (model obsługi wyjątków)](../build/reference/eh-exception-handling-model.md) i użyj instrukcji **try/catch** .

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

**safe_cast** umożliwia zmianę typu wyrażenia i wygenerowanie zweryfikowanego kodu MSIL.

### <a name="syntax"></a>Składnia

```cpp
[cli]:: safe_cast< type-id >( expression )
```

### <a name="parameters"></a>Parametry

*Identyfikator typu*<br/>
Dojście do typu odwołania lub wartości, typ wartości lub odwołanie śledzące do typu odwołania lub wartości.

*expression*<br/>
Wyrażenie, które oblicza do dojścia do typu odwołania lub wartości, typu wartości lub odwołania śledzenia do typu odwołania lub wartości.

### <a name="remarks"></a>Uwagi

`safe_cast<`Wyrażenie *identyfikatora typu wyrażenia konwertuje wyrażenie*operandu na obiekt typu Type *-ID*. `>(``)`

Kompilator akceptuje [static_cast](../cpp/static-cast-operator.md) w większości miejsc, że zaakceptuje **safe_cast**.  Jednak **safe_cast** ma na celu tworzenie zweryfikowanych MSIL, gdzie **static_cast** może generować niemożliwy do sprawdzenia MSIL.  Zobacz [czysty i możliwy do zweryfikowania kod (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md) i [PEVerify. exe (narzędzie PEVerify)](/dotnet/framework/tools/peverify-exe-peverify-tool) , aby uzyskać więcej informacji na temat kodu możliwego do zweryfikowania.

Podobnie jak **static_cast**, **safe_cast** wywołuje konwersje zdefiniowane przez użytkownika.

Aby uzyskać więcej informacji na temat rzutowania, zobacz [Operatory rzutowania](../cpp/casting-operators.md).

**safe_cast** nie stosuje **const_cast** (Rzutowanie **const**).

**safe_cast** znajduje się w przestrzeni nazw interfejsu wiersza polecenia.  Aby uzyskać więcej informacji [, zobacz przestrzenie nazw platform, Default i CLI](platform-default-and-cli-namespaces-cpp-component-extensions.md) .

Aby uzyskać więcej informacji na temat **safe_cast**, zobacz:

- [Rzutowania w stylu języka C z/CLRC++(/CLI)](c-style-casts-with-clr-cpp-cli.md)

- [Instrukcje: korzystanie z polecenia safe_cast w języku C++/interfejsie wiersza polecenia](../dotnet/how-to-use-safe-cast-in-cpp-cli.md)

### <a name="requirements"></a>Wymagania

Opcja kompilatora:`/clr`

### <a name="examples"></a>Przykłady

Przykład, w którym kompilator nie akceptuje **static_cast** , ale akceptuje **safe_cast** jest dla rzutowania między niepowiązanymi typami interfejsów.  W przypadku **safe_cast**kompilator nie będzie wystawiał błędu konwersji i wykona sprawdzenie w czasie wykonywania, aby sprawdzić, czy Rzutowanie jest możliwe

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

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)
