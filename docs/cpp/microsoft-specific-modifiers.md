---
title: Modyfikatory specyficzne dla firmy Microsoft
ms.date: 08/16/2018
ms.assetid: 22c7178c-f854-47fa-9de6-07d23fda58e1
ms.openlocfilehash: 2d65c0fe99895949d537ccf4368df2add3ff91ad
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857427"
---
# <a name="microsoft-specific-modifiers"></a>Modyfikatory specyficzne dla firmy Microsoft

Ten rozdział opisuje specyficzne dla Microsoft rozszerzenia do C++ w następujących obszarach:

- [Adresowanie na podstawie](based-addressing.md), praktyczne użycie wskaźnika jako podstawy, z którego mogą być przesunięte inne wskaźniki

- [Konwencje wywoływania funkcji](calling-conventions.md)

- Rozszerzone atrybuty klasy magazynu zadeklarowane za pomocą słowa kluczowego [__declspec](declspec.md)

- Słowo kluczowe [__w64](w64.md)

## <a name="microsoft-specific-keywords"></a>słowa kluczowe specyficzne dla firmy Microsoft

Wiele słów kluczowych specyficznych dla firmy Microsoft może służyć do modyfikowania deklaratorów w celu tworzenia typów pochodnych. Aby uzyskać więcej informacji na temat deklaratory, zobacz [Deklaratory](overview-of-declarators.md).

|Słowo kluczowe|Znaczenie|Używany do tworzenia typów pochodnych?|
|-------------|-------------|---------------------------------|
|[__based](based-grammar.md)|Widoczna dalej nazwa deklaruje 32-bitowe przesunięcie w stosunku do zawartej w zgłoszeniu podstawy 32-bitowej.|Tak|
|[__cdecl](cdecl.md)|Widoczna dalej nazwa używa konwencji wywoływania i nazewnictwa języka C.|Tak|
|[__declspec](declspec.md)|Widoczna dalej nazwa określa atrybut klasy magazynu specyficzny dla firmy Microsoft.|Nie|
|[__fastcall](fastcall.md)|Widoczna dalej nazwa deklaruje funkcję, która używa rejestrów, jeśli są dostępne, zamiast stosu do przekazywania argumentu.|Tak|
|[__restrict](extension-restrict.md)|Podobne do __declspec ([Ogranicz](restrict.md)), ale do użycia w zmiennych.|Nie|
|[__stdcall](stdcall.md)|Widoczna dalej nazwa określa funkcję, która przestrzega standardowej konwencji wywoływania.|Tak|
|[__w64](w64.md)|Oznacza typ danych jako większe na 64-bitowym kompilatorze.|Nie|
|[__unaligned](unaligned.md)|Określa, że wskaźnik do typu lub innych danych nie jest wyrównany...|Nie|
|[__vectorcall](vectorcall.md)|Widoczna dalej nazwa deklaruje funkcję, która używa rejestrów, włącznie z rejestrami SSE, jeśli są dostępne, zamiast stosu do przekazywania argumentu.|Tak|

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](cpp-language-reference.md)
