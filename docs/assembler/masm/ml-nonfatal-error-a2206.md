---
title: Błąd niekrytyczny ML A2206 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2206
dev_langs:
- C++
helpviewer_keywords:
- A2206
ms.assetid: 711846d0-5a09-4353-8857-60588c25526a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10edbe68ca7f0093cdeb6a9ca5a02cde07f556e6
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676351"
---
# <a name="ml-nonfatal-error-a2206"></a>Błąd niekrytyczny ML A2206

**Brak operatora w wyrażeniu**

Nie można obliczyć wyrażenia, ponieważ brakuje operatora. Ten komunikat o błędzie może być również efekt uboczny poprzedni błąd programu.

Następujące polecenie spowoduje wygenerowanie tego błędu:

```asm
value1 = ( 1 + 2 ) 3
```

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>