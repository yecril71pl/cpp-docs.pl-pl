---
title: Specyfikator automatycznej klasy magazynowania
ms.date: 11/04/2016
ms.assetid: 8e73f57e-aa92-4e41-91ea-5c8ad2a2b332
ms.openlocfilehash: 926322fa55a14cc736dc41fbebd5c276ad61f020
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619911"
---
# <a name="auto-storage-class-specifier"></a>Specyfikator automatycznej klasy magazynowania

**Automatycznie** Specyfikator klasy magazynowania deklaruje automatycznej zmiennej, zmienna o lokalne okresy istnienia. **Automatycznie** zmienna jest widoczna tylko w bloku, w którym jest zdeklarowana. Deklaracje **automatycznie** zmiennych, które mogą zawierać inicjatory, zgodnie z opisem w [inicjowania](../c-language/initialization.md). Od zmiennych o **automatycznie** klasę magazynu nie są automatycznie inicjowane, należy albo jawnie zainicjować je zadeklarować je lub przypisać je wartościami początkowymi instrukcje w bloku. Wartości niezainicjowanej **automatycznie** zmienne są niezdefiniowane. (Lokalnej zmiennej **automatycznie** lub **zarejestrować** klasę magazynu jest zawsze zainicjowana podczas chodzi w zakresie, jeśli podano inicjatora.)

Wewnętrznego **statyczne** zmiennej (statycznej zmiennej lokalnej lub zakresie bloku) mogą być inicjowane przy użyciu adresu żadnych zewnętrznych lub **statyczne** elementu, ale nie z adresu innego **automatycznie**  elementu, ponieważ adres **automatycznie** element nie jest stałą.

## <a name="see-also"></a>Zobacz też

[Auto, słowo kluczowe](../cpp/auto-keyword.md)