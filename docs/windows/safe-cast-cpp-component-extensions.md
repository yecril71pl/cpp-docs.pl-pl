---
title: safe_cast (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- safe_cast
- safe_cast_cpp
- stdcli::language::safe_cast
dev_langs:
- C++
helpviewer_keywords:
- safe_cast keyword [C++]
ms.assetid: 4fa688bf-a8ec-49bc-a4c5-f48134efa4f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8d5a4f92e16c2d758fa5e2b88575b12d5710dd08
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404218"
---
# <a name="safecast-c-component-extensions"></a>safe_cast (C++ Component Extensions)

**Safe_cast** limit czasu operacji zwraca określone wyrażenie jako określony typ, jeśli to się powiedzie; w przeciwnym razie zgłasza `InvalidCastException`.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

(Nie ma żadnych uwag dla tej funkcji języka, które są stosowane do wszystkich środowisk uruchomieniowych).

### <a name="syntax"></a>Składnia

```cpp
[default]:: safe_cast<
type-id
>(
expression
)  
```

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

**safe_cast** pozwala na zmianę typu określonego wyrażenia. W sytuacjach, w pełni nieoczekiwany zmiennej lub parametru, aby umożliwiać konwersję do pewnego typu, można użyć **safe_cast** bez **try-catch —** bloku, aby wykryć błędy programowania podczas programowania. Aby uzyskać więcej informacji, zobacz [rzutowanie (C + +/ CX)](https://msdn.microsoft.com/library/windows/apps/hh755802.aspx).

### <a name="syntax"></a>Składnia

```cpp
[default]:: safe_cast<
type-id
>(
expression
)  
```

### <a name="parameters"></a>Parametry

*Identyfikator typu*<br/>
Typ docelowy konwersji *wyrażenie* do. Dojście do odwołanie lub typ wartości, typem wartości lub odwołanie śledzące do typu odwołania lub wartość.

*Wyrażenie*<br/>
Na wyrażenie obliczane do uchwytu odwołania lub typu wartości, typem wartości lub odwołanie śledzące do typu odwołania lub wartość.

### <a name="remarks"></a>Uwagi

**safe_cast** zgłasza `InvalidCastException` Jeśli go nie można przekonwertować *wyrażenie* do typu określonego przez *identyfikator typu*. Aby przechwycić `InvalidCastException`, określ [/EH (Model obsługi wyjątku)](../build/reference/eh-exception-handling-model.md) — opcja kompilatora i użyj **bloku try/catch** instrukcji.

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

### <a name="examples"></a>Przykłady

Poniższy przykład kodu demonstruje sposób używania **safe_cast** za pomocą środowiska wykonawczego Windows.

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

**safe_cast** można zmienić typu wyrażenia i generowanie weryfikowalny kod MSIL.

### <a name="syntax"></a>Składnia

```cpp
[cli]:: safe_cast<
type-id
>(
expression
)  
```

### <a name="parameters"></a>Parametry

*Identyfikator typu*<br/>
Dojście do odwołanie lub typ wartości, typem wartości lub odwołanie śledzące do typu odwołania lub wartość.

*Wyrażenie*<br/>
Na wyrażenie obliczane do uchwytu odwołania lub typu wartości, typem wartości lub odwołanie śledzące do typu odwołania lub wartość.

### <a name="remarks"></a>Uwagi

Wyrażenie `safe_cast<` *identyfikator typu*`>(`*wyrażenie* `)` Konwertuje obiekt identyfikator typu typu wyrażenia argumentu operacji.

Kompilator będzie akceptować [static_cast](../cpp/static-cast-operator.md) w większości miejsc, które go obsługują **safe_cast**.  Jednak **safe_cast** jest gwarantowane do produkcji weryfikowalny MSIL, gdzie jako **static_cast** może utworzyć nieweryfikowalnego MSIL.  Zobacz [czystej i możliwe do zweryfikowania kodu (C + +/ CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md) i [Peverify.exe (narzędzie PEVerify)](/dotnet/framework/tools/peverify-exe-peverify-tool) więcej informacji na temat weryfikowalny kod.

Podobnie jak **static_cast**, **safe_cast** wywołuje konwersje zdefiniowane przez użytkownika.

Aby uzyskać więcej informacji na temat rzutowania zobacz [operatorów rzutowania](../cpp/casting-operators.md).

**safe_cast** nie ma zastosowania **const_cast** (oddać **const**).

**safe_cast** znajduje się w przestrzeni nazw cli.  Zobacz [platformy, domyślna i cli przestrzenie nazw](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md) Aby uzyskać więcej informacji.

Aby uzyskać więcej informacji na temat **safe_cast**, zobacz:

- [Rzutowania w stylu języka C z/CLR (C + +/ CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)

- [Instrukcje: korzystanie z polecenia safe_cast w języku C++/interfejsie wiersza polecenia](../dotnet/how-to-use-safe-cast-in-cpp-cli.md)  

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

Jeden przykład gdzie kompilator nie będzie akceptować **static_cast** , ale będzie akceptować **safe_cast** dotyczy rzutowania między typami niepowiązanych interfejsu.  Za pomocą **safe_cast**, kompilator nie będzie wystawiać błąd konwersji i wykona sprawdzenie w czasie wykonywania, aby zobaczyć, jeśli możliwe jest rzutowanie

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

## <a name="see-also"></a>Zobacz też

[Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)