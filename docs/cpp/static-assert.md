---
title: static_assert | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- static_assert_cpp
dev_langs:
- C++
helpviewer_keywords:
- C++ keywords, static_assert
- C2338
- assertions [C++], static_assert
- static_assert
ms.assetid: 28dd3668-e78c-4de8-ba68-552084743426
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a3c3648f0b372df3c898c41197cba86e6ae9f894
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078494"
---
# <a name="staticassert"></a>static_assert

Testuje asercję oprogramowania w czasie kompilacji. Jeśli podane wyrażenie stałe ma wartość FALSE, kompilator Wyświetla określony komunikat, jeśli zostało ono określone, a kompilacja kończy się niepowodzeniem ze zgłoszeniem błędu C2338; w przeciwnym razie deklaracja nie ma znaczenia.

## <a name="syntax"></a>Składnia

```
static_assert( constant-expression, string-literal );

static_assert( constant-expression ); // Visual Studio 2017 and later
```

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*constant-expression*|Wyrażenie stałe liczby całkowitej, można przekonwertować na wartość logiczną.<br /><br /> Jeśli obliczane wyrażenie jest równa zero (false), *literał ciągu* parametru jest wyświetlany, a kompilacja kończy się niepowodzeniem z powodu błędu. Jeśli wyrażenie jest niezerowe (PRAWDA), **static_assert** deklaracja nie ma wpływu.|
|*literał ciągu*|Komunikat, który jest wyświetlany, gdy *wyrażenie_stałe* parametr ma wartość zero. Wiadomość to ciąg znaków w [podstawowy zestaw znaków](../c-language/ascii-character-set.md) z kompilatora; oznacza to, a nie [znaki wielobajtowe ani szerokie](../c-language/multibyte-and-wide-characters.md).|

## <a name="remarks"></a>Uwagi

*Wyrażenie_stałe* parametru **static_assert** reprezentuje deklaracji *asercję oprogramowania*. Potwierdzenie oprogramowania określa warunek, który będzie mieć wartość true w określonym punkcie w programie. Jeśli warunek jest spełniony, **static_assert** deklaracja nie ma wpływu. Jeśli warunek nie jest spełniony, potwierdzenie nie powiedzie się, kompilator wyświetla komunikat w *literał ciągu* parametr i kompilacja kończy się niepowodzeniem z powodu błędu. W programie Visual Studio 2017 i nowsze parametr literał ciągu jest opcjonalny.

**Static_assert** deklaracji testuje asercję oprogramowania w czasie kompilacji. Z kolei [assert — makro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) makro testuje asercję oprogramowania w czasie wykonywania i ponosi koszty wykonywania w przestrzeni lub w czasie. **Static_assert** deklaracja jest szczególnie przydatna podczas debugowania szablonów, ponieważ argumenty szablonu mogą być zawarte w *wyrażenie_stałe* parametru.

Kompilator sprawdza **static_assert** deklaracji pod kątem błędów składniowych po napotkaniu deklaracji. Kompilator ocenia *wyrażenie_stałe* parametr natychmiast, jeśli go nie zależy od parametru szablonu. W przeciwnym wypadku kompilator oblicza *wyrażenie_stałe* parametru podczas tworzenia wystąpienia szablonu. W związku z tym, kompilator może wydać komunikat diagnostyczny raz po napotkaniu deklaracji, a następnie ponownie podczas konkretyzacji szablonu.

Możesz użyć **static_assert** — słowo kluczowe w przestrzeni nazw, klasy lub zakresie bloku. ( **Static_assert** — słowo kluczowe jest technicznie deklaracją, mimo że nie wprowadza nowej nazwy do tego programu, ponieważ może służyć w zakresie przestrzeni nazw.)

## <a name="description"></a>Opis

W poniższym przykładzie **static_assert** deklaracji ma zakres przestrzeni nazw. Ponieważ kompilator zna wybrany rozmiar czcionki `void *`, wyrażenie jest oceniane natychmiast.

## <a name="example"></a>Przykład

```cpp
static_assert(sizeof(void *) == 4, "64-bit code generation is not supported.");
```

## <a name="description"></a>Opis

W poniższym przykładzie **static_assert** deklaracja ma zakres klasy. **Static_assert** sprawdza, czy parametr szablonu jest *zwykłe stare dane* typu (POD). Kompilator sprawdza **static_assert** deklaracji, gdy jest zadeklarowana, ale nie może oszacować *wyrażenie_stałe* parametru do momentu `basic_string` konkretyzacji szablonu klasy w `main()`.

## <a name="example"></a>Przykład

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

W poniższym przykładzie **static_assert** deklaracji ma zakres bloku. **Static_assert** sprawdza, czy rozmiar struktury VMPage jest równy pagesize pamięci wirtualnej systemu.

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

## <a name="see-also"></a>Zobacz także

[Potwierdzanie i komunikaty dostarczone przez użytkownika (C++)](../cpp/assertion-and-user-supplied-messages-cpp.md)<br/>
[#error, dyrektywa (C/C++)](../preprocessor/hash-error-directive-c-cpp.md)<br/>
[assert Macro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[Szablony](../cpp/templates-cpp.md)<br/>
[Zestaw znaków ASCII](../c-language/ascii-character-set.md)<br/>
[Deklaracje i definicje](declarations-and-definitions-cpp.md)