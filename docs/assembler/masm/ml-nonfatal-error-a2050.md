---
title: "Błąd niekrytyczny ML A2050 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A2050
dev_langs: C++
helpviewer_keywords: A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a51a90f294afd0347057efb04ab37ce790532ba4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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