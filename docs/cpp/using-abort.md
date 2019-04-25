---
title: Użycie przerywania
ms.date: 11/04/2016
f1_keywords:
- Abort
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
ms.openlocfilehash: 0961f6f88f5de4d435fa65e50b9dbdbc478e7608
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62244216"
---
# <a name="using-abort"></a>Użycie przerywania

Wywoływanie [przerwać](../c-runtime-library/reference/abort.md) funkcja powoduje natychmiastowe przerwanie działania. Pomija się zniszczenie normalny proces zainicjowane statycznych obiektów globalnych. Pomija również specjalnego przetwarzania, który został określony przy użyciu `atexit` funkcji.

## <a name="see-also"></a>Zobacz także

[Dodatkowe zagadnienia dotyczące kończenia](../cpp/additional-termination-considerations.md)