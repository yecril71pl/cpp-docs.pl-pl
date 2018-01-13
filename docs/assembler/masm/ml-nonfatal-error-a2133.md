---
title: "Błąd niekrytyczny ML A2133 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A2133
dev_langs: C++
helpviewer_keywords: A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 64619e6e14ce0268516c6c688c9a2bdeb5ea7a11
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ml-nonfatal-error-a2133"></a>Błąd niekrytyczny ML A2133
**zastąpione przez INVOKE wartości rejestru**  
  
 Rejestr został przekazany jako argument do procedury, ale kod wygenerowany przez [INVOKE](../../assembler/masm/invoke.md) Aby przekazać argumenty inne zniszczone zawartość rejestru.  
  
 Rejestruje AX, AL AH, EAX, DX, DL, DH i EDX może posłużyć asemblera Aby dokonać konwersji danych.  
  
 Użyj innego rejestru.  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)