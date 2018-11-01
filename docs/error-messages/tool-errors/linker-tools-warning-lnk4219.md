---
title: Ostrzeżenie LNK4219 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4219
helpviewer_keywords:
- LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
ms.openlocfilehash: 7407537b55525bf622fc11cdbdb8e00244e51c18
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598253"
---
# <a name="linker-tools-warning-lnk4219"></a>Ostrzeżenie LNK4219 narzędzi konsolidatora

przepełnienie naprawy nazwa naprawy. Element docelowy "target name symboli" jest poza zakresem, zostanie wstawiona

Konsolidator dodaje sekcją thunk w sytuacji, gdy adres lub offset nie mieści się w danej instrukcji, ponieważ symbol docelowy jest zbyt daleko od lokalizacji instrukcji.

Możesz chcieć zmienić kolejność obrazu (przy użyciu [/ORDER](../../build/reference/order-put-functions-in-order.md) opcji, na przykład) w celu uniknięcia dodatkowy poziom pośredni.