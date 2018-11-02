---
title: Naked (C)
ms.date: 11/04/2016
helpviewer_keywords:
- naked keyword [C], storage-class attribute
- naked keyword [C]
- prolog code
- epilog code
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
ms.openlocfilehash: c79502d1793df2a3340eed26c67cca5d2a8b0d9b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537244"
---
# <a name="naked-c"></a>Naked (C)

**Microsoft Specific**

Atrybut "naked" klasę magazynu jest rozszerzeniem specyficzne dla firmy Microsoft dla języka C. Kompilator generuje kod bez kodu prologu i epilogu funkcji zadeklarowana z atrybutem "naked" klasy magazynowania. Funkcji "naked" są przydatne, gdy trzeba napisać własne sekwencji kodu prologu/epilogu przy użyciu kodu asemblera wbudowanego. Funkcje naked są przydatne przy pisaniu sterowniki urządzeń wirtualnych.

Określone informacje o korzystaniu z atrybutem "naked" można wyświetlić [funkcji "naked"](../c-language/naked-functions.md).

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Rozszerzone atrybuty klasy magazynu języka C](../c-language/c-extended-storage-class-attributes.md)