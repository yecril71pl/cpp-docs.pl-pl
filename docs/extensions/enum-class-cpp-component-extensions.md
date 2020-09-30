---
title: klasa wyliczeniowa  (C++/CLI i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
ms.assetid: 8010fa8c-bad6-45b4-8214-b4db64d7ffe1
ms.openlocfilehash: 9acf93976b2f7751e85bf3ed0ddd2735c29e121c
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590319"
---
# <a name="enum-class--ccli-and-ccx"></a>klasa wyliczeniowa  (C++/CLI i C++/CX)

Deklaruje Wyliczenie w zakresie przestrzeni nazw, który jest typem zdefiniowanym przez użytkownika składającym się z zestawu nazwanych stałych o nazwie Enumerators.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

### <a name="remarks"></a>Uwagi

C++/CX i C++/CLI obsługują **publiczną klasę** wyliczeniową i **prywatną klasę enum** , która jest podobna do standardowej **klasy wyliczeniowej** C++, ale z dodaniem specyfikatora dostępności. W obszarze **/CLR**typ **klasy enum** języka C++ 11 jest dozwolony, ale generuje C4472 ostrzegawczy, który jest przeznaczony do zapewnienia, że naprawdę chcesz, aby typ wyliczenia ISO, a nie typ c++/CX i c++/CLI. Aby uzyskać więcej informacji na temat standardowego **`enum`** słowa kluczowego ISO języka C++, zobacz [wyliczenia](../cpp/enumerations-cpp.md).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

### <a name="syntax"></a>Składnia

```cpp
      access
      enum class
      enumeration-identifier
      [:underlying-type] { enumerator-list } [var];
accessenum structenumeration-identifier[:underlying-type] { enumerator-list } [var];
```

### <a name="parameters"></a>Parametry

*niego*<br/>
Dostępność wyliczenia, która może być **`public`** lub **`private`** .

*Wyliczenie — identyfikator*<br/>
Nazwa wyliczenia.

*Typ podstawowy*<br/>
Obowiązkowe Podstawowy typ wyliczenia.

Obowiązkowe. Tylko środowisko wykonawcze systemu Windows) podstawowy typ wyliczenia, który może mieć wartość **`bool`** ,,,,,, **`char`** `char16` `int16` `uint16` **`int`** `uint32` , `int64` lub `uint64` .

*moduł wyliczający — lista*<br/>
Rozdzielana przecinkami lista nazw modułów wyliczających.

Wartość każdego modułu wyliczającego jest wyrażeniem stałym zdefiniowanym niejawnie przez kompilator lub jawnie przez notację, wyrażenie *stałe modułu wyliczającego* `=` *constant-expression*. Domyślnie wartość pierwszego modułu wyliczającego jest równa zero, jeśli jest niejawnie zdefiniowana. Wartość każdego kolejnego zdefiniowanego niejawnie modułu wyliczającego jest wartością poprzedniego modułu wyliczającego + 1.

*funkcję*<br/>
Obowiązkowe Nazwa zmiennej typu wyliczenia.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji i zapoznać się z przykładami, zobacz [wyliczenia](../cppcx/enums-c-cx.md).

Należy zauważyć, że kompilator emituje komunikaty o błędach, jeśli wyrażenie stałe definiujące wartość modułu wyliczającego nie może być reprezentowane przez *Typ podstawowy*.  Jednak kompilator nie zgłasza błędu dla wartości, która jest nieodpowiedni dla typu źródłowego. Na przykład:

- Jeśli *Typ podstawowy* jest wartością numeryczną, a moduł wyliczający określa maksymalną wartość tego typu, wartość następnego niejawnie zdefiniowanego wyliczenia nie może być reprezentowana.

- Jeśli *Typ podstawowy* jest **`bool`** i więcej niż dwa moduły wyliczające są zdefiniowane niejawnie, nie można przedstawić modułów wyliczających po pierwszych dwóch.

- Jeśli *typem podstawowym* jest `char16` , a wartość wyliczenia jest z zakresu od 0xD800 do 0xDFFF, wartość może być reprezentowana. Jednakże wartość logiczna jest nieprawidłowa, ponieważ reprezentuje połowę pary dwuskładnikowej Unicode i nie powinna być wyświetlana w izolacji.

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

### <a name="syntax"></a>Składnia

```cpp
      access
      enum class
      name [:type] { enumerator-list } var;
accessenum structname [:type] { enumerator-list } var;
```

### <a name="parameters"></a>Parametry

*niego*<br/>
Dostępność wyliczenia. Może być albo **`public`** **`private`** .

*moduł wyliczający — lista*<br/>
Rozdzielana przecinkami lista identyfikatorów (modułów wyliczających) w wyliczeniu.

*Nazwij*<br/>
Nazwa wyliczenia. Anonimowe wyliczenia zarządzane są niedozwolone.

*Wprowadź*<br/>
Obowiązkowe Typ podstawowy *identyfikatorów*. Może to być dowolny typ skalarny, taki jak podpisane lub niepodpisane wersje systemu **`int`** , **`short`** lub **`long`** .  **`bool`** lub **`char`** jest również dozwolone.

*funkcję*<br/>
Obowiązkowe Nazwa zmiennej typu wyliczenia.

### <a name="remarks"></a>Uwagi

**Klasa enum** i **Struktura wyliczenia** są równoważnymi deklaracjami.

Istnieją dwa typy wyliczeniowe: Managed lub C++/CX i Standard.

Wyliczenie zarządzane lub C++/CX może być zdefiniowane w następujący sposób:

```cpp
public enum class day {sun, mon };
```

i jest semantycznie równoważne z:

```cpp
ref class day {
public:
   static const int sun = 0;
   static const int mon = 1;
};
```

Standardowe Wyliczenie może być zdefiniowane w następujący sposób:

```cpp
enum day2 { sun, mon };
```

i jest semantycznie równoważne z:

```cpp
static const int sun = 0;
static const int mon = 1;
```

Zarządzane nazwy modułów wyliczających (*identyfikatory*) nie są wstrzykiwane do zakresu, w którym zdefiniowano Wyliczenie; wszystkie odwołania do modułów wyliczających muszą być w pełni kwalifikowane*name*( `::` *Identyfikator*nazwy).  Z tego powodu nie można zdefiniować anonimowego wyliczenia zarządzanego.

Moduły wyliczające standardowe wyliczenie są silnie wstrzykiwane do otaczającego zakresu.  Oznacza to, że jeśli istnieje inny symbol o takiej samej nazwie jak moduł wyliczający w otaczającym zakresie, kompilator wygeneruje błąd.

W programie Visual Studio 2002 i Visual Studio 2003 moduły wyliczające zostały słabo wstrzykiwane (widoczne w otaczającym zakresie, chyba że istnieje inny identyfikator o tej samej nazwie).

Jeśli zdefiniowano standardowe Wyliczenie języka C++ (bez **`class`** lub **`struct`** ), kompilacja z `/clr` spowoduje, że Wyliczenie zostanie skompilowane jako zarządzane Wyliczenie.  Wyliczenie ma nadal semantykę niezarządzanego wyliczania.  Należy pamiętać, że kompilator wprowadza atrybut, `Microsoft::VisualC::NativeEnumAttribute` Aby zidentyfikować zamiar programisty, że Wyliczenie ma być natywnym wyliczeniem.  Inne kompilatory będą po prostu wyświetlać standardowe Wyliczenie jako zarządzane Wyliczenie.

Nazwane, standardowe Wyliczenie skompilowane przy użyciu `/clr` będzie widoczne w zestawie jako zarządzane Wyliczenie i może być używane przez dowolny inny zarządzany kompilator.   Jednak nienazwane Wyliczenie standardowe nie będzie publicznie widoczne z zestawu.

W programie Visual Studio 2002 i Visual Studio 2003, standardowe Wyliczenie używane jako typ w parametrze funkcji:

```cpp
// mcppv2_enum.cpp
// compile with: /clr
enum E { a, b };
void f(E) {System::Console::WriteLine("hi");}

int main() {
   E myi = b;
   f(myi);
}
```

emituje następujące instrukcje w języku MSIL dla sygnatury funkcji:

```cpp
void f(int32);
```

Jednak w bieżących wersjach kompilatora standardowe wyliczenie jest emitowane jako zarządzane Wyliczenie z [NativeEnumAttribute] i następujące w języku MSIL dla sygnatury funkcji:

```cpp
void f(E)
```

Aby uzyskać więcej informacji na temat natywnych typów wyliczeniowych, zobacz [deklaracje wyliczenia języka C++](../cpp/enumerations-cpp.md).

Aby uzyskać więcej informacji na temat typów wyliczeniowych CLR, zobacz:

- [Typ podstawowy wyliczenia](../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

```cpp
// mcppv2_enum_2.cpp
// compile with: /clr
// managed enum
public enum class m { a, b };

// standard enum
public enum n { c, d };

// unnamed, standard enum
public enum { e, f } o;

int main()
{
   // consume managed enum
   m mym = m::b;
   System::Console::WriteLine("no automatic conversion to int: {0}", mym);
   System::Console::WriteLine("convert to int: {0}", (int)mym);

   // consume standard enum
   n myn = d;
   System::Console::WriteLine(myn);

   // consume standard, unnamed enum
   o = f;
   System::Console::WriteLine(o);
}
```

```Output
no automatic conversion to int: b

convert to int: 1

1

1
```

## <a name="see-also"></a>Zobacz też

[Rozszerzenia składników dla platform .NET i platformy UWP](component-extensions-for-runtime-platforms.md)
