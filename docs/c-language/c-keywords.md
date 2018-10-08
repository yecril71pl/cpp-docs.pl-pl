---
title: Słowa kluczowe języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 80c1f0d4ac5d843732771281202612e31a4073c2
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860891"
---
# <a name="c-keywords"></a>Słowa kluczowe języka C

„Słowa kluczowe” to słowa, które mają specjalne znaczenie dla kompilatora C. W fazach translacji 7 i 8 identyfikator nie może mieć tej samej pisowni i wielkości liter co słowo kluczowe C. (Zobacz opis [fazy tłumaczenia](../preprocessor/phases-of-translation.md) w *Preprocessor Reference*; Aby uzyskać informacje dotyczące identyfikatorów, zobacz [identyfikatory](../c-language/c-identifiers.md).) Język C używa następujących słów kluczowych:

|||||
|-|-|-|-|
|**auto**|**double**|**int**|**struct**|
|**break**|**else**|**long**|**switch**|
|**przypadek**|**enum**|**register**|**Element TypeDef**|
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
|**__asm**|**DllImport**<sup>2</sup>|**__int8**|**"naked"**<sup>2</sup>|
|**__based**<sup>1</sup>|**__except**|**__int16**|**__stdcall**|
|**__cdecl**|**__fastcall**|**__int32**|**Wątek**<sup>2</sup>|
|**__declspec**|**__finally**|**__int64**|**__try**|
|**dllexport**<sup>2</sup>|**__inline**|**__leave**||

<sup>1</sup> **__based** — słowo kluczowe ma ograniczone zastosowanie do 32-bitowych i 64-bitowych docelowej kompilacji.

<sup>2</sup> są to specjalne identyfikatory używane z **__declspec**; ich użycie w innych kontekstach nie jest ograniczona.

Rozszerzenia Microsoft są domyślnie włączone. Aby upewnić się, że Twoje programy są w pełni zgodne, możesz wyłączyć rozszerzenia Microsoft określając opcję wiersza polecenia /Za (kompiluj dla zgodności ANSI) podczas kompilacji. Gdy to zrobisz, wyłączane są słowa kluczowe specyficzne dla firmy Microsoft.

Po włączeniu rozszerzeń Microsoft, możesz używać słów kluczowych wymienionych powyżej w swoich programach. W celu zachowania zgodności z ANSI, większość słów kluczowych jest poprzedzona podwójnym podkreśleniem. Cztery wyjątki **dllexport**, **dllimport**, **"naked"**, i **wątku**, są używane tylko z **__declspec** i w związku z tym nie wymagają wiodącego podwójnego podkreślenia. W celu zapewnienia zgodności z poprzednimi wersjami, wersje z pojedynczym podkreśleniem reszty słów kluczowych są obsługiwane.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Elementy języka C](../c-language/elements-of-c.md)
