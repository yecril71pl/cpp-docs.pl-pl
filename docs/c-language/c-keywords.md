---
title: Słowa kluczowe języka C
ms.date: 10/09/2018
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
ms.openlocfilehash: e1364e0edacd94efa4ade6c6892a57d619635a39
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326797"
---
# <a name="c-keywords"></a>Słowa kluczowe języka C

„Słowa kluczowe” to słowa, które mają specjalne znaczenie dla kompilatora C. W fazach translacji 7 i 8 identyfikator nie może mieć tej samej pisowni i wielkości liter co słowo kluczowe C. (Zobacz opis [fazy tłumaczenia](../preprocessor/phases-of-translation.md) w *Preprocessor Reference*; Aby uzyskać informacje dotyczące identyfikatorów, zobacz [identyfikatory](../c-language/c-identifiers.md).) Język C używa następujących słów kluczowych:

|||||
|-|-|-|-|
|**auto**|**double**|**int**|**struct**|
|**break**|**else**|**long**|**switch**|
|**case**|**enum**|**register**|**typedef**|
|**char**|**extern**|**return**|**Unia**|
|**const**|**float**|**short**|**Bez znaku**|
|**continue**|**for**|**Podpisany**|**void**|
|**default**|**goto**|**sizeof**|**volatile**|
|**do**|**if**|**static**|**while**|

Nie można przedefiniować słów kluczowych. Jednakże, można określić tekst do podstawienia pod słowa kluczowe przed kompilacją za pomocą języka C [dyrektywy preprocesora](../preprocessor/preprocessor-directives.md).

**Microsoft Specific**

Standard ANSI C umożliwia identyfikatorom z dwoma podkreśleniami wiodącymi rezerwację do implementacji kompilatora. Tym samym, konwencja Microsoft zakłada, że podwójne podkreślenie będzie poprzedzało charakterystyczne dla Microsoft słowa kluczowe. Tych słów nie można używać jako nazw identyfikatorów. Opis ANSI zasad nazewnictwa identyfikatorów, w tym użycie podwójnego podkreślenia w temacie [identyfikatory](../c-language/c-identifiers.md).

Poniższe słowa kluczowe i specjalne identyfikatory są rozpoznawane przez kompilator Microsoft C:

|||||
|-|-|-|-|
|**__asm**<sup>3</sup>|**dllimport**<sup>2</sup>|**__int8**<sup>3</sup>|**"naked"**<sup>2</sup>|
|**__based**<sup>1, 3</sup>|**__except**<sup>3</sup>|**__int16**<sup>3</sup>|**__stdcall**<sup>3</sup>|
|**__cdecl**<sup>3</sup>|**__fastcall**|**__int32**<sup>3</sup>|**Wątek**<sup>2</sup>|
|**__declspec**<sup>3</sup>|**__finally**<sup>3</sup>|**__int64**<sup>3</sup>|**__try**<sup>3</sup>|
|**dllexport**<sup>2</sup>|**__inline**<sup>3</sup>|**__leave**<sup>3</sup>||

<sup>1</sup> **__based** — słowo kluczowe ma ograniczone zastosowanie do 32-bitowych i 64-bitowych docelowej kompilacji.

<sup>2</sup> są to specjalne identyfikatory używane z **__declspec**; ich użycie w innych kontekstach nie jest ograniczona.

<sup>3</sup> zgodność z poprzednimi wersjami, te słowa kluczowe są dostępne zarówno z dwoma podkreśleniami wiodącymi i pojedynczego wiodącego podkreślnika po włączeniu rozszerzeń Microsoft.

Rozszerzenia Microsoft są domyślnie włączone. Aby upewnić się, że Twoje programy są w pełni zgodne, można wyłączyć rozszerzenia Microsoft określając [/Za \(Wyłącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md) opcji podczas kompilacji. Gdy to zrobisz, wyłączane są słowa kluczowe niektóre specyficzne dla firmy Microsoft.

Po włączeniu rozszerzeń Microsoft, możesz używać słów kluczowych wymienionych powyżej w swoich programach. W celu zachowania zgodności z ANSI, większość słów kluczowych jest poprzedzona podwójnym podkreśleniem. Cztery wyjątki **dllexport**, **dllimport**, **"naked"**, i **wątku**, są używane tylko z **__declspec** i w związku z tym nie wymagają wiodącego podwójnego podkreślenia. W celu zapewnienia zgodności z poprzednimi wersjami, wersje z pojedynczym podkreśleniem reszty słów kluczowych są obsługiwane.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Elementy języka C](../c-language/elements-of-c.md)
