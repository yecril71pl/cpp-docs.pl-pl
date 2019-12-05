---
title: Błąd niekrytyczny ML A2206
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2206
helpviewer_keywords:
- A2206
ms.assetid: 711846d0-5a09-4353-8857-60588c25526a
ms.openlocfilehash: 6cd24e32dc000b63a6d70520250e5a792cdbc455
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74854644"
---
# <a name="ml-nonfatal-error-a2206"></a>Błąd niekrytyczny ML A2206

**Brak operatora w wyrażeniu**

Nie można obliczyć wyrażenia, ponieważ brakuje w nim operatora. Ten komunikat o błędzie może być również efektem ubocznym poprzedniego błędu programu.

Następujący wiersz spowoduje wygenerowanie tego błędu:

```asm
value1 = ( 1 + 2 ) 3
```

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>