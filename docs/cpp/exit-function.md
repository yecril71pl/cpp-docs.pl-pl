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
ms.openlocfilehash: e4a1ee1a533309dfedce139efc7c6db1f41653a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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