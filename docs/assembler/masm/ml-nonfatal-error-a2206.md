---
title: Błąd niekrytyczny ML A2206
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2206
helpviewer_keywords:
- A2206
ms.assetid: 711846d0-5a09-4353-8857-60588c25526a
ms.openlocfilehash: 6590d294b967d33bb016078f187c7aeb0649719d
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316788"
---
# <a name="ml-nonfatal-error-a2206"></a>Błąd niekrytyczny ML A2206

**Brak operatora w wyrażeniu**

Nie można obliczyć wyrażenia, ponieważ brakuje w nim operatora. Ten komunikat o błędzie może być również efektem ubocznym poprzedniego błędu programu.

Następujący wiersz spowoduje wygenerowanie tego błędu:

```asm
value1 = ( 1 + 2 ) 3
```

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](ml-error-messages.md)
