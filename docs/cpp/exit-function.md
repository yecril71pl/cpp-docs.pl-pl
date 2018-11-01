---
title: Funkcja exit
ms.date: 11/04/2016
f1_keywords:
- Exit
helpviewer_keywords:
- exit function
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
ms.openlocfilehash: 82c9d00a49c8a080d893a51052739a0265ad0860
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532564"
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