---
title: 2.7.2.4 — udostępnione
ms.date: 11/04/2016
ms.assetid: c9c5d653-58fc-4620-ab0a-443ac4f8ba2e
ms.openlocfilehash: ae470f4be67fac57146017d3e2791f6f95aa61b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583446"
---
# <a name="2724-shared"></a>2.7.2.4 — udostępnione

Ta klauzula udostępnia zmiennych, które pojawiają się w *liście zmiennych* przez wszystkie wątki w zespole. Wszystkie wątki w zespole dostęp do tego samego obszaru pamięci masowej **udostępnionego** zmiennych.

Składnia **udostępnionego** klauzula jest w następujący sposób:

```
shared(variable-list)
```