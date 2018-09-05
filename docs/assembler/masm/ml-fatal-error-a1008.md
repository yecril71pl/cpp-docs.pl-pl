---
title: Błąd krytyczny ML A1008 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1008
dev_langs:
- C++
helpviewer_keywords:
- A1008
ms.assetid: fe592f9d-c37b-4cd8-a51d-e3c15ddcab83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ec709823856e17c90d4af2a06262b30c966f39c
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691941"
---
# <a name="ml-fatal-error-a1008"></a>Błąd krytyczny ML A1008

**Zagnieżdżanie niedopasowane — makro**

Albo makra nie zostało zakończone przed końcem pliku lub kończący dyrektywy [endm —](../../assembler/masm/endm.md) znaleziono poza blokiem makra.

Jedną z przyczyn tego błędu jest pominięcie kropki (.) przed [. Powtórz](../../assembler/masm/dot-repeat.md) lub [. GDY](../../assembler/masm/dot-while.md).

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>