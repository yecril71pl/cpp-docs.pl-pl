---
title: COMM | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- COMM
dev_langs:
- C++
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 87bf6d91de052d7ecaf637100b455e66819c748b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43690035"
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
