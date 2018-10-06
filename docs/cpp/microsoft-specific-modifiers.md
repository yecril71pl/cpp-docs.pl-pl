---
title: Modyfikatory specyficzne dla firmy Microsoft | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/16/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 22c7178c-f854-47fa-9de6-07d23fda58e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b845ccb24d6d7a93767ec3c3219562c1c87bf81f
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820249"
---
# <a name="microsoft-specific-modifiers"></a>Modyfikatory specyficzne dla firmy Microsoft

Ten rozdział opisuje specyficzne dla Microsoft rozszerzenia do C++ w następujących obszarach:

- [Adresowanie na podstawie](based-addressing.md), praktyka używana wskaźnik jako podstawowy, z którego mogą być rekompensowane inne wskaźniki

- [Konwencje wywoływania funkcji](calling-conventions.md)

- Rozszerzone atrybuty klasy magazynowania zadeklarowane za pomocą [__declspec](declspec.md) — słowo kluczowe

- [__W64](w64.md) — słowo kluczowe

## <a name="microsoft-specific-keywords"></a>Słowa kluczowe specyficzne dla firmy Microsoft

Wiele słów kluczowych specyficznych dla firmy Microsoft może służyć do modyfikowania deklaratorów w celu tworzenia typów pochodnych. Aby uzyskać więcej informacji dotyczących deklaratorów, zobacz [deklaratory](overview-of-declarators.md).

|Słowo kluczowe|Znaczenie|Używany do tworzenia typów pochodnych?|
|-------------|-------------|---------------------------------|
|[__based](based-grammar.md)|Widoczna dalej nazwa deklaruje 32-bitowego przesunięcia zawartej w zgłoszeniu podstawy 32-bitowych.|Tak|
|[__cdecl](cdecl.md)|Widoczna dalej nazwa używa nazewnictwo C i Konwencje wywoływania.|Tak|
|[__declspec](declspec.md)|Widoczna dalej nazwa Określa atrybut klasy magazynu specyficzne dla firmy Microsoft.|Nie|
|[__fastcall](fastcall.md)|Widoczna dalej nazwa deklaruje funkcję, która używa rejestrów, jeśli są dostępne, zamiast stosu do przekazywania argumentu.|Tak|
|[__restrict](extension-restrict.md)|Podobnie jak __declspec ([ograniczyć](restrict.md)), ale do wykorzystania dla zmiennych.|Nie|
|[__stdcall](stdcall.md)|Widoczna dalej nazwa określa funkcję, która przestrzega standardowej konwencji wywoływania.|Tak|
|[__w64](w64.md)|Oznacza typ danych jako większe na 64-bitowego kompilatora.|Nie|
|[__unaligned](unaligned.md)|Określa, czy wskaźnik do typu lub innych danych nie jest wyrównany...|Nie|
|[__vectorcall](vectorcall.md)|Widoczna dalej nazwa deklaruje funkcję, która używa rejestrów, włącznie z rejestrami SSE, jeśli są dostępne, zamiast stosu do przekazywania argumentu.|Tak|

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka C++](cpp-language-reference.md)