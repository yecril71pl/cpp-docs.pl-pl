---
title: Błąd niekrytyczny ML A2096 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2096
dev_langs:
- C++
helpviewer_keywords:
- A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e5d07afa864c9f6f4214de953aa9e03fe0e7e4f
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="ml-nonfatal-error-a2096"></a>Błąd niekrytyczny ML A2096
**Segment, grupy lub rejestru segmentu oczekiwano**  
  
 Segment lub grupy był oczekiwany, ale nie został znaleziony.  
  
 Wystąpił jeden z następujących czynności:  
  
-   Lewy operand określona z segmentem zastąpienie — operator (**:**) nie jest segmentu rejestru (CS, DS, SS, ES, FS lub GS), nazwa grupy, nazwą segmentu lub wyrażenie segmentu.  
  
-   [ASSUME](../../assembler/masm/assume.md) dyrektywy podano rejestr segmentu bez adresu prawidłowy segment, rejestru segmentu, grupy lub specjalną **PŁASKIEJ** grupy.  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)