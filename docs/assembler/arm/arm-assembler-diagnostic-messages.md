---
title: Komunikaty diagnostyczne asemblera ARM | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- A2193
- A2196
- A2202
- A2513
- A2557
- A4228
- A4508
- A4509
helpviewer_keywords:
- A2193
- A2196
- A2202
- A2513
- A2557
- A4228
- A4508
- A4509
dev_langs:
- C++
ms.assetid: 52b38267-6023-4bdc-a0ef-863362f48eec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 765a2c842d9e3714edd3303d3536efe603bd9c2c
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43684849"
---
# <a name="arm-assembler-diagnostic-messages"></a>Komunikaty diagnostyczne asemblera ARM

Asemblera ARM firmy Microsoft (*armasm*) emituje diagnostycznych ostrzeżenia i błędy po ich napotkaniu. W tym artykule opisano najbardziej często napotykanych wiadomości.

## <a name="syntax"></a>Składnia

> <em>Nazwa pliku</em>**(**<em>numer wiersza</em>**):** \[ **błąd**|**ostrzeżenie** ] **A**<em>numer</em>**:** *wiadomości*

## <a name="diagnostic-messages---errors"></a>Komunikaty diagnostyczne — błędy

> A2193: Ta instrukcja generuje nieprzewidywalne zachowanie

Architektura ARM nie może zagwarantować, co się dzieje podczas wykonywania tej instrukcji.  Aby uzyskać szczegółowe informacje o dobrze zdefiniowanych formularzy tej instrukcji, zapoznaj się [ARM architektury Reference Manual](http://go.microsoft.com/fwlink/p/?linkid=246464).

```asm
    ADD r0, r8, pc         ; A2193: this instruction generates unpredictable behavior
```

> A2196: instrukcja nie może być zakodowany za pomocą 16 bitów

Określona instrukcja nie może zostać zakodowana jako instrukcji Thumb 16-bitowych.  Określ instrukcję 32-bitowych lub rozmieszczanie kodu w celu umożliwienia etykietą docelową szereg instrukcji 16-bitowych.

Asembler może podejmować prób kodowanie gałąź w 16 bitów i zakończyć się niepowodzeniem z powodu następującego błędu, nawet jeśli gałąź 32-bitowych jest można kodować. Ten problem można rozwiązać, używając `.W` specyfikator, aby wyraźnie oznaczyć gałąź jako 32-bitowych.

```asm
    ADD.N r0, r1, r2      ; A2196: instruction cannot be encoded in 16 bits

    B.W label             ; OK
    B.N label             ; A2196: instruction cannot be encoded in 16 bits
    SPACE 10000
label
```

> A2202: Składnia instrukcji Pre-UAL niedozwolona w regionie THUMB

Kod Thumb należy użyć składni Unified języka asemblera (UAL, Distributed File System).  Stara składnia nie jest akceptowane.

```asm
    ADDEQS r0, r1         ; A2202: Pre-UAL instruction syntax not allowed in THUMB region
    ADDSEQ r0, r1         ; OK
```

> A2513: Obracanie musi być parzysta

W trybie ARM istnieje alternatywny składnia określająca stałe.  Zamiast pisania `#<const>`, można napisać `#<byte>,#<rot>`, która reprezentuje stałą wartość, która uzyskuje się przez obracanie wartość `<byte>` bezpośrednio przez `<rot>`.  Gdy używasz tej składni, należy wartość `<rot>` nawet.

```asm
    MOV r0, #4, #2       ; OK
    MOV r0, #4, #1       ; A2513: Rotation must be even
```

> A2557: Niepoprawna liczba bajtów do zapisania z powrotem

W strukturze NEON ładować i przechowywać instrukcje (`VLDn`, `VSTn`), istnieje alternatywny składnia określająca zapisywania zwrotnego podstawowy rejestrowania się.  Zamiast umieszczać wykrzyknika (!), po adresem, można określić natychmiastowego wartość, która wskazuje przesunięcie ma zostać dodany do rejestru podstawowej.  Jeśli używasz tej składni, należy określić dokładną liczbę bajtów, które zostały załadowane lub przechowywane przez instrukcję.

```asm
    VLD1.8 {d0-d3}, [r0]!         ; OK
    VLD1.8 {d0-d3}, [r0], #32     ; OK
    VLD1.8 {d0-d3}, [r0], #100    ; A2557: Incorrect number of bytes to write back
```

## <a name="diagnostic-messages---warnings"></a>Komunikaty diagnostyczne — ostrzeżenia

> A4228: Przekracza wartość wyrównania wyrównania obszaru; wyrównanie nie jest gwarantowana

Wyrównanie, który jest określony w `ALIGN` dyrektywa jest większa niż wyrównanie otaczający `AREA`.  W rezultacie asembler nie może zagwarantować, że `ALIGN` dyrektywy będą uznawane.

Aby rozwiązać ten problem, można określić na `AREA` dyrektywy `ALIGN` atrybut, który jest równy lub większy niż żądany wyrównania.

```asm
AREA |.myarea1|
ALIGN 8           ; A4228: Alignment value exceeds AREA alignment; alignment not guaranteed

AREA |.myarea2|,ALIGN=3
ALIGN 8           ; OK
```

> A4508: Użyj tej stałej obrócony jest przestarzały.

W trybie ARM istnieje alternatywny składnia określająca stałe.  Zamiast pisania `#<const>`, można napisać `#<byte>,#<rot>`, która reprezentuje stałą wartość, która uzyskuje się przez obracanie wartość `<byte>` bezpośrednio przez `<rot>`.  W niektórych kontekstach ARM jest przestarzała użytkowania tych obrócony stałych. W takich przypadkach należy użyć podstawowa `#<const>` składni zamiast tego.

```asm
    ANDS r0, r0, #1                ; OK
    ANDS r0, r0, #4, #2            ; A4508: Use of this rotated constant is deprecated
```

> A4509: Ta forma instrukcji warunkowych jest przestarzały.

Ta forma instrukcji warunkowych została zastąpiona przez ARM w architekturze ARMv8. Firma Microsoft zaleca zmianę kod, aby użyć rozgałęzień warunkowych. Aby zobaczyć, które instrukcje warunkowe są nadal obsługiwane, zapoznaj się z [ARM architektury Reference Manual](http://go.microsoft.com/fwlink/p/?linkid=246464).

To ostrzeżenie nie jest emitowane, kiedy **- oldit** przełącznik wiersza polecenia jest używany.

```asm
    ADDEQ r0, r1, r8              ; A4509: This form of conditional instruction is deprecated
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja wiersza polecenia asemblera ARM](../../assembler/arm/arm-assembler-command-line-reference.md)<br/>
[Dyrektywy ARM dotycząca asemblera](../../assembler/arm/arm-assembler-directives.md)<br/>
