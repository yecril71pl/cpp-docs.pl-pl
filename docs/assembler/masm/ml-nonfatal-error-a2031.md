---
title: Błąd niekrytyczny ML A2031
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2031
helpviewer_keywords:
- A2031
ms.assetid: d5b11f58-4a00-42be-9062-8fa8728e6306
ms.openlocfilehash: f964c67ba7bf399e9a3761e4e201662a6a712a1b
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856704"
---
# <a name="ml-nonfatal-error-a2031"></a>Błąd niekrytyczny ML A2031

**musi być indeksem lub rejestrem podstawowym**

Podjęto próbę użycia rejestru, który nie jest rejestrem podstawowym ani indeksem w wyrażeniu pamięci.

Na przykład następujące wyrażenia powodują wystąpienie tego błędu:

```asm
[ax]
[bl]
```

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>