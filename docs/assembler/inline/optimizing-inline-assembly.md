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
ms.openlocfilehash: 0051b16ddc19e233cfac2688c0b77e1e023f0833
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169269"
---
# <a name="optimizing-inline-assembly"></a>Optymalizacja wbudowanego asemblera

**Specyficzne dla firmy Microsoft**

Obecność bloku `__asm` w funkcji ma wpływ na optymalizację na kilka sposobów. Najpierw kompilator nie próbuje zoptymalizować samego bloku `__asm`. To, co otrzymujesz w języku asemblera, jest dokładne. Po drugie, obecność bloku `__asm` ma wpływ na rejestr magazynu zmiennych. Kompilator pozwala uniknąć zmiennych rejestrowanie w bloku `__asm`, jeśli zawartość rejestru zostanie zmieniona przez blok `__asm`. Na koniec niektóre inne optymalizacje na poziomie funkcji mają wpływ na włączenie języka zestawu w funkcji.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Wbudowany asembler](../../assembler/inline/inline-assembler.md)<br/>
