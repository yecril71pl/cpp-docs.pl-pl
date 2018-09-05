---
title: Błąd niekrytyczny ML A2085 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2085
dev_langs:
- C++
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd5ec9f36a4f956b8eeb097b6a8f8eaed89ba2b2
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681439"
---
# <a name="ml-nonfatal-error-a2085"></a>Błąd niekrytyczny ML A2085

**instrukcji lub rejestru nie są akceptowane w bieżącym trybie procesora CPU**

Próbowano użyć instrukcji, rejestr lub słowo kluczowe, które nie jest prawidłowa dla bieżącego trybu procesora.

Na przykład wymagać 32-bitowych rejestrów [.386](../../assembler/masm/dot-386.md) lub nowszej. Rejestruje kontroli, takie jak CR0 wymagają trybie uprzywilejowanym [.386p —](../../assembler/masm/dot-386p.md) lub nowszej. Ten błąd zostanie również wygenerowany dla **NEAR32**, **FAR32**, i **PROSTEGO** słów kluczowych, które wymagają. **386** lub nowszej.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>