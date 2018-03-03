---
title: "Exit — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Exit
dev_langs:
- C++
helpviewer_keywords:
- exit function
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ee6a34a70465904e6725f42e68eb4a00c03a1661
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="exit-function"></a>Funkcja exit
**Zakończyć** funkcja zadeklarowany w pliku dołączanego standardowe \<stdlib.h >, program w języku C++ kończy.  
  
 Wartość podana jako argument **zakończyć** jest zwracana do systemu operacyjnego jako zwracany kod lub zakończenia kod programu. Według Konwencji kod powrotny zero oznacza, że program została ukończona pomyślnie.  
  
> [!NOTE]
>  Można użyć stałe `EXIT_FAILURE` i `EXIT_SUCCESS`zdefiniowanej w \<stdlib.h >, aby wskazać powodzenie lub niepowodzenie działania programu.  
  
 Wystawianie `return` instrukcji z **głównego** jest odpowiednikiem wywołania funkcji **zakończyć** funkcji z wartością zwracaną jako jej argument.  
  
 Aby uzyskać więcej informacji, zobacz [zakończyć](../c-runtime-library/reference/exit-exit-exit.md) w *odwołanie do biblioteki wykonawczej*.  
  
## <a name="see-also"></a>Zobacz też  
 [Kończenie działania programu](../cpp/program-termination.md)