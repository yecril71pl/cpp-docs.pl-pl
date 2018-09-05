---
title: Błąd niekrytyczny ML A2133 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2133
dev_langs:
- C++
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0df094f5e7135ffb3b9a5f09383e03e411755de3
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678069"
---
# <a name="ml-nonfatal-error-a2133"></a>Błąd niekrytyczny ML A2133

**Zarejestruj wartość zastępowany INVOKE**

Rejestr został przekazany jako argument do procedury, ale kod wygenerowany przez [INVOKE](../../assembler/masm/invoke.md) do przekazania inne argumenty zniszczone zawartość rejestru.

AX, AL, AH i EAX, a także DX, listy Dystrybucyjnej, DH i EDX rejestrów może służyć przez asembler przeprowadzenie konwersji danych.

Użyj innego rejestru.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>