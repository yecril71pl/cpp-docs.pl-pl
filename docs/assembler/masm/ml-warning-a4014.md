---
title: "Ostrzeżenie ML A4014 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A4014
dev_langs: C++
helpviewer_keywords: A4014
ms.assetid: 11bc8920-3255-4ac8-999a-b9ea9c15bc81
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2c618d4414dc69f9c69728f47f1b7c3ba7c2f742
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ml-warning-a4014"></a>Ostrzeżenie ML A4014
instrukcje i zainicjowane dane nie są obsługiwane w segmentach BSS  
  
 Została podjęta próba zdefiniowania danymi zainicjowanymi wewnątrz sekcji BSS.  Sekcja BSS jest zdefiniowany jako klasa, której nazwa jest BSS.  Obejmuje to uproszczona segmentu `.data?`.  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)