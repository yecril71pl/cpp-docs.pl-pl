---
title: "Ostrzeżenie LNK4219 narzędzi konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4219
dev_langs: C++
helpviewer_keywords: LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c2416e8872998f9cb59efee21d33bbe60dd96d37
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4219"></a>Ostrzeżenie LNK4219 narzędzi konsolidatora
przepełnienie naprawy nazwa naprawy. Docelowy "Nazwa symbolu docelowego" jest poza zakresem, zostanie wstawiona konwersja bitowa  
  
 Konsolidator dodaje sekcją thunk w sytuacji, gdy adres lub przesunięcie nie mieści się w danej instrukcji, ponieważ symbolu docelowego jest zbyt daleko od lokalizacji tę instrukcję.  
  
 Może zajść potrzeba zmiany kolejności obrazu (przy użyciu [/kolejność](../../build/reference/order-put-functions-in-order.md) opcji, na przykład) w celu uniknięcia dodatkowy poziom pośredni.