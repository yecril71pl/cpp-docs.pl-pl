---
title: Klasa wyliczenia (C + +/ CLI i C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 8010fa8c-bad6-45b4-8214-b4db64d7ffe1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7c63a043b8f1a91654c0b765632969b82725a3c0
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066165"
---
# <a name="enum-class--ccli-and-ccx"></a>Klasa wyliczenia (C + +/ CLI i C + +/ CX)

Deklaruje wyliczenie w zakresie przestrzeni nazw, która jest typ zdefiniowany przez użytkownika, składających się z szeregu nazwanych stałych zwanych wyliczeniami.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

### <a name="remarks"></a>Uwagi

C + +/ CX i C + +/ interfejsu wiersza polecenia **klasy publicznym typie wyliczeniowym** i **klasa wyliczeniowa prywatnej** które są podobne do standardowego języka C++ **klasa wyliczeniowa** z dodatkową dostępność Specyfikator. W obszarze **/CLR**, C ++ 11 **klasa wyliczeniowa** typ jest dozwolone, ale spowoduje wygenerowanie ostrzeżenia C4472, który jest przeznaczony do upewnij się, że naprawdę chcesz typu wyliczeniowego ISO i nie C + +/ CX i C + +/ interfejsu wiersza polecenia typu. Aby uzyskać więcej informacji na temat ISO Standard C++ **wyliczenia** — słowo kluczowe, zobacz [wyliczenia](../cpp/enumerations-cpp.md).

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

*Dostęp do*<br/>
Dostępność wyliczenia, które mogą być **publicznych** lub **prywatnej**.

*Identyfikator wyliczenia*<br/>
Nazwa wyliczenia.

*Typ podstawowy*<br/>
(Opcjonalnie) Podstawowy typ wyliczenia.

(Opcjonalnie. Tylko Windows Runtime) podstawowym typem wyliczenia, które mogą być **bool**, **char**, `char16`, `int16`, `uint16`, **int**, `uint32`, `int64`, lub `uint64`.

*Moduł wyliczający listę*<br/>
Rozdzielana przecinkami lista nazw wyliczania.

Wartość każdy moduł wyliczający jest wyrażeniem stałym, zdefiniowanego albo niejawnie przez kompilator, lub jawnie przez notacji, *modułu wyliczającego*`=`*wyrażenie_stałe*. Domyślnie wartość modułu wyliczającego pierwszego wynosi zero, jeśli jest niejawnie definiowany. Wartość każdej kolejnej modułu wyliczającego niejawnie definiowany jest wartość poprzedniego enumeratora + 1.

*var*<br/>
(Opcjonalnie) Nazwa zmiennej typu wyliczenia.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji i przykładów, zobacz [wyliczenia](https://msdn.microsoft.com/%20library/windows/apps/hh755820.aspx).

Należy pamiętać, że kompilator generuje komunikaty o błędach, jeśli wyrażenie stałe, który definiuje wartość modułu wyliczającego nie może być przedstawiona przez *typu bazowego*.  Jednak kompilator nie zgłasza błędu dla wartości, który jest nieodpowiedni dla podstawowego typu. Na przykład:

- Jeśli *typu bazowego* to pole liczbowe, a moduł wyliczający określa maksymalną wartość dla tego typu, nie może być przedstawiony wartość następnego enumeratoin niejawnie zdefiniowany.

- Jeśli *typu bazowego* jest **bool**, i więcej niż dwa moduły wyliczające są niejawną kolekcją zdefiniowane moduły wyliczające po pierwsze dwa nie może być reprezentowana.

- Jeśli *typu bazowego* jest `char16`i wartość wyliczenia zakresu od 0xD800 do 0xDFFF, może być reprezentowany wartość. Jednak wartości logicznie niepoprawne, ponieważ reprezentuje on połowa Unicode dwuskładnikowy i nie powinny być wyświetlane w izolacji.

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

### <a name="syntax"></a>Składnia

```cpp
      access
      enum class
      name [:type] { enumerator-list } var;
accessenum structname [:type] { enumerator-list } var;
```

### <a name="parameters"></a>Parametry

*Dostęp do*<br/>
Dostępność wyliczenia. Może być **publicznych** lub **prywatnej**.

*Moduł wyliczający listę*<br/>
Rozdzielana przecinkami lista identyfikatorów (moduły wyliczające), która znajduje się w wyliczeniu.

*Nazwa*<br/>
Nazwa wyliczenia. Anonimowe wyliczenia zarządzane nie są dozwolone.

*Typ*<br/>
(Opcjonalnie) Typ podstawowy elementu *identyfikatory*. Może to być dowolny typ skalarne, takie jak podpisane lub niepodpisane wersje **int**, **krótki**, lub **długie**.  **wartość logiczna** lub **char** jest również dozwolony.

*var*<br/>
(Opcjonalnie) Nazwa zmiennej typu wyliczenia.

### <a name="remarks"></a>Uwagi

**Klasa wyliczeniowa** i **enum struct** są równoważne deklaracji.

Istnieją dwa rodzaje wyliczeń: zarządzane lub C + +/ CX i standard.

Zarządzane lub C + +/ CX wyliczenia można zdefiniować w następujący sposób,

```cpp
public enum class day {sun, mon };
```

i semantycznie równoważne:

```cpp
ref class day {
public:
   static const int sun = 0;
   static const int mon = 1;
};
```

Standardowa wyliczenia można zdefiniować w następujący sposób:

```cpp
enum day2 { sun, mon };
```

i semantycznie równoważne:

```cpp
static const int sun = 0;
static const int mon = 1;
```

Zarządzane nazwy modułu wyliczającego (*identyfikatory*) nie są wprowadzane do zakresu, w którym zdefiniowano wyliczenia; wszystkie odniesienia do wyliczenia musi być w pełni kwalifikowana (*nazwa* `::` *identyfikator*).  Z tego powodu nie można zdefiniować wyliczenie zarządzane anonimowe.

Moduły wyliczające standardowa wyliczenia silnie są wprowadzane w zasięgu.  Oznacza to jeśli istnieje inny symbol o tej samej nazwie jak moduł wyliczający w zasięgu, kompilator wygeneruje błąd.

W Visual Studio 2002 i Visual Studio 2003 moduły wyliczające słabo zostały dodane (widoczne w zasięgu o ile nie wystąpił inny identyfikator o takiej samej nazwie).

Jeśli nie zdefiniowano standard wyliczeniową C++ (bez **klasy** lub **struktury**), kompilowanie za pomocą `/clr` spowoduje, że wyliczenie jest kompilowana jako wyliczenie zarządzane.  Wyliczanie nadal ma semantykę niezarządzane wyliczenia.  Należy pamiętać, kompilator wprowadza atrybutu `Microsoft::VisualC::NativeEnumAttribute` do identyfikowania intencji programisty dla wyliczenia jako natywnym wyliczeniem.  Inne kompilatory po prostu zostanie wyświetlony standardowy wyliczenia jako wyliczenie zarządzane.

Element o nazwie, standardowe wyliczenia skompilowany przy użyciu `/clr` będą widoczne w zestawie, jako wyliczenie zarządzane i mogą być używane przez inne zarządzane kompilatora.   Jednak bez nazwy wyliczenia standard nie będą publicznie widoczne z zestawu.

W Visual Studio 2002 i Visual Studio 2003, standard wyliczenia, używany jako typ parametru funkcji:

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

czy emitować następujące opcje w MSIL dla sygnatury funkcji:

```cpp
void f(int32);
```

Jednak w bieżącej wersji kompilatora standardowa wyliczenia jest emitowane, jako wyliczenie zarządzane przy użyciu [NativeEnumAttribute] i następujące opcje w MSIL dla sygnatury funkcji:

```cpp
void f(E)
```

Aby uzyskać więcej informacji dotyczących natywnych typów wyliczeniowych, zobacz [deklaracje modułów Wyliczających języka C++](../cpp/enumerations-cpp.md).

Aby uzyskać więcej informacji na temat typów wyliczeniowych CLR zobacz:

- [Podstawowym typem wyliczenia](../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/clr`

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

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](../windows/component-extensions-for-runtime-platforms.md)