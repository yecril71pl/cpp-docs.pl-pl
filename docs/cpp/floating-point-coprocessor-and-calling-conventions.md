---
title: Koprocesor zmiennoprzecinkowy i konwencje wywoływania
ms.date: 11/04/2016
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
ms.openlocfilehash: 09358ee36da7e5a86c214789fa7fd0687e9b8825
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231198"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>Koprocesor zmiennoprzecinkowy i konwencje wywoływania

Jeśli piszesz procedury asemblera dla współprocesora zmiennoprzecinkowego, musisz zachować słowo kontrolne zmiennoprzecinkowe i wyczyścić stos współprocesora, chyba że zwracasz **`float`** lub **`double`** wartość (którą funkcja powinna zwrócić w St (0)).

## <a name="see-also"></a>Zobacz także

[Konwencje wywoływania](../cpp/calling-conventions.md)
