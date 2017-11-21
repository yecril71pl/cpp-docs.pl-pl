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
ms.openlocfilehash: ae268175c1f104f6f39f5ecbfd1f917ef415000e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ml-nonfatal-error-a2096"></a>Błąd niekrytyczny ML A2096
**Segment, grupy lub rejestru segmentu oczekiwano**  
  
 Segment lub grupy był oczekiwany, ale nie został znaleziony.  
  
 Wystąpił jeden z następujących czynności:  
  
-   Lewy operand określona z segmentem zastąpienie — operator (**:**) nie jest segmentu rejestru (CS, DS, SS, ES, FS lub GS), nazwa grupy, nazwą segmentu lub wyrażenie segmentu.  
  
-   [ASSUME](../../assembler/masm/assume.md) dyrektywy podano rejestr segmentu bez adresu prawidłowy segment, rejestru segmentu, grupy lub specjalną **PŁASKIEJ** grupy.  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)