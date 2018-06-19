---
title: Błąd niekrytyczny ML A2050 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2050
dev_langs:
- C++
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 159ed131c13166435114234b3b16a82cd4d41d1f
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32056197"
---
# <a name="ml-nonfatal-error-a2050"></a>Błąd niekrytyczny ML A2050
**Rzeczywista lub nie jest dozwolona liczba BCD**  
  
 Liczba zmiennoprzecinkowa (rzeczywiste) lub stała binary kodowany dziesiętnych (BCD) użyto innych niż jako inicjator danych.  
  
 Wystąpił jeden z następujących czynności:  
  
-   Liczba rzeczywista lub danych konfiguracji rozruchu została użyta w wyrażeniu.  
  
-   Liczba rzeczywista użyto innych niż zainicjować dyrektywy [DWORD](../../assembler/masm/dword.md), [QWORD](../../assembler/masm/qword.md), lub [tbyte —](../../assembler/masm/tbyte.md).  
  
-   BCD użyto innych niż zainicjować dyrektywy `TBYTE`.  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)