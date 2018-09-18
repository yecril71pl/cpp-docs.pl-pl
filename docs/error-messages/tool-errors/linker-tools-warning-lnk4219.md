---
title: Ostrzeżenie LNK4219 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4219
dev_langs:
- C++
helpviewer_keywords:
- LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: daf097cd8715a7c523e6e8a2ea46714481ca7d2a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105215"
---
# <a name="linker-tools-warning-lnk4219"></a>Ostrzeżenie LNK4219 narzędzi konsolidatora

przepełnienie naprawy nazwa naprawy. Element docelowy "target name symboli" jest poza zakresem, zostanie wstawiona

Konsolidator dodaje sekcją thunk w sytuacji, gdy adres lub offset nie mieści się w danej instrukcji, ponieważ symbol docelowy jest zbyt daleko od lokalizacji instrukcji.

Możesz chcieć zmienić kolejność obrazu (przy użyciu [/ORDER](../../build/reference/order-put-functions-in-order.md) opcji, na przykład) w celu uniknięcia dodatkowy poziom pośredni.