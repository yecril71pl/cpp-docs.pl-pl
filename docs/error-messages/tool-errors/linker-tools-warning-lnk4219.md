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
ms.openlocfilehash: 59cb7376957b7985b7ae2335ea472171d490ff42
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301138"
---
# <a name="linker-tools-warning-lnk4219"></a>Ostrzeżenie LNK4219 narzędzi konsolidatora
przepełnienie naprawy nazwa naprawy. Docelowy "Nazwa symbolu docelowego" jest poza zakresem, zostanie wstawiona konwersja bitowa  
  
 Konsolidator dodaje sekcją thunk w sytuacji, gdy adres lub przesunięcie nie mieści się w danej instrukcji, ponieważ symbolu docelowego jest zbyt daleko od lokalizacji tę instrukcję.  
  
 Może zajść potrzeba zmiany kolejności obrazu (przy użyciu [/kolejność](../../build/reference/order-put-functions-in-order.md) opcji, na przykład) w celu uniknięcia dodatkowy poziom pośredni.