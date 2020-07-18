---
title: Odwołania do operatorów MASM
ms.date: 07/15/2020
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), operators reference
- operators [MASM]
ms.assetid: c069cab7-d6b0-4f82-a6ce-0ca3fc7e6428
ms.openlocfilehash: c29b173a1dcf29c297e41f136044599fbd5218a5
ms.sourcegitcommit: e15b46ea7888dbdd7e0bb47da76aeed680c3c1f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2020
ms.locfileid: "86446466"
---
# <a name="masm-operators-reference"></a>Odwołania do operatorów MASM

## <a name="arithmetic"></a>Arytmetyczny

:::row:::
   :::column span="":::
      [`*`mnożenia](operator-multiply.md)<br/>[`+`dodana](operator-add.md)<br/>[`-`(Odejmij lub Negate)](operator-subtract-2.md)
   :::column-end:::
   :::column span="":::
      [`.`polami](operator-dot.md)<br/>[`/`mieszczon](operator-subtract-1.md)
   :::column-end:::
   :::column span="":::
      [`[]`indeks](operator-brackets.md)<br/>[`MOD`pozostałej części](operator-mod.md)
   :::column-end:::
:::row-end:::

## <a name="control-flow"></a>Przepływ sterowania

:::row:::
   :::column span="":::
      [`!`(nie ma logicznego środowiska uruchomieniowego)](operator-logical-not-masm-run-time.md)<br/>[`!=`(nierówne środowisko uruchomieniowe)](operator-not-equal-masm.md)<br/>[`||`(logiczne środowisko uruchomieniowe lub)](operator-logical-or.md)<br/>[`&&`(logiczne środowisko uruchomieniowe i)](operator-logical-and-masm-run-time.md)<br/>[`<`(środowisko uruchomieniowe mniejsze niż)](operator-less-than-masm-run-time.md)
   :::column-end:::
   :::column span="":::
      [`<=`(mniejsze lub równe środowisko uruchomieniowe)](operator-less-or-equal-masm-run-time.md)<br/>[`==`(równe środowisko uruchomieniowe)](operator-equal-masm-run-time.md)<br/>[`>`(środowisko uruchomieniowe większe niż)](operator-greater-than-masm-run-time.md)<br/>[`>=`(środowisko uruchomieniowe jest większe lub równe)](operator-greater-or-equal-masm-run-time.md)<br/>[`&`(bitowe środowisko uruchomieniowe i)](operator-bitwise-and.md)
   :::column-end:::
   :::column span="":::
      [`CARRY?`(test przenoszenia przez środowisko uruchomieniowe)](operator-carry-q.md)<br/>[`OVERFLOW?`(test przepełnienia środowiska uruchomieniowego)](operator-overflow-q.md)<br/>[`PARITY?`(test parzystości środowiska uruchomieniowego)](operator-parity-q.md)<br/>[`SIGN?`(test znaku w czasie wykonywania)](operator-sign-q.md)<br/>[`ZERO?`(Test zerowy czasu wykonania)](operator-zero-q.md)
   :::column-end:::
:::row-end:::

## <a name="logical-and-shift"></a>Koniunkcja logiczna i Shift

:::row:::
   :::column span="":::
      [`AND`(bitowe i)](operator-and.md)<br/>[`NOT`(nie bitowe)](operator-not.md)
   :::column-end:::
   :::column span="":::
      [`OR`(bitowe lub)](operator-or.md)<br/>[`SHL`(po lewej stronie bity Shift)](operator-shl.md)
   :::column-end:::
   :::column span="":::
      [`SHR`(prawy klawisz Shift)](operator-shr.md)<br/>[`XOR`(bitowe wykluczające lub)](operator-xor.md)
   :::column-end:::
:::row-end:::

## <a name="macro"></a>Makro

:::row:::
   :::column span="":::
      [`!`(literał znakowy)](operator-logical-not-masm.md)<br/>[`%`(Traktuj jako tekst)](operator-percent.md)
   :::column-end:::
   :::column span="":::
      [`;;`(Traktuj jako komentarz)](operator-semicolons.md)<br/>[`< >`(Traktuj jako jeden literał)](operator-literal.md)
   :::column-end:::
   :::column span="":::
      [`& &`(Zastąp wartość parametru)](operator-logical-and-masm.md)
   :::column-end:::
:::row-end:::

## <a name="miscellaneous"></a>Różne

:::row:::
   :::column span="":::
      [`' '`(Traktuj jako ciąg)](operator-single-quote.md)<br/>[`" "`(Traktuj jako ciąg)](operator-double-quote.md)<br/>`:`(definicja etykiety lokalnej)
   :::column-end:::
   :::column span="":::
      `::`(Rejestruj segment i przesunięcia)<br/>`::`(definicja etykiety globalnej)
   :::column-end:::
   :::column span="":::
      [`;`(Traktuj jako komentarz)](operator-semicolon.md)<br/>[`DUP`(powtarzanie deklaracji)](operator-dup.md)
   :::column-end:::
:::row-end:::

## <a name="record"></a>Rekord

:::row:::
   :::column span="":::
      [`MASK`(Pobierz maskę rekordu lub pola)](operator-mask.md)
   :::column-end:::
   :::column span="2":::
      [`WIDTH`(Pobierz rekord lub szerokość pola)](operator-width.md)
   :::column-end:::
:::row-end:::

## <a name="relational"></a>Relacyjne

:::row:::
   :::column span="":::
      [`EQ`większy](operator-eq.md)<br/>[`GE`(większe lub równe)](operator-ge.md)
   :::column-end:::
   :::column span="":::
      [`GT`(większe niż)](operator-gt.md)<br/>[`LE`(mniejsze lub równe)](operator-le.md)
   :::column-end:::
   :::column span="":::
      [`LT`(mniejsze niż)](operator-lt.md)<br/>[`NE`(nie równa się)](operator-ne.md)
   :::column-end:::
:::row-end:::

## <a name="segment"></a>Segment

:::row:::
   :::column span="":::
      [`:`(przesłonięcie segmentu)](operator-colon.md)<br/>`::`(Rejestruj segment i przesunięcia)<br/>[`IMAGEREL`(względne względem obrazu)](operator-imagerel.md)
   :::column-end:::
   :::column span="":::
      [`LROFFSET`(rozwiązane przesunięcia modułu ładującego)](operator-lroffset.md)<br/>[`OFFSET`(przesunięcie względne segmentu)](operator-offset.md)
   :::column-end:::
   :::column span="":::
      [`SECTIONREL`(względne przesunięcie sekcji)](operator-sectionrel.md)<br/>[`SEG`(Pobierz segment)](operator-seg.md)
   :::column-end:::
:::row-end:::

## <a name="type"></a>Typ

:::row:::
   :::column span="":::
      [`HIGH`(wysoko 8 bitów z najniższych 16 bitów)](operator-high.md)<br/>[`HIGH32`(wysoka 32 bitów z 64 bitów)](operator-high32.md)<br/>[`HIGHWORD`(duża liczba 16 bitów z najniższych 32 bitów)](operator-highword.md)<br/>[`LENGTH`(liczba elementów w tablicy)](operator-length.md)<br/>[`LENGTHOF`(liczba elementów w tablicy)](operator-lengthof.md)<br/>[`LOW`(niski 8 bitów)](operator-low.md)
   :::column-end:::
   :::column span="":::
      [`LOW32`(niska 32 bitów)](operator-low32.md)<br/>[`LOWWORD`(małe 16 bitów)](operator-lowword.md)<br/>[`OPATTR`(Pobierz informacje o typie argumentu)](operator-opattr.md)<br/>[`PTR`(wskaźnik do lub jako typ)](operator-ptr.md)<br/>[`SHORT`(Oznacz typ krótkiej etykiety)](operator-short.md)
   :::column-end:::
   :::column span="":::
      [`SIZE`(rozmiar typu lub zmiennej)](operator-size.md)<br/>[`SIZEOF`(rozmiar typu lub zmiennej)](operator-sizeof.md)<br/>[`THIS`(bieżąca lokalizacja)](operator-this.md)<br/>[`TYPE`(Pobierz typ wyrażenia)](operator-type.md)<br/>[`.TYPE`(Pobierz informacje o typie argumentu)](operator-dot-type.md)
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>Zobacz także

[Dokumentacja asemblera programu Microsoft Macro](microsoft-macro-assembler-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
