---
title: Słowa kluczowe języka C
ms.date: 10/09/2018
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
ms.openlocfilehash: 081235f987d3f6f8dbfd3abb4af9d70688b7fd98
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87200715"
---
# <a name="c-keywords"></a>Słowa kluczowe języka C

„Słowa kluczowe” to słowa, które mają specjalne znaczenie dla kompilatora C. W fazach translacji 7 i 8 identyfikator nie może mieć tej samej pisowni i wielkości liter co słowo kluczowe C. (Zobacz Opis [faz tłumaczenia](../preprocessor/phases-of-translation.md) w *odniesieniu do preprocesora*; Aby uzyskać informacje na temat identyfikatorów, zobacz [identyfikatory](../c-language/c-identifiers.md)). Język C używa następujących słów kluczowych:

:::row:::
    :::column:::
        **`auto`**<br/>
        **`double`**<br/>
        **`int`**<br/>
        **`struct`**<br/>
        **`break`**<br/>
        **`else`**<br/>
        **`long`**<br/>
        **`switch`**<br/>
    :::column-end:::
    :::column:::
        **`case`**<br/>
        **`enum`**<br/>
        **`register`**<br/>
        **`typedef`**<br/>
        **`char`**<br/>
        **`extern`**<br/>
        **`return`**<br/>
        **`union`**<br/>
    :::column-end:::
    :::column:::
        **`const`**<br/>
        **`float`**<br/>
        **`short`**<br/>
        **`unsigned`**<br/>
        **`continue`**<br/>
        **`for`**<br/>
        **`signed`**<br/>
        **`void`**<br/>
    :::column-end:::
    :::column:::
        **`default`**<br/>
        **`goto`**<br/>
        **`sizeof`**<br/>
        **`volatile`**<br/>
        **`do`**<br/>
        **`if`**<br/>
        **`static`**<br/>
        **`while`**<br/>
    :::column-end:::
:::row-end:::

Nie można ponownie zdefiniować słów kluczowych. Można jednak określić tekst, który ma zostać zastąpiony słowami kluczowymi przed kompilacją przy użyciu [dyrektyw preprocesora](../preprocessor/preprocessor-directives.md)języka C.

**Specyficzne dla firmy Microsoft**

Standard ANSI C umożliwia identyfikatorom z dwoma podkreśleniami wiodącymi rezerwację do implementacji kompilatora. Tym samym, konwencja Microsoft zakłada, że podwójne podkreślenie będzie poprzedzało charakterystyczne dla Microsoft słowa kluczowe. Tych słów nie można używać jako nazw identyfikatorów. Aby uzyskać opis reguł ANSI dotyczących identyfikatorów nazw, w tym używania podwójnego podkreślenia, zobacz [identyfikatory](../c-language/c-identifiers.md).

Poniższe słowa kluczowe i specjalne identyfikatory są rozpoznawane przez kompilator Microsoft C:

:::row:::
    :::column:::
        **`__asm`**<sup>r.3</sup><br/>
        **`dllimport`**<sup>dwóch</sup><br/>
        **`__int8`**<sup>r.3</sup><br/>
        **`naked`**<sup>dwóch</sup><br/>
        **`__based`**<sup>1, 3</sup><br/>
    :::column-end:::
    :::column:::
        **`__except`**<sup>r.3</sup><br/>
        **`__int16`**<sup>r.3</sup><br/>
        **`__stdcall`**<sup>r.3</sup><br/>
        **`__cdecl`**<sup>r.3</sup><br/>
        **`__fastcall`**<br/>
    :::column-end:::
    :::column:::
        **`__int32`**<sup>r.3</sup><br/>
        **`thread`**<sup>dwóch</sup><br/>
        **`__declspec`**<sup>r.3</sup><br/>
        **`__finally`**<sup>r.3</sup><br/>
        **`__int64`**<sup>r.3</sup><br/>
    :::column-end:::
    :::column:::
        **`__try`**<sup>r.3</sup><br/>
        **`dllexport`**<sup>dwóch</sup><br/>
        **`__inline`**<sup>r.3</sup><br/>
        **`__leave`**<sup>r.3</sup><br/>
    :::column-end:::
:::row-end:::

<sup>1</sup> **`__based`** słowo kluczowe ma ograniczone zastosowania do 32-bitowych i 64-bitowych kompilacji elementów docelowych.

<sup>2</sup> są to specjalne identyfikatory, które są używane z **`__declspec`** ; ich użycie w innych kontekstach nie jest ograniczone.

<sup>3</sup> aby zapewnić zgodność z poprzednimi wersjami, te słowa kluczowe są dostępne zarówno z dwoma wiodącymi podkreśleniami, jak i pojedynczym podkreśleniem wiodącym, gdy rozszerzenia Microsoft są włączone.

Rozszerzenia Microsoft są domyślnie włączone. Aby upewnić się, że programy są w pełni przenośne, możesz wyłączyć rozszerzenia Microsoft, określając opcję [/za \( disable Language Extensions](../build/reference/za-ze-disable-language-extensions.md) (Opcje) podczas kompilacji. Po wykonaniu tej czynności niektóre słowa kluczowe specyficzne dla firmy Microsoft są wyłączone.

Po włączeniu rozszerzeń Microsoft, możesz używać słów kluczowych wymienionych powyżej w swoich programach. W celu zachowania zgodności z ANSI, większość słów kluczowych jest poprzedzona podwójnym podkreśleniem. Cztery wyjątki, **`dllexport`** ,, **`dllimport`** **`naked`** i **`thread`** , są używane tylko z **`__declspec`** i dlatego nie wymagają wiodącego podwójnego podkreślenia. W celu zapewnienia zgodności z poprzednimi wersjami, wersje z pojedynczym podkreśleniem reszty słów kluczowych są obsługiwane.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Elementy języka C](../c-language/elements-of-c.md)
