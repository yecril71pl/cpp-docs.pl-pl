---
title: Użycie przerywania
ms.date: 11/04/2016
f1_keywords:
- Abort
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
ms.openlocfilehash: 0961f6f88f5de4d435fa65e50b9dbdbc478e7608
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591831"
---
# <a name="using-abort"></a>Użycie przerywania

Wywoływanie [przerwać](../c-runtime-library/reference/abort.md) funkcja powoduje natychmiastowe przerwanie działania. Pomija się zniszczenie normalny proces zainicjowane statycznych obiektów globalnych. Pomija również specjalnego przetwarzania, który został określony przy użyciu `atexit` funkcji.

## <a name="see-also"></a>Zobacz także

[Dodatkowe zagadnienia dotyczące kończenia](../cpp/additional-termination-considerations.md)