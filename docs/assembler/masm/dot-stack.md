---
title: . STOS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .STACK
dev_langs:
- C++
helpviewer_keywords:
- .STACK directive
ms.assetid: 70019463-5d4f-41b6-8464-023a8ac2466f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dab47677da8db2afca73a078b110300a017e7c8d
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32052303"
---
# <a name="stack"></a>.STACK
W przypadku użycia z [. MODEL](../../assembler/masm/dot-model.md), określa segment stosu (z nazwą segmentu STOSU). Opcjonalny `size` określa liczbę bajtów stosu (ustawienie domyślne 1024). `.STACK` Dyrektywa jest automatycznie zamykany instrukcji stosu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
.STACK [[size]]  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)