---
title: "Błąd niekrytyczny ML A2096 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A2096
dev_langs: C++
helpviewer_keywords: A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6d4466d87e33068b10b3f620bfbe764e4aec76c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ml-nonfatal-error-a2096"></a>Błąd niekrytyczny ML A2096
**Segment, grupy lub rejestru segmentu oczekiwano**  
  
 Segment lub grupy był oczekiwany, ale nie został znaleziony.  
  
 Wystąpił jeden z następujących czynności:  
  
-   Lewy operand określona z segmentem zastąpienie — operator (**:**) nie jest segmentu rejestru (CS, DS, SS, ES, FS lub GS), nazwa grupy, nazwą segmentu lub wyrażenie segmentu.  
  
-   [ASSUME](../../assembler/masm/assume.md) dyrektywy podano rejestr segmentu bez adresu prawidłowy segment, rejestru segmentu, grupy lub specjalną **PŁASKIEJ** grupy.  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)