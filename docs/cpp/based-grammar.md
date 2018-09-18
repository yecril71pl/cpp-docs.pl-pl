---
title: __based — gramatyka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43e9074de25d8cb914432123478f5f338ff4ba1e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103772"
---
# <a name="based-grammar"></a>__based — Gramatyka

## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft

Adresowanie na podstawie jest przydatne, gdy będziesz potrzebować precyzyjną kontrolę nad tym segment, w których obiekty są przydzielane (statycznych i dynamicznych na podstawie danych).

Tylko formularza na podstawie adresowania dopuszczalne w kompilacjach kodu 32-bitowych i 64-bitowy "opiera się na wskaźnik", który definiuje typ, który zawiera 32-bitową lub 64-bitowe przesunięcie podstawowy 32-bitową lub 64-bitowe lub oparte na **void**.

## <a name="grammar"></a>Gramatyka

*na podstawie zakresu — modyfikator*: **__based (***base-expression***)** 

*wyrażenie Base*: *based-variablebased-abstract-declaratorsegment-namesegment-cast*

*na podstawie zmiennej*: *identyfikator*

*na podstawie abstrakcyjny declarator*: *deklaratora abstrakcyjny*

*typem podstawowym*: *Nazwa typu*

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Wskaźniki bazowe](../cpp/based-pointers-cpp.md)