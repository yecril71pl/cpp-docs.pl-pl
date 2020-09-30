---
title: '&lt;bit&gt;'
description: Funkcje umożliwiające dostęp, manipulowanie i przetwarzanie poszczególnych bitów i sekwencji bitów.
ms.date: 08/28/2020
f1_keywords:
- <bit>
helpviewer_keywords:
- bit header
ms.openlocfilehash: f9742ce1e15a817923c144544eb3bb6325e76765
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509953"
---
# <a name="ltbitgt"></a>&lt;bit&gt;

Definiuje funkcje do uzyskiwania dostępu, manipulowania i przetwarzania poszczególnych bitów i sekwencji bitów.

Na przykład znajdują się funkcje, które umożliwiają obracanie bitów, wyszukiwanie liczby kolejnych zestawów lub wyczyszczonych bitów, zobacz, czy liczba jest całkowitą potęgą dwóch, Znajdź najmniejszą liczbę bitów reprezentującą liczbę itd.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<bit>

**Przestrzeń nazw:** std

[/std: wymagany jest język c + +](../build/reference/std-specify-language-standard-version.md) .

## <a name="members"></a>Elementy członkowskie

### <a name="types"></a>Typy

| Typ | Opis |
|--------|----------|
| [endian](bit-enum.md) | Określa wartość endian typów skalarnych. |

### <a name="functions"></a>Funkcje

| Funkcja | Opis |
|-----|-----|
|[bit_cast](bit-functions.md#bit_cast) | Ponownie interpretuje reprezentację obiektu z jednego typu na inny. |
|[bit_ceil](bit-functions.md#bit_ceil) | Znajdź najmniejszą potęgę większą lub równą wartości. |
|[bit_floor](bit-functions.md#bit_floor) | Znajdź największą całkę, która nie jest większa od wartości. |
|[bit_width](bit-functions.md#bit_width) | Znajdź najmniejszą liczbę bitów, które są konieczne do reprezentowania wartości. |
|[countl_zero](bit-functions.md#countl_zero) | Zlicz liczbę kolejnych bitów ustawionych na zero, rozpoczynając od najbardziej znaczącego bitu. |
|[countl_one](bit-functions.md#countl_one) | Zlicz liczbę kolejnych bitów ustawionych na jeden, rozpoczynając od najbardziej znaczącego bitu. |
|[countr_zero](bit-functions.md#countr_zero) | Zlicz liczbę kolejnych bitów ustawionych na zero, rozpoczynając od najmniej znaczącego bitu. |
|[countr_one](bit-functions.md#countl_one) | Zlicz liczbę kolejnych bitów ustawionych na jeden, rozpoczynając od najmniej znaczącego bitu. |
|[has_single_bit](bit-functions.md#has_single_bit) | Sprawdź, czy wartość ma tylko jeden bit ustawiony jako jeden. Jest to takie samo, jak testowanie, czy wartość jest potęgą liczby 2. |
|[popcount](bit-functions.md#popcount) | Liczba bitów ustawionych na jeden. |
|[rotl](bit-functions.md#rotl) | Oblicza wynik dla bitowej lewej obrotu. |
|[rotr](bit-functions.md#rotr) | Oblicza wynik dwustopniowego obrotu. |

## <a name="see-also"></a>Zobacz też

[Dokumentacja plików nagłówkowych](cpp-standard-library-header-files.md)
