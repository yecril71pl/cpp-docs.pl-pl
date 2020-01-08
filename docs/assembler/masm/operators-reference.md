---
title: Odwołania do operatorów MASM
ms.date: 12/17/2019
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), operators reference
- operators [MASM]
ms.assetid: c069cab7-d6b0-4f82-a6ce-0ca3fc7e6428
ms.openlocfilehash: c0059ab1b0204b79e040d18bd5aa88145775ebcd
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318764"
---
# <a name="masm-operators-reference"></a>Odwołania do operatorów MASM

## <a name="arithmetic"></a>Operacje arytmetyczne

||||
|-|-|-|
|[* (pomnóż)](operator-multiply.md)|[+ (Dodaj)](operator-add.md)|[-(Odejmij lub Negate)](operator-subtract-2.md)|
|[. polami](operator-dot.md)|[/(dzielenie)](operator-subtract-1.md)|[&#91;&#93;indeks](operator-brackets.md)|
|[MOD (reszta)](operator-mod.md)|||

## <a name="control-flow"></a>Przepływ sterowania

||||
|-|-|-|
|[\! (nie ma logicznego środowiska uruchomieniowego)](operator-logical-not-masm-run-time.md)|[\!= (środowisko uruchomieniowe nie jest równe)](operator-not-equal-masm.md)|[&#124;&#124;(logiczne środowisko uruchomieniowe lub)](operator-logical-or.md)|
|[& & (logiczne środowisko uruchomieniowe i)](operator-logical-and-masm-run-time.md)|[< (środowisko uruchomieniowe mniejsze niż)](operator-less-than-masm-run-time.md)|[\<= (mniejsze lub równe środowisko uruchomieniowe)](operator-less-or-equal-masm-run-time.md)|
|[= = (równe środowisko uruchomieniowe)](operator-equal-masm-run-time.md)|[> (środowisko uruchomieniowe większe niż)](operator-greater-than-masm-run-time.md)|[> = (środowisko uruchomieniowe jest większe lub równe)](operator-greater-or-equal-masm-run-time.md)|
|[& (bitowe środowisko uruchomieniowe i)](operator-bitwise-and.md)|||
|[SPRAW? (test przenoszenia przez środowisko uruchomieniowe)](operator-carry-q.md)|[PRZEPŁYW? (test przepełnienia środowiska uruchomieniowego)](operator-overflow-q.md)|[BITU? (test parzystości środowiska uruchomieniowego)](operator-parity-q.md)|
|[ZAPIS? (test znaku w czasie wykonywania)](operator-sign-q.md)|[ZER? (Test zerowy czasu wykonania)](operator-zero-q.md)||

## <a name="logical-and-shift"></a>Koniunkcja logiczna i Shift

||||
|-|-|-|
|[AND (bitowe i)](operator-and.md)|[NOT (bitowe not)](operator-not.md)|[OR (bitowe lub)](operator-or.md)|
|[SHL (pozostały bity Shift)](operator-shl.md)|[SHR (przesuń w prawo bity)](operator-shr.md)|[XOR (bitowe wykluczające or)](operator-xor.md)|

## <a name="macro"></a>Macro

||||
|-|-|-|
|[\! (literał znakowy)](operator-logical-not-masm.md)|[% (Traktuj jako tekst)](operator-percent.md)||
|[;; (Traktuj jako komentarz)](operator-semicolons.md)|[&lt; &gt; (Traktuj jako jeden literał)](operator-literal.md)|[& & (Zastąp wartość parametru)](operator-logical-and-masm.md)|

## <a name="miscellaneous"></a>Różne

||||
|-|-|-|
|["" (Traktuj jako ciąg)](operator-single-quote.md)|["" (Traktuj jako ciąg)](operator-double-quote.md)||
|: (definicja etykiety lokalnej)|:: (Rejestruj segment i przesunięcia)|:: (definicja etykiety globalnej)|
|[; (Traktuj jako komentarz)](operator-semicolon.md)|[DUP (Powtarzaj deklarację)](operator-dup.md)||

## <a name="record"></a>Rekord

|||
|-|-|
|[Maska (Pobieranie rekordu lub maski bitów pola)](operator-mask.md)|[Szerokość (Pobieranie rekordu lub szerokość pola)](operator-width.md)|

## <a name="relational"></a>Relacyjne

||||
|-|-|-|
|[EQ (równe)](operator-eq.md)|[GE (większe lub równe)](operator-ge.md)|[GT (większe niż)](operator-gt.md)|
|[LE (mniejsze lub równe)](operator-le.md)|[LT (mniejsze niż)](operator-lt.md)|[NE (nie równa się)](operator-ne.md)|

## <a name="segment"></a>Segment

|||
|-|-|
|[: (przesłonięcie segmentu)](operator-colon.md)|:: (Rejestruj segment i przesunięcia)|
|[IMAGEREL (odsunięte względem obrazu)](operator-imagerel.md)|[LROFFSET (rozwiązane przesunięcia modułu ładującego)](operator-lroffset.md)|
|[Przesunięcie (względne przesunięcie segmentu)](operator-offset.md)|[SECTIONREL (względne przesunięcie sekcji)](operator-sectionrel.md)|
|[SEG (Pobierz segment)](operator-seg.md)||

## <a name="type"></a>Typ

||||
|-|-|-|
|[Wysoka (wysoko 8 bitów z najniższych 16 bitów)](operator-high.md)|[HIGH32 (wysokie 32 bitów z 64 bitów)](operator-high32.md)|[HIGHWORD (wysokie 16 bitów z najniższych 32 bitów)](operator-highword.md)|
|[Długość (liczba elementów w tablicy)](operator-length.md)|[LENGTHOF (liczba elementów w tablicy)](operator-lengthof.md)|[NISKI (niski 8 bitów)](operator-low.md)|
|[LOW32 (niska 32 bitów)](operator-low32.md)|[LOWWORD (mały 16 bitów)](operator-lowword.md)|[OPATTR (Uzyskiwanie informacji o typie argumentu)](operator-opattr.md)|
|[PTR (wskaźnik do lub jako typ)](operator-ptr.md)|[SHORT (Oznacz typ krótkiej etykiety)](operator-short.md)|[ROZMIAR (rozmiar typu lub zmiennej)](operator-size.md)|
|[SIZEOF (rozmiar typu lub zmiennej)](operator-sizeof.md)|[THIS (bieżąca lokalizacja)](operator-this.md)|[Typ (Get Expression Type)](operator-type.md)|
|[. Typ (Uzyskiwanie informacji o typie argumentu)](operator-dot-type.md)|||

## <a name="see-also"></a>Zobacz także

[Odwołanie do asemblera programu Microsoft Macro](microsoft-macro-assembler-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
