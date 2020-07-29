---
title: __based — Gramatyka
ms.date: 11/04/2016
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
ms.openlocfilehash: 539ccef65477bafe2c46ce328bdaf65f52aff1b9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229158"
---
# <a name="__based-grammar"></a>__based — Gramatyka

**Specyficzne dla firmy Microsoft**

Adresowanie na podstawie jest przydatne, gdy potrzebujesz precyzyjnej kontroli nad segmentem, w którym są przydzielane obiekty (dane statyczne i dynamiczne).

Jedyną formą dopuszczalną w oparciu o 32-bitowe i 64-bitowe kompilacje jest "w oparciu o wskaźnik", który definiuje typ, który zawiera 32-bit lub 64-bit do 32, lub na podstawie **`void`** .

## <a name="grammar"></a>Gramatyka

*modyfikator zakresu z zakresem*: **__based (**  *wyrażenie podstawowe*  **)**

*wyrażenie podstawowe*: *based-variablebased-abstract-declaratorsegment-namesegment-Cast*

*zmienna*: *Identyfikator*

*oparta na deklarator*: *abstract-deklarator*

*Typ podstawowy*: *type-name*

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Wskaźniki bazujące](../cpp/based-pointers-cpp.md)
