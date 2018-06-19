---
title: Błąd niekrytyczny ML A2133 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: f240ed6f2e8330017e56334dfcc41be478537c7b
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32056210"
---
# <a name="ml-nonfatal-error-a2133"></a>Błąd niekrytyczny ML A2133
**zastąpione przez INVOKE wartości rejestru**  
  
 Rejestr został przekazany jako argument do procedury, ale kod wygenerowany przez [INVOKE](../../assembler/masm/invoke.md) Aby przekazać argumenty inne zniszczone zawartość rejestru.  
  
 Rejestruje AX, AL AH, EAX, DX, DL, DH i EDX może posłużyć asemblera Aby dokonać konwersji danych.  
  
 Użyj innego rejestru.  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)