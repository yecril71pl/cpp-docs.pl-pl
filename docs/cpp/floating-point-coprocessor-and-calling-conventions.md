---
title: Koprocesor zmiennoprzecinkowy i konwencje wywoływania
ms.date: 11/04/2016
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
ms.openlocfilehash: 7e9184d66bde26ab0e2b345f8f10c2e28619fd2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625114"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>Koprocesor zmiennoprzecinkowy i konwencje wywoływania

Jeśli piszesz zestawu procedury dla zmiennoprzecinkowego punktu Koprocesor, należy zachować wartość zmiennoprzecinkowa punktem słowa sterującego i wyczyścić stosu Koprocesor, chyba że jest zwracany **float** lub **double** wartość (która funkcja powinna zwrócić w ST(0)).

## <a name="see-also"></a>Zobacz także

[Konwencje wywoływania](../cpp/calling-conventions.md)