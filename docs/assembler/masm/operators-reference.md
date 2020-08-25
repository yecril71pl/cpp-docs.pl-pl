---
title: Odwołania do operatorów MASM
ms.date: 07/15/2020
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), operators reference
- operators [MASM]
ms.assetid: c069cab7-d6b0-4f82-a6ce-0ca3fc7e6428
ms.openlocfilehash: db79473f5d4264b869eeac334fa7957cfe553364
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88830946"
---
# <a name="masm-operators-reference"></a>Odwołania do operatorów MASM

## <a name="arithmetic"></a>Arytmetyczny

:::row:::
   :::column span="":::
      [`*` mnożenia](operator-multiply.md)\
      [`+` dodana](operator-add.md)\
      [`-` (Odejmij lub Negate)](operator-subtract-2.md)
   :::column-end:::
   :::column span="":::
      [`.` polami](operator-dot.md)\
      [`/` mieszczon](operator-subtract-1.md)
   :::column-end:::
   :::column span="":::
      [`[]` indeks](operator-brackets.md)\
      [`MOD` pozostałej części](operator-mod.md)
   :::column-end:::
:::row-end:::

## <a name="control-flow"></a>Przepływ sterowania

:::row:::
   :::column span="":::
      [`!` (nie ma logicznego środowiska uruchomieniowego)](operator-logical-not-masm-run-time.md)\
      [`!=` (nierówne środowisko uruchomieniowe)](operator-not-equal-masm.md)\
      [`||` (logiczne środowisko uruchomieniowe lub)](operator-logical-or.md)\
      [`&&` (logiczne środowisko uruchomieniowe i)](operator-logical-and-masm-run-time.md)\
      [`<` (środowisko uruchomieniowe mniejsze niż)](operator-less-than-masm-run-time.md)
   :::column-end:::
   :::column span="":::
      [`<=` (mniejsze lub równe środowisko uruchomieniowe)](operator-less-or-equal-masm-run-time.md)\
      [`==` (równe środowisko uruchomieniowe)](operator-equal-masm-run-time.md)\
      [`>` (środowisko uruchomieniowe większe niż)](operator-greater-than-masm-run-time.md)\
      [`>=` (środowisko uruchomieniowe jest większe lub równe)](operator-greater-or-equal-masm-run-time.md)\
      [`&` (bitowe środowisko uruchomieniowe i)](operator-bitwise-and.md)
   :::column-end:::
   :::column span="":::
      [`CARRY?` (test przenoszenia przez środowisko uruchomieniowe)](operator-carry-q.md)\
      [`OVERFLOW?` (test przepełnienia środowiska uruchomieniowego)](operator-overflow-q.md)\
      [`PARITY?` (test parzystości środowiska uruchomieniowego)](operator-parity-q.md)\
      [`SIGN?` (test znaku w czasie wykonywania)](operator-sign-q.md)\
      [`ZERO?` (Test zerowy czasu wykonania)](operator-zero-q.md)
   :::column-end:::
:::row-end:::

## <a name="logical-and-shift"></a>Koniunkcja logiczna i Shift

:::row:::
   :::column span="":::
      [`AND` (bitowe i)](operator-and.md)\
      [`NOT` (nie bitowe)](operator-not.md)
   :::column-end:::
   :::column span="":::
      [`OR` (bitowe lub)](operator-or.md)\
      [`SHL` (po lewej stronie bity Shift)](operator-shl.md)
   :::column-end:::
   :::column span="":::
      [`SHR` (prawy klawisz Shift)](operator-shr.md)\
      [`XOR` (bitowe wykluczające lub)](operator-xor.md)
   :::column-end:::
:::row-end:::

## <a name="macro"></a>Makro

:::row:::
   :::column span="":::
      [`!` (literał znakowy)](operator-logical-not-masm.md)\
      [`%` (Traktuj jako tekst)](operator-percent.md)
   :::column-end:::
   :::column span="":::
      [`;;` (Traktuj jako komentarz)](operator-semicolons.md)\
      [`< >` (Traktuj jako jeden literał)](operator-literal.md)
   :::column-end:::
   :::column span="":::
      [`& &` (Zastąp wartość parametru)](operator-logical-and-masm.md)
   :::column-end:::
:::row-end:::

## <a name="miscellaneous"></a>Różne

:::row:::
   :::column span="":::
      [`' '` (Traktuj jako ciąg)](operator-single-quote.md)\
      [`" "` (Traktuj jako ciąg)](operator-double-quote.md)\
      `:` (definicja etykiety lokalnej)
   :::column-end:::
   :::column span="":::
      `::` (Rejestruj segment i przesunięcie) \
      `::` (definicja etykiety globalnej)
   :::column-end:::
   :::column span="":::
      [`;` (Traktuj jako komentarz)](operator-semicolon.md)\
      [`DUP` (powtarzanie deklaracji)](operator-dup.md)
   :::column-end:::
:::row-end:::

## <a name="record"></a>Rekord

:::row:::
   :::column span="":::
      [`MASK` (Pobierz maskę rekordu lub pola)](operator-mask.md)
   :::column-end:::
   :::column span="2":::
      [`WIDTH` (Pobierz rekord lub szerokość pola)](operator-width.md)
   :::column-end:::
:::row-end:::

## <a name="relational"></a>Relacyjne

:::row:::
   :::column span="":::
      [`EQ` większy](operator-eq.md)\
      [`GE` (większe lub równe)](operator-ge.md)
   :::column-end:::
   :::column span="":::
      [`GT` (większe niż)](operator-gt.md)\
      [`LE` (mniejsze lub równe)](operator-le.md)
   :::column-end:::
   :::column span="":::
      [`LT` (mniejsze niż)](operator-lt.md)\
      [`NE` (nie równa się)](operator-ne.md)
   :::column-end:::
:::row-end:::

## <a name="segment"></a>Segment

:::row:::
   :::column span="":::
      [`:` (przesłonięcie segmentu)](operator-colon.md)\
      `::` (Rejestruj segment i przesunięcie) \
      [`IMAGEREL` (względne względem obrazu)](operator-imagerel.md)
   :::column-end:::
   :::column span="":::
      [`LROFFSET` (rozwiązane przesunięcia modułu ładującego)](operator-lroffset.md)\
      [`OFFSET` (przesunięcie względne segmentu)](operator-offset.md)
   :::column-end:::
   :::column span="":::
      [`SECTIONREL` (względne przesunięcie sekcji)](operator-sectionrel.md)\
      [`SEG` (Pobierz segment)](operator-seg.md)
   :::column-end:::
:::row-end:::

## <a name="type"></a>Typ

:::row:::
   :::column span="":::
      [`HIGH` (wysoko 8 bitów z najniższych 16 bitów)](operator-high.md)\
      [`HIGH32` (wysoka 32 bitów z 64 bitów)](operator-high32.md)\
      [`HIGHWORD` (duża liczba 16 bitów z najniższych 32 bitów)](operator-highword.md)\
      [`LENGTH` (liczba elementów w tablicy)](operator-length.md)\
      [`LENGTHOF` (liczba elementów w tablicy)](operator-lengthof.md)\
      [`LOW` (niski 8 bitów)](operator-low.md)
   :::column-end:::
   :::column span="":::
      [`LOW32` (niska 32 bitów)](operator-low32.md)\
      [`LOWWORD` (małe 16 bitów)](operator-lowword.md)\
      [`OPATTR` (Pobierz informacje o typie argumentu)](operator-opattr.md)\
      [`PTR` (wskaźnik do lub jako typ)](operator-ptr.md)\
      [`SHORT` (Oznacz typ krótkiej etykiety)](operator-short.md)
   :::column-end:::
   :::column span="":::
      [`SIZE` (rozmiar typu lub zmiennej)](operator-size.md)\
      [`SIZEOF` (rozmiar typu lub zmiennej)](operator-sizeof.md)\
      [`THIS` (bieżąca lokalizacja)](operator-this.md)\
      [`TYPE` (Pobierz typ wyrażenia)](operator-type.md)\
      [`.TYPE` (Pobierz informacje o typie argumentu)](operator-dot-type.md)
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>Zobacz też

[Dokumentacja asemblera programu Microsoft Macro](microsoft-macro-assembler-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
