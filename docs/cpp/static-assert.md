---
title: static_assert
ms.date: 07/29/2019
f1_keywords:
- static_assert_cpp
helpviewer_keywords:
- assertions [C++], static_assert
- static_assert
ms.assetid: 28dd3668-e78c-4de8-ba68-552084743426
ms.openlocfilehash: b30af5fcf5d4f58143e657d84e743ef09a34e268
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742973"
---
# <a name="static_assert"></a>static_assert

Testuje potwierdzenie oprogramowania w czasie kompilacji. Jeśli określone wyrażenie stałe ma wartość **`false`** , kompilator Wyświetla określony komunikat, jeśli został podany, a kompilacja kończy się niepowodzeniem z powodu błędu C2338; w przeciwnym razie deklaracja nie ma wpływu.

## <a name="syntax"></a>Składnia

```
static_assert( constant-expression, string-literal );

static_assert( constant-expression ); // C++17 (Visual Studio 2017 and later)
```

### <a name="parameters"></a>Parametry

*wyrażenie stałe*\
Całkowite wyrażenie stałe, które można przekonwertować na wartość logiczną. Jeśli obliczone wyrażenie ma wartość zero (false), wyświetlany jest parametr *literału ciągu* , a kompilacja kończy się niepowodzeniem z powodu błędu. Jeśli wyrażenie ma wartość różną od zera (true), **`static_assert`** Deklaracja nie ma wpływu.

*literał ciągu*\
Komunikat, który jest wyświetlany, jeśli parametr *stałej Expression* ma wartość zero. Komunikat jest ciągiem znaków w [podstawowym zestawie znaków](../c-language/ascii-character-set.md) kompilatora; oznacza to, że nie są to [znaki wielobajtowe czy szerokie](../c-language/multibyte-and-wide-characters.md).

## <a name="remarks"></a>Uwagi

Parametr *wyrażenia stałej* **`static_assert`** deklaracji reprezentuje *potwierdzenie oprogramowania*. Potwierdzenie oprogramowania określa warunek, który powinien być prawdziwy w konkretnym punkcie w programie. Jeśli warunek ma wartość true, **`static_assert`** Deklaracja nie ma wpływu. Jeśli warunek ma wartość false, potwierdzenie kończy się niepowodzeniem, kompilator wyświetla komunikat w parametrze *literału ciągu* , a kompilacja kończy się niepowodzeniem z powodu błędu. W programie Visual Studio 2017 i nowszych parametr literału ciągu jest opcjonalny.

**`static_assert`** Deklaracja testuje potwierdzenie oprogramowania w czasie kompilacji. Z kolei, [makro Assert i _ASSERT i funkcje _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) testują potwierdzenie oprogramowania w czasie wykonywania i ponoszą koszt czasu wykonywania w przestrzeni lub czasie. **`static_assert`** Deklaracja jest szczególnie przydatna w przypadku debugowania szablonów, ponieważ argumenty szablonu mogą być zawarte w parametrze *wyrażenia stałej* .

Kompilator analizuje **`static_assert`** deklarację pod kątem błędów składniowych w przypadku napotkania deklaracji. Kompilator oblicza parametr *wyrażenia stałej* natychmiast, jeśli nie zależy od parametru szablonu. W przeciwnym razie kompilator oblicza parametr *wyrażenia stałego* podczas tworzenia wystąpienia szablonu. W związku z tym kompilator może wydać komunikat diagnostyczny po napotkaniu deklaracji i ponownie po utworzeniu wystąpienia szablonu.

Możesz użyć **`static_assert`** słowa kluczowego w przestrzeni nazw, klasie lub zakresie bloku. ( **`static_assert`** Słowo kluczowe jest technicznie deklaracją, mimo że nie wprowadza nowej nazwy do programu, ponieważ może być używane w zakresie przestrzeni nazw).

## <a name="description-of-static_assert-with-namespace-scope"></a>Opis static_assert z zakresem przestrzeni nazw

W poniższym przykładzie **`static_assert`** Deklaracja ma zakres przestrzeni nazw. Ponieważ kompilator wie o wielkości typu `void *` , wyrażenie jest oceniane natychmiast.

## <a name="example-of-static_assert-with-namespace-scope"></a>Przykład static_assert z zakresem przestrzeni nazw

```cpp
static_assert(sizeof(void *) == 4, "64-bit code generation is not supported.");
```

## <a name="description-of-static_assert-with-class-scope"></a>Opis static_assert z zakresem klasy

W poniższym przykładzie **`static_assert`** Deklaracja ma zakres klas. **`static_assert`** Sprawdza, czy parametr szablonu jest *zwykłym starym typem danych* (pod). Kompilator sprawdza **`static_assert`** deklarację, gdy jest zadeklarowany, ale nie ocenia parametru *stałego wyrażenia* do momentu `basic_string` wystąpienia szablonu klasy w `main()` .

## <a name="example-of-static_assert-with-class-scope"></a>Przykład static_assert z zakresem klasy

```cpp
#include <type_traits>
#include <iosfwd>
namespace std {
template <class CharT, class Traits = std::char_traits<CharT> >
class basic_string {
    static_assert(std::is_pod<CharT>::value,
                  "Template argument CharT must be a POD type in class template basic_string");
    // ...
    };
}

struct NonPOD {
    NonPOD(const NonPOD &) {}
    virtual ~NonPOD() {}
};

int main()
{
    std::basic_string<char> bs;
}
```

## <a name="description"></a>Opis

W poniższym przykładzie **`static_assert`** Deklaracja ma zakres bloku. **`static_assert`** Sprawdza, czy rozmiar struktury VMPage jest równy wartości PageSize pamięci wirtualnej.

## <a name="example"></a>Przykład

```cpp
#include <sys/param.h> // defines PAGESIZE
class VMMClient {
public:
    struct VMPage { // ...
           };
    int check_pagesize() {
    static_assert(sizeof(VMPage) == PAGESIZE,
        "Struct VMPage must be the same size as a system virtual memory page.");
    // ...
    }
// ...
};
```

## <a name="see-also"></a>Zobacz też

[Potwierdzanie i komunikaty dostarczone przez użytkownika (C++)](../cpp/assertion-and-user-supplied-messages-cpp.md)<br/>
[#error — dyrektywa (C/C++)](../preprocessor/hash-error-directive-c-cpp.md)<br/>
[potwierdzj makro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[Szablony](../cpp/templates-cpp.md)<br/>
[Zestaw znaków ASCII](../c-language/ascii-character-set.md)<br/>
[Deklaracje i definicje](declarations-and-definitions-cpp.md)
