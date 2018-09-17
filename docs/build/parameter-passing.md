---
title: Przekazywanie parametru | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e838ee5f-c2fe-40b0-9a23-8023c949c820
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8db6b61936b2122cd984e594c1ff3f162fa3dfe
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724454"
---
# <a name="parameter-passing"></a>Przekazywanie parametru

Pierwsze cztery liczby całkowitej argumenty są przekazywane w rejestrach. Wartości całkowite są przekazywane (w kolejności od lewej do prawej) w RCX, RDX, R8 i R9. Od pięciu argumentów i nowszej są przekazywane na stosie. Wszystkie argumenty są wyrównane do prawej w rejestrach. Jest to zrobić, aby obiekt wywoływany można zignorować górny bitów rejestru, jeśli muszą być i może uzyskać dostęp tylko część niezbędne rejestru.

Argumenty zmiennoprzecinkowe i podwójnej precyzji są przekazywane w XMM0 — XMM3 (maksymalnie 4) z gniazdem liczby całkowitej (RCX, RDX, R8 i R9), która jest zwykle używane dla tego gniazda kardynalnej są ignorowane (Zobacz przykład) i na odwrót.

[__m128](../cpp/m128.md) typów, tablic i ciągi nigdy nie są przekazywane przez natychmiastowe korzyści, ale raczej wskaźnik jest przekazywany do pamięci przydzielonej przez obiekt wywołujący. Struktury/Unii, rozmiar, 8, 16, 32 lub 64 bitów i __m64 są przekazywane tak, jakby były one liczb całkowitych w tej samej wielkości. Struktury/Unii, inne niż te rozmiary są przekazywane jako wskaźnik do pamięci przydzielonej przez obiekt wywołujący. Dla tych typów agregacji przekazywane jako wskaźnika (w tym \__m128), tymczasowego pamięci przydzielonej przez obiekt wywołujący będzie wyrównane do 16-bajtowy.

Funkcje wewnętrzne, które nie przydzielenie miejsca na stosie i nie należy wywoływać innych funkcji można użyć innych rejestrów volatile Aby przekazać argumenty dodatkowe rejestrowanie, ponieważ ścisłej powiązania między kompilator i implementację funkcji wewnętrznej. Jest to dodatkowe możliwości dla poprawy wydajności.

Obiekt wywoływany ma obowiązek zrzucanie Parametry rejestru do ich miejsca w tle, jeśli to konieczne.

W poniższej tabeli przedstawiono, jak parametry są przekazywane:

|Typ parametru|Jak przekazany|
|--------------------|----------------|
|Liczba zmiennoprzecinkowa|Pierwsze 4 parametry - XMM0 za pośrednictwem XMM3. Inne są przekazywane na stosie.|
|Liczba całkowita|Pierwsze 4 parametry — RCX, RDX, R8, R9. Inne są przekazywane na stosie.|
|Agregacje (8, 16, 32 lub 64-bitowy) i __m64|Pierwsze 4 parametry — RCX, RDX, R8, R9. Inne są przekazywane na stosie.|
|Agregacje (inne)|Przez wskaźnik. Pierwsze 4 parametry są przekazywane jako wskaźniki w RCX, RDX, R8 i R9|
|__m128|Przez wskaźnik. Pierwsze 4 parametry są przekazywane jako wskaźniki w RCX, RDX, R8 i R9|

## <a name="example-of-argument-passing-1---all-integers"></a>Przykład 1 - wszystkich liczb całkowitych przekazywanie argumentów

```
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

## <a name="example-of-argument-passing-2---all-floats"></a>Przykład 2 — wszystkie wartości zmiennoprzecinkowe przekazywanie argumentów

```
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

## <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Przykład 3 - mieszane liczby całkowite i wartości zmiennoprzecinkowe przekazywanie argumentów

```
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

## <a name="example-of-argument-passing-4--m64-m128-and-aggregates"></a>Przykład 4 przekazywania argumentu-__m64, \__m128, a agregacje

```
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="see-also"></a>Zobacz też

[Konwencja wywoływania](../build/calling-convention.md)