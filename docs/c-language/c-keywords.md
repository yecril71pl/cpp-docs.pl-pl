---
title: Słowa kluczowe języka C
description: Słowa kluczowe w standardowych rozszerzeniach kompilatora C i Microsoft C.
ms.date: 09/12/2020
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
ms.openlocfilehash: f459b81c2b3f314218108f3f367eec0c1bf17f26
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075741"
---
# <a name="c-keywords"></a>Słowa kluczowe języka C

*Słowa kluczowe* są słowami, które mają specjalne znaczenie w kompilatorze języka C. W fazach translacji 7 i 8 identyfikator nie może mieć takiej samej pisowni i wielkości liter jak słowo kluczowe języka C. Aby uzyskać więcej informacji, zobacz [etapy translacji](../preprocessor/phases-of-translation.md) w *odniesieniu do preprocesora*. Aby uzyskać więcej informacji na temat identyfikatorów, zobacz [identyfikatory](../c-language/c-identifiers.md).

## <a name="standard-c-keywords"></a>Standardowe słowa kluczowe języka C

Język C używa następujących słów kluczowych:

:::row:::
    :::column:::
        **`auto`**\
        **`break`**\
        **`case`**\
        **`char`**\
        **`const`**\
        **`continue`**\
        **`default`**\
        **`do`**\
        **`double`**\
        **`else`**\
        **`enum`**
    :::column-end:::
    :::column:::
        **`extern`**\
        **`float`**\
        **`for`**\
        **`goto`**\
        **`if`**\
        **`inline`**<sup>1, a</sup>\
        **`int`**\
        **`long`**\
        **`register`**\
        **`restrict`**<sup>1, a</sup>\
        **`return`**
    :::column-end:::
    :::column:::
        **`short`**\
        **`signed`**\
        **`sizeof`**\
        **`static`**\
        **`struct`**\
        **`switch`**\
        **`typedef`**\
        **`union`**\
        **`unsigned`**\
        **`void`**\
        **`volatile`**
    :::column-end:::
    :::column:::
        **`while`**\
        **`_Alignas`**<sup>2, a</sup>\
        **`_Alignof`**<sup>2, a</sup>\
        **`_Atomic`**<sup>2, b</sup>\
        **`_Bool`**<sup>1, a</sup>\
        **`_Complex`**<sup>1, b</sup>\
        **`_Generic`**<sup>2, a</sup>\
        **`_Imaginary`**<sup>1, b</sup>\
        **`_Noreturn`**<sup>2, a</sup>\
        **`_Static_assert`**<sup>2, a</sup>\
        **`_Thread_local`**<sup>2, b</sup>
    :::column-end:::
:::row-end:::

<sup>1</sup>  słowa kluczowe wprowadzone w pliku ISO C99.

<sup>2</sup>   słowa kluczowe wprowadzone w pliku ISO C11.

<sup>począwszy od programu Visual</sup>  Studio 2019 w wersji 16,8, te słowa kluczowe są obsługiwane w kodzie skompilowanym jako C w przypadku **`/std:c11`** **`/std:c17`** określenia opcji kompilatora lub.

<sup>b</sup>  począwszy od programu Visual Studio 2019 w wersji 16,8, te słowa kluczowe są rozpoznawane, ale nie są obsługiwane przez kompilator w kodzie skompilowanym jako C w przypadku **`/std:c11`** **`/std:c17`** określenia opcji kompilatora.

Nie można ponownie zdefiniować słów kluczowych. Można jednak określić tekst, aby zastąpić słowa kluczowe przed kompilacją przy użyciu [dyrektyw preprocesora](../preprocessor/preprocessor-directives.md)języka C.

## <a name="microsoft-specific-c-keywords"></a>Słowa kluczowe języka C specyficzne dla firmy Microsoft

Standardy ANSI i ISO C zezwalają na identyfikatory z dwoma wiodącymi podkreśleniami, które mają zostać zarezerwowane dla implementacji kompilatora. Konwencją firmy Microsoft jest powstawanie nazw słów kluczowych specyficznych dla firmy Microsoft z podwójnego podkreślenia. Tych słów nie można używać jako nazw identyfikatorów. Aby uzyskać opis reguł nazw identyfikatorów, w tym używania podwójnego podkreślenia, zobacz [identyfikatory](../c-language/c-identifiers.md).

Poniższe słowa kluczowe i specjalne identyfikatory są rozpoznawane przez kompilator Microsoft C:

:::row:::
    :::column:::
        **`__asm`**<sup>5000</sup>\
        **`dllimport`**<sup>czwart</sup>\
        **`__int8`**<sup>5000</sup>\
        **`naked`**<sup>czwart</sup>\
        **`__based`**<sup>3, 5</sup>
    :::column-end:::
    :::column:::
        **`__except`**<sup>5000</sup>\
        **`__int16`**<sup>5000</sup>\
        **`__stdcall`**<sup>5000</sup>\
        **`__cdecl`**<sup>5000</sup>\
        **`__fastcall`**
    :::column-end:::
    :::column:::
        **`__int32`**<sup>5000</sup>\
        **`thread`**<sup>czwart</sup>\
        **`__declspec`**<sup>5000</sup>\
        **`__finally`**<sup>5000</sup>\
        **`__int64`**<sup>5000</sup>
    :::column-end:::
    :::column:::
        **`__try`**<sup>5000</sup>\
        **`dllexport`**<sup>czwart</sup>\
        **`__inline`**<sup>5000</sup>\
        **`__leave`**<sup>5000</sup>
    :::column-end:::
:::row-end:::

<sup>3</sup> **`__based`** słowo kluczowe ma ograniczone zastosowania do 32-bitowych i 64-bitowych kompilacji docelowych.

<sup>4</sup> są to specjalne identyfikatory, które są używane z **`__declspec`** ; ich użycie w innych kontekstach jest nieograniczone.

<sup>5</sup> aby zapewnić zgodność z poprzednimi wersjami, te słowa kluczowe są dostępne zarówno z dwoma wiodącymi podkreśleniami, jak i z pojedynczym znakiem wiodącym po włączeniu rozszerzeń firmy Microsoft.

Rozszerzenia Microsoft są domyślnie włączone. Aby pomóc w tworzeniu kodu przenośnego, można wyłączyć rozszerzenia Microsoft przez określenie opcji [/za \( disable Language Extensions (wyłączając)](../build/reference/za-ze-disable-language-extensions.md) w trakcie kompilacji. W przypadku korzystania z tej opcji niektóre słowa kluczowe specyficzne dla firmy Microsoft są wyłączone.

Po włączeniu rozszerzeń Microsoft, możesz używać słów kluczowych wymienionych powyżej w swoich programach. W przypadku zgodności ze standardami większość tych słów kluczowych jest poprzedzona podwójnym podkreśleniem. Cztery wyjątki, **`dllexport`** ,, **`dllimport`** **`naked`** i **`thread`** , są używane tylko z **`__declspec`** i nie wymagają wiodącego podwójnego podkreślenia. W celu zapewnienia zgodności z poprzednimi wersjami, wersje z pojedynczym podkreśleniem reszty słów kluczowych są obsługiwane.

## <a name="see-also"></a>Zobacz także

[Elementy języka C](../c-language/elements-of-c.md)
