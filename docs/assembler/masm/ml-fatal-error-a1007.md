---
title: Błąd krytyczny ML A1007 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1007
dev_langs:
- C++
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 539ab431510d5dc721e6531c11069a87e27c287a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693604"
---
# <a name="ml-fatal-error-a1007"></a>Błąd krytyczny ML A1007

**poziom zagnieżdżenia, które są zbyt głęboko**

Asembler osiągnęła limit zagnieżdżania. Limit wynosi 20 poziomy, chyba że zaznaczono inaczej.

Jedną z następujących był zbyt głęboko zagnieżdżone:

- Dyrektywy wysokiego poziomu, takie jak [. Jeśli](../../assembler/masm/dot-if.md), [. Powtórz](../../assembler/masm/dot-repeat.md), lub [. GDY](../../assembler/masm/dot-while.md).

- Definicja struktury.

- Dyrektywa zestawu warunkowe.

- Definicja procedury.

- A [pushcontext —](../../assembler/masm/pushcontext.md) — dyrektywa (limit wynosi 10).

- Definicja segmentu.

- Plik dołączania.

- Makra.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>