---
title: Operatory rzutowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cast operators
- type casts, operators
- operators [C++], cast
- type conversion, cast operators
ms.assetid: 43b90bbd-39ef-43e6-ae5d-e8a67a01de40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: abb4b84519b943d02eca277c9372a128f7d6c2fe
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098510"
---
# <a name="cast-operators"></a>Operatory rzutowania

Rzutowanie typu udostępnia metodę jawnej konwersji typu obiektu w konkretnej sytuacji.

## <a name="syntax"></a>Składnia

*wyrażenie CAST*: *jednoargumentowe wyrażenie*

**(***nazwy typu***)***wyrażenie cast*

Kompilator traktuje *wyrażenie cast* jako typ *nazwy typu* po dokonaniu rzutowanie typu. Rzutowania może służyć do konwersji obiektów o dowolnym typie skalarnym do lub z innych typów skalarnych. Rzutowania jawnego typu są ograniczone przez te same zasady, które określają skutki konwersje niejawne omówione w [konwersje przypisań](../c-language/assignment-conversions.md). Dodatkowe ograniczenia na rzutowania mogą wynikać z rzeczywistych rozmiarów lub reprezentację określonych typów. Zobacz [magazyn typów podstawowych](../c-language/storage-of-basic-types.md) informacji na temat rozmiarów rzeczywistych typów całkowitych. Aby uzyskać więcej informacji na temat rzutowania typów, zobacz [konwersje rzutowania typów](../c-language/type-cast-conversions.md).

## <a name="see-also"></a>Zobacz też

[Operator rzutowania: ()](../cpp/cast-operator-parens.md)