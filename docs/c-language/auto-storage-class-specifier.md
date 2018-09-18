---
title: Auto — Specyfikator klasy magazynowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 8e73f57e-aa92-4e41-91ea-5c8ad2a2b332
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ca42eb26cc6bb08cd8a05e31b23e004b1cbeb8b2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057434"
---
# <a name="auto-storage-class-specifier"></a>Specyfikator automatycznej klasy magazynowania

**Automatycznie** Specyfikator klasy magazynowania deklaruje automatycznej zmiennej, zmienna o lokalne okresy istnienia. **Automatycznie** zmienna jest widoczna tylko w bloku, w którym jest zdeklarowana. Deklaracje **automatycznie** zmiennych, które mogą zawierać inicjatory, zgodnie z opisem w [inicjowania](../c-language/initialization.md). Od zmiennych o **automatycznie** klasę magazynu nie są automatycznie inicjowane, należy albo jawnie zainicjować je zadeklarować je lub przypisać je wartościami początkowymi instrukcje w bloku. Wartości niezainicjowanej **automatycznie** zmienne są niezdefiniowane. (Lokalnej zmiennej **automatycznie** lub **zarejestrować** klasę magazynu jest zawsze zainicjowana podczas chodzi w zakresie, jeśli podano inicjatora.)

Wewnętrznego **statyczne** zmiennej (statycznej zmiennej lokalnej lub zakresie bloku) mogą być inicjowane przy użyciu adresu żadnych zewnętrznych lub **statyczne** elementu, ale nie z adresu innego **automatycznie**  elementu, ponieważ adres **automatycznie** element nie jest stałą.

## <a name="see-also"></a>Zobacz też

[Auto, słowo kluczowe](../cpp/auto-keyword.md)