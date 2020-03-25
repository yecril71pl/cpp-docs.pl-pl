---
title: __based — Gramatyka
ms.date: 11/04/2016
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
ms.openlocfilehash: 149439c82780f12669e5a3180f975c573ed30422
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181411"
---
# <a name="__based-grammar"></a>__based — Gramatyka

**Specyficzne dla firmy Microsoft**

Adresowanie na podstawie jest przydatne, gdy potrzebujesz precyzyjnej kontroli nad segmentem, w którym są przydzielane obiekty (dane statyczne i dynamiczne).

Jedyną formą dopuszczalną w oparciu o 32-bitowe i 64-bitowe kompilacje jest "na podstawie wskaźnika", który definiuje typ, który zawiera 32-bit lub 64-bit przemieszczenia do bazy danych 32-bit lub 64-bit lub na podstawie typu **void**.

## <a name="grammar"></a>Gramatyka

*modyfikator zakresu z zakresem*: **__based (**  *wyrażenie podstawowe*  **)**

*wyrażenie podstawowe*: *based-variablebased-abstract-declaratorsegment-namesegment-Cast*

*zmienna*: *Identyfikator*

*oparta na deklarator*: *abstract-deklarator*

*Typ podstawowy*: *type-name*

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Wskaźniki bazowe](../cpp/based-pointers-cpp.md)
