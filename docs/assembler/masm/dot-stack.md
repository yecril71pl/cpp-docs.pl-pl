---
title: . STOS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .STACK
dev_langs: C++
helpviewer_keywords: .STACK directive
ms.assetid: 70019463-5d4f-41b6-8464-023a8ac2466f
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 20557bf243db1c004d6ec62dcb589cfb8605a285
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="stack"></a>.STACK
W przypadku użycia z [. MODEL](../../assembler/masm/dot-model.md), określa segment stosu (z nazwą segmentu STOSU). Opcjonalny `size` określa liczbę bajtów stosu (ustawienie domyślne 1024). `.STACK` Dyrektywa jest automatycznie zamykany instrukcji stosu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
.STACK [[size]]  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania do dyrektyw](../../assembler/masm/directives-reference.md)