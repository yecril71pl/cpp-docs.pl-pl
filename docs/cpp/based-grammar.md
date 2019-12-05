---
title: __based — Gramatyka
ms.date: 11/04/2016
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
ms.openlocfilehash: a8c923b5a111144c539b5bea1b2f47eb58dd1fbd
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857648"
---
# <a name="__based-grammar"></a>__based — Gramatyka

**Microsoft Specific**

Adresowanie na podstawie jest przydatne, gdy potrzebujesz precyzyjnej kontroli nad segmentem, w którym są przydzielane obiekty (dane statyczne i dynamiczne).

Jedyną formą dopuszczalną w oparciu o 32-bitowe i 64-bitowe kompilacje jest "na podstawie wskaźnika", który definiuje typ, który zawiera 32-bit lub 64-bit przemieszczenia do bazy danych 32-bit lub 64-bit lub na podstawie typu **void**.

## <a name="grammar"></a>Gramatyka

*modyfikator zakresu z zakresem*: **__based (**  *wyrażenie podstawowe*  **)**

*wyrażenie podstawowe*: *based-variablebased-abstract-declaratorsegment-namesegment-Cast*

*zmienna*: *Identyfikator*

*oparta na deklarator*: *abstract-deklarator*

*Typ podstawowy*: *type-name*

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Wskaźniki bazowe](../cpp/based-pointers-cpp.md)