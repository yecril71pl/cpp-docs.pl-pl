---
title: Błąd niekrytyczny ML A2133
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2133
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
ms.openlocfilehash: 9e13dd48c77b9574229023e3cfc4cc2f2221d153
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586946"
---
# <a name="ml-nonfatal-error-a2133"></a>Błąd niekrytyczny ML A2133

**Zarejestruj wartość zastępowany INVOKE**

Rejestr został przekazany jako argument do procedury, ale kod wygenerowany przez [INVOKE](../../assembler/masm/invoke.md) do przekazania inne argumenty zniszczone zawartość rejestru.

AX, AL, AH i EAX, a także DX, listy Dystrybucyjnej, DH i EDX rejestrów może służyć przez asembler przeprowadzenie konwersji danych.

Użyj innego rejestru.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>