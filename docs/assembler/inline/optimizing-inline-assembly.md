---
title: Optymalizacja wbudowanego asemblera
ms.date: 08/30/2018
helpviewer_keywords:
- storage, optimizing in inline assembly
- optimization, inline assembly
- inline assembly, optimizing
- optimizing performance, inline assembly
- __asm keyword [C++], optimizing
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
ms.openlocfilehash: a558761ff49c2b508a5bad6172cda2283801e30e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87191732"
---
# <a name="optimizing-inline-assembly"></a>Optymalizacja wbudowanego asemblera

**Specyficzne dla firmy Microsoft**

Obecność **`__asm`** bloku w funkcji ma wpływ na optymalizację na kilka sposobów. Najpierw kompilator nie próbuje zoptymalizować **`__asm`** samego bloku. To, co otrzymujesz w języku asemblera, jest dokładne. Po drugie, obecność **`__asm`** bloku ma wpływ na rejestr magazynu zmiennych. Kompilator pozwala uniknąć zmiennych rejestrowanie w bloku, **`__asm`** Jeśli zawartość rejestru zostałaby zmieniona przez **`__asm`** blok. Na koniec niektóre inne optymalizacje na poziomie funkcji mają wpływ na włączenie języka zestawu w funkcji.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Asembler wbudowany](../../assembler/inline/inline-assembler.md)<br/>
