---
title: COMM
ms.date: 08/30/2018
f1_keywords:
- COMM
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
ms.openlocfilehash: 342c8acd95fd45de1a21dc298325de9a7b40b717
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434804"
---
# <a name="comm"></a>COMM

Tworzy zmienną gminna za pomocą atrybutów, określona w *definicji*.

## <a name="syntax"></a>Składnia

> **COMM** *definicji* [, *definicji*]...

## <a name="remarks"></a>Uwagi

Gminna zmienne są przydzielane przez konsolidator i nie można zainicjować. Oznacza to, że nie mogą być zależne od lokalizacji lub sekwencji takich zmiennych.

Każdy *definicji* ma następującą postać:

[*langtype*] [**NEAR** &#124; **DALEKIEGO**] _etykiety_**:**_typu_[**:**_liczba_]

Opcjonalny *langtype* ustawia konwencje nazewnictwa dla nazwy, która jest zgodna. Zastępuje ona wszelkie języka określona przez **. MODEL** dyrektywy. Opcjonalny **NEAR** lub **DALEKIEGO** zastąpić bieżący model pamięci. *Etykiety* to nazwa zmiennej. *Typu* może być dowolny Specyfikator typu ([BAJTÓW](../../assembler/masm/byte-masm.md), [WORD](../../assembler/masm/word.md)i tak dalej) lub liczbę całkowitą określającą liczbę bajtów. Opcjonalny *liczba* określa liczbę elementów w obiekcie danych zadeklarowany; wartość domyślna to jeden.

## <a name="example"></a>Przykład

W tym przykładzie tworzy tablicę elementów 512-BAJTOWE:

```asm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)<br/>
