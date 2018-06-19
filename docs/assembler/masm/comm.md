---
title: COMM | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/22/2018
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
ms.openlocfilehash: 1df6c729ab130a7ff38d7f7cf83224e7425e7dba
ms.sourcegitcommit: da7b7533d1a4dc141cc0f09149e4e4196f2fe329
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
ms.locfileid: "34463026"
---
# <a name="comm"></a>COMM

Tworzy zmienną gminna z atrybutów określonych w *definicji*.

## <a name="syntax"></a>Składnia

> **COMM** *definicji* [, *definicji*]...

## <a name="remarks"></a>Uwagi

Zmienne gminna są przydzielane przez konsolidator i nie można zainicjować. Oznacza to, że nie są zależne od lokalizacji lub sekwencji tych zmiennych.

Każdy *definicji* ma następujący format:

[*langtype*] [**NEAR** &#124; **DALEKIEGO**] _etykiety_**:**_typu_[**:**_liczba_]

Opcjonalny *langtype* ustawia konwencje nazewnictwa dla nazwy, która jest zgodna. Zastępuje on dowolnego języka, określony przez **. MODEL** dyrektywy. Opcjonalny **NEAR** lub **DALEKIEGO** zastąpić bieżący model pamięci. *Etykiety* to nazwa zmiennej. *Typu* może być dowolnym specyfikatora typu ([BAJTÓW](../../assembler/masm/byte-masm.md), [WORD](../../assembler/masm/word.md)i tak dalej) lub liczba całkowita określająca liczbę bajtów. Opcjonalny *liczba* określa liczbę elementów w obiekcie danych zadeklarowane; wartość domyślna to jeden.

## <a name="example"></a>Przykład

W tym przykładzie tworzy tablicę elementów 512-BAJTOWE:

```masm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)
