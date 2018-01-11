---
title: "Exit — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Exit
dev_langs: C++
helpviewer_keywords: exit function
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b9e0d6a7f903d4af39698b2d98c005cbf64515eb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="exit-function"></a>Funkcja exit
**Zakończyć** funkcja zadeklarowany w pliku dołączanego standardowe STDLIB. H, kończy program w języku C++.  
  
 Wartość podana jako argument **zakończyć** jest zwracana do systemu operacyjnego jako zwracany kod lub zakończenia kod programu. Według Konwencji kod powrotny zero oznacza, że program została ukończona pomyślnie.  
  
> [!NOTE]
>  Można użyć stałe `EXIT_FAILURE` i `EXIT_SUCCESS`zdefiniowanej w STDLIB. H do wskazania powodzenia lub niepowodzenia programu.  
  
 Wystawianie `return` instrukcji z **głównego** jest odpowiednikiem wywołania funkcji **zakończyć** funkcji z wartością zwracaną jako jej argument.  
  
 Aby uzyskać więcej informacji, zobacz [zakończyć](../c-runtime-library/reference/exit-exit-exit.md) w *odwołanie do biblioteki wykonawczej*.  
  
## <a name="see-also"></a>Zobacz też  
 [Kończenie działania programu](../cpp/program-termination.md)