---
title: Błąd niekrytyczny ML A2063 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2063
dev_langs:
- C++
helpviewer_keywords:
- A2063
ms.assetid: 12976b25-2159-4e0c-9df3-dcfac61091ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5ce02fcbab6452b45f38d7d8becff64a880d403
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680739"
---
# <a name="ml-nonfatal-error-a2063"></a>Błąd niekrytyczny ML A2063

**może tylko WYRÓWNAJ potęgą liczby 2: wyrażenie**

Wyrażenie określone za pomocą [WYRÓWNAJ](../../assembler/masm/align-masm.md) dyrektywy był nieprawidłowy.

**WYRÓWNAJ** wyrażenie musi być potęgą liczby 2 od 2 do 256, a musi być mniejsza niż lub równe wyrównanie bieżący segment, struktury lub Unii.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>