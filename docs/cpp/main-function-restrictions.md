---
title: Ograniczenia funkcji Main | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Main
dev_langs:
- C++
helpviewer_keywords:
- main function, restrictions on using
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93f5cce15d4db9f7f6d4e3361d22028fccd676f2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117364"
---
# <a name="main-function-restrictions"></a>Ograniczenia funkcji main

Kilku ograniczeniom **głównego** funkcji, które nie mają zastosowanie do innych funkcji w języku C++. **Głównego** funkcji:

- Nie mogą być przeciążone (zobacz [przeciążanie funkcji](function-overloading.md)).

- Nie można zadeklarować jako **wbudowane**.

- Nie można zadeklarować jako **statyczne**.

- Nie można jej adres miały.

- Nie można wywołać.

## <a name="see-also"></a>Zobacz także

[main: uruchamianie programu](../cpp/main-program-startup.md)