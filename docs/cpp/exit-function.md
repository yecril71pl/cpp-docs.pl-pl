---
title: Funkcja Exit | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Exit
dev_langs:
- C++
helpviewer_keywords:
- exit function
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce4272ecfee4b3d02d8bf79f7816200a392c9735
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404831"
---
# <a name="exit-function"></a>Funkcja exit
**Wyjść** funkcji zadeklarowanych w pliku standardowych dołączonych \<stdlib.h >, kończy program w języku C++.  
  
 Wartość podana jako argument do **wyjść** są zwracane do programu kodu lub przycisk Zakończ, kod powrotny systemu operacyjnego. Zgodnie z Konwencją kod powrotny zero oznacza, że program została ukończona pomyślnie.  
  
> [!NOTE]
>  Można używać stałych EXIT_FAILURE i EXIT_SUCCESS, zdefiniowane w \<stdlib.h > w celu wskazania powodzenia lub niepowodzenia działania programu.  
  
 Wystawianie **zwracają** instrukcji z `main` funkcja jest równoważne z wywoływaniem **wyjść** funkcji z wartością zwracaną jako argumentem.  
  
 Aby uzyskać więcej informacji, zobacz [wyjść](../c-runtime-library/reference/exit-exit-exit.md) w *odwołanie do biblioteki wykonawczej*.  
  
## <a name="see-also"></a>Zobacz także  
 [Kończenie działania programu](../cpp/program-termination.md)