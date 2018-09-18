---
title: Niewłaściwy dostęp do złożenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ac723ed80eaebc4b3f245ef56b761600007cd2d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028379"
---
# <a name="improper-access-to-a-union"></a>Niewłaściwy dostęp do złożenia

**ANSI 3.3.2.3** składowej Unii obiektu odbywa się przy użyciu członkiem innego typu

Jeśli zadeklarowano sumę dwóch typów jednej wartości są przechowywane, ale Unii odbywa się przy użyciu innego typu, wyniki są nieprzewidywalne.

Na przykład sumę **float** i `int` jest zadeklarowana. A **float** wartości są przechowywane, ale program później dostęp do wartości jako `int`. W takiej sytuacji wartość będzie zależeć od pamięci wewnętrznej **float** wartości. Wartość całkowitą nie być wiarygodne.

## <a name="see-also"></a>Zobacz też

[Struktury, złożenia, wyliczenia i pola bitowe](../c-language/structures-unions-enumerations-and-bit-fields.md)