---
title: Modyfikatory specyficzne dla firmy Microsoft
ms.date: 08/16/2018
ms.assetid: 22c7178c-f854-47fa-9de6-07d23fda58e1
ms.openlocfilehash: 2f56220ba15027a522264b91366cab9cf0b65d21
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506538"
---
# <a name="microsoft-specific-modifiers"></a>Modyfikatory specyficzne dla firmy Microsoft

W tej sekcji opisano rozszerzenia specyficzne dla firmy Microsoft do języka C++ w następujących obszarach:

- [Adresowanie na podstawie](based-addressing.md), praktyczne użycie wskaźnika jako podstawy, z którego mogą być przesunięte inne wskaźniki

- [Konwencje wywoływania funkcji](calling-conventions.md)

- Rozszerzone atrybuty klasy magazynu zadeklarowane za pomocą słowa kluczowego [__declspec](declspec.md)

- Słowo kluczowe [__w64](w64.md)

## <a name="microsoft-specific-keywords"></a>Słowa kluczowe specyficzne dla firmy Microsoft

Wiele słów kluczowych specyficznych dla firmy Microsoft może służyć do modyfikowania Deklaratory do tworzenia typów pochodnych. Aby uzyskać więcej informacji na temat deklaratory, zobacz [Deklaratory](./declarations-and-definitions-cpp.md).

|Słowo kluczowe|Znaczenie|Służy do tworzenia typów pochodnych?|
|-------------|-------------|---------------------------------|
|[__based](based-grammar.md)|Nazwa, która następuje, deklaruje przesunięcie 32-bitowe do 32-bitowej bazy zawartej w deklaracji.|Tak|
|[__cdecl](cdecl.md)|Nazwa, która posługuje się z konwencją nazewnictwa języka C i konwencjami wywoływania.|Tak|
|[__declspec](declspec.md)|Następująca nazwa określa atrybut klasy magazynu specyficzny dla firmy Microsoft.|Nie|
|[__fastcall](fastcall.md)|Następująca nazwa deklaruje funkcję, która używa rejestrów, gdy jest dostępna, zamiast stosu do przekazywania argumentu.|Tak|
|[__restrict](extension-restrict.md)|Podobne do __declspec ([Ogranicz](restrict.md)), ale do użycia w zmiennych.|Nie|
|[__stdcall](stdcall.md)|Następująca nazwa określa funkcję, która przestrzega standardowej konwencji wywoływania.|Tak|
|[__w64](w64.md)|Oznacza typ danych jako większy dla kompilatora 64-bitowego.|Nie|
|[__unaligned](unaligned.md)|Określa, że wskaźnik do typu lub innych danych nie jest wyrównany.|Nie|
|[__vectorcall](vectorcall.md)|Następująca nazwa deklaruje funkcję, która używa rejestrów, w tym rejestrów SSE, jeśli są dostępne, zamiast stosu do przekazywania argumentu.|Tak|

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka C++](cpp-language-reference.md)
