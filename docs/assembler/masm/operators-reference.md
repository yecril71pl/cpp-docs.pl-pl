---
title: Odwołanie do operatorów MASM | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), operators reference
- operators [MASM]
ms.assetid: c069cab7-d6b0-4f82-a6ce-0ca3fc7e6428
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c9f5beb0e3525de6df88e44248410810502962e
ms.sourcegitcommit: 4cbde5d164d681204c4011dc95a921d75292f423
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49459156"
---
# <a name="masm-operators-reference"></a>Odwołanie do operatorów MASM

## <a name="arithmetic"></a>Operacje arytmetyczne

||||
|-|-|-|
|[* (mnożenie)](operator-multiply.md)|[+ (Dodaj)](operator-add.md)|[-(odejmowania lub odwrócić)](operator-subtract-2.md)|
|[. (pole)](operator-dot.md)|[/ (dzielenie)](operator-subtract-1.md)|[&#91;&#93;(indeks)](operator-brackets.md)|
|[Dzielenie MODULO (reszta)](operator-mod.md)|||

## <a name="control-flow"></a>Przepływ sterowania

||||
|-|-|-|
|[\! (logiczne not środowiska wykonawczego)](operator-logical-not-masm-run-time.md)|[\!= (środowisko uruchomieniowe nie jest równe)](operator-not-equal-masm.md)|[&#124;&#124;(środowiska uruchomieniowego logiczny lub)](operator-logical-or.md)|
|[& & (środowisko uruchomieniowe logicznych i)](operator-logical-and-masm-run-time.md)|[< (środowisko uruchomieniowe mniej niż)](operator-less-than-masm-run-time.md)|[\<= (środowisko uruchomieniowe mniejsze lub równe)](operator-less-or-equal-masm-run-time.md)|
|[== (środowisko uruchomieniowe równe)](operator-equal-masm-run-time.md)|[> (większe niż środowiska wykonawczego)](operator-greater-than-masm-run-time.md)|[> = (środowisko uruchomieniowe większe lub równe)](operator-greater-or-equal-masm-run-time.md)|
|[& (środowisko uruchomieniowe bitowe i)](operator-bitwise-and.md)|||
|[WYKONUJE? (test przeniesienia środowiska wykonawczego)](operator-carry-q.md)|[OVERFLOW? (środowisko uruchomieniowe przepełnienie test)](operator-overflow-q.md)|[PARZYSTOŚCI? (środowisko uruchomieniowe parzystości test)](operator-parity-q.md)|
|[ZALOGUJ SIĘ? (test logowania środowiska wykonawczego)](operator-sign-q.md)|[ZERO? (środowisko uruchomieniowe zero test)](operator-zero-q.md)||

## <a name="logical-and-shift"></a>Logiczne and -Shift

||||
|-|-|-|
|[I (bitowe i)](operator-and.md)|[NIE (bitowego not)](operator-not.md)|[OR (bitowe lub)](operator-or.md)|
|[Shl — (lewy shift bits)](operator-shl.md)|[SHR (bity przesunięcia w prawo)](operator-shr.md)|[XOR (wyłączny sumy bitowej lub)](operator-xor.md)|

## <a name="macro"></a>Macro

||||
|-|-|-|
|[\! (znak literału)](operator-logical-not-masm.md)|[% (traktowanej jako tekst)](operator-percent.md)||
|[;; (należy traktować jako komentarz)](operator-semicolons.md)|[&lt; &gt; (należy traktować jako jeden literał)](operator-literal.md)|[& & (Zastąp wartość parametru)](operator-logical-and-masm.md)|

## <a name="miscellaneous"></a>Różne

||||
|-|-|-|
|["" (traktować jako ciąg)](operator-single-quote.md)|["" (traktować jako ciąg)](operator-double-quote.md)||
|: (etykieta lokalny definicja)|:: (Zarejestruj segmentu i przesunięcie)|:: (globalne etykiety definicja)|
|[; (należy traktować jako komentarz)](operator-semicolon.md)|[DUP (deklaracja powtórzeń)](operator-dup.md)||

## <a name="record"></a>Rekord

|||
|-|-|
|[MASKA (get maski bitów rekordu lub pola)](operator-mask.md)|[SZEROKOŚĆ (get szerokość rekordu lub pola)](operator-width.md)|

## <a name="relational"></a>Relacyjne

||||
|-|-|-|
|[EQ (równe)](operator-eq.md)|[GE (większe lub równe)](operator-ge.md)|[GT (większe niż)](operator-gt.md)|
|[LE (mniejsze lub równe)](operator-le.md)|[Długoterminowe (mniejsze niż)](operator-lt.md)|[No (nie równa się)](operator-ne.md)|

## <a name="segment"></a>Segment

|||
|-|-|
|[: (przesłonięcie segmentu)](operator-colon.md)|:: (Zarejestruj segmentu i przesunięcie)|
|[Imagerel — (przesunięcie względne obrazu)](operator-imagerel.md)|[Lroffset — (moduł ładujący rozpoznanego przesunięcia)](operator-lroffset.md)|
|[Przesunięcie (przesunięcie względne segmentu)](operator-offset.md)|[Sectionrel — (przesunięcie względne sekcji)](operator-sectionrel.md)|
|[Seg — (get segmentu)](operator-seg.md)||

## <a name="type"></a>Typ

||||
|-|-|-|
|[Wysoki (wysoka 8 bitów najniższy 16 bitów)](operator-high.md)|[High32 — (wysoka 32 bity 64-bitowy)](operator-high32.md)|[Highword — (wysoka 16 bitów o najniższej 32-bitowy)](operator-highword.md)|
|[DŁUGOŚĆ (liczba elementów w tablicy)](operator-length.md)|[Lengthof — (liczba elementów w tablicy)](operator-lengthof.md)|[Niski (niskie 8 bitów)](operator-low.md)|
|[Low32 — (niska 32-bitowy)](operator-low32.md)|[Lowword — (niski 16 bitów)](operator-lowword.md)|[Opattr — (argument typu informacje)](operator-opattr.md)|
|[PTR (wskaźnik lub jako typ)](operator-ptr.md)|[SHORT (znak krótkich etykietach typu)](operator-short.md)|[ROZMIAR (rozmiar, typ lub zmiennej)](operator-size.md)|
|[Operator SIZEOF (rozmiar, typ lub zmiennej)](operator-sizeof.md)|[Ta (bieżąca lokalizacja)](operator-this.md)|[Typ (typ wyrażenia get)](operator-type.md)|
|[. Typ (argument typu informacje)](operator-dot-type.md)|||

## <a name="see-also"></a>Zobacz także

[Microsoft Macro Assembler — dokumentacja](microsoft-macro-assembler-reference.md)<br/>
