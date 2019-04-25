---
title: Błąd niekrytyczny ML A2085
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2085
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
ms.openlocfilehash: 729f6f38761171c6ddc4cccfc2443c6a2b597bf3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62177191"
---
# <a name="ml-nonfatal-error-a2085"></a>Błąd niekrytyczny ML A2085

**instrukcji lub rejestru nie są akceptowane w bieżącym trybie procesora CPU**

Próbowano użyć instrukcji, rejestr lub słowo kluczowe, które nie jest prawidłowa dla bieżącego trybu procesora.

Na przykład wymagać 32-bitowych rejestrów [.386](../../assembler/masm/dot-386.md) lub nowszej. Rejestruje kontroli, takie jak CR0 wymagają trybie uprzywilejowanym [.386p —](../../assembler/masm/dot-386p.md) lub nowszej. Ten błąd zostanie również wygenerowany dla **NEAR32**, **FAR32**, i **PROSTEGO** słów kluczowych, które wymagają. **386** lub nowszej.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>