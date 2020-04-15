---
title: Dwa interfejsy i zdarzenia
ms.date: 11/04/2016
helpviewer_keywords:
- events [C++], dual interfaces
- dual interfaces, events
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
ms.openlocfilehash: 4ce5048c25bd55feb0f1eb20fc04ec6bfeead746
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319608"
---
# <a name="dual-interfaces-and-events"></a>Dwa interfejsy i zdarzenia

Chociaż możliwe jest zaprojektowanie interfejsu zdarzeń jako podwójnego, istnieje wiele dobrych powodów projektowych, aby tego nie robić. Podstawowym powodem jest to, że źródło zdarzenia będzie tylko ogień `Invoke`zdarzenia za pośrednictwem vtable lub za pośrednictwem , nie oba. Jeśli źródło zdarzenia uruchamia zdarzenie jako bezpośrednie wywołanie `IDispatch` metody vtable, metody nigdy nie będą używane i jest jasne, że interfejs powinien być czysty interfejs vtable. Jeśli źródło zdarzenia uruchamia zdarzenie jako `Invoke`wywołanie , metody vtable nigdy nie będą używane i jest jasne, że interfejs powinien być dispinterface. Jeśli zdefiniujesz interfejsy zdarzeń jako duals, będziesz wymagać od klientów zaimplementowania części interfejsu, który nigdy nie będzie używany.

> [!NOTE]
> Argument ten nie ma zastosowania do dwóch interfejsów, ogólnie. Z punktu widzenia implementacji duals to szybki, wygodny i dobrze obsługiwany sposób implementacji interfejsów, które są dostępne dla szerokiego grona klientów.

Istnieją dalsze powody, aby uniknąć interfejsów zdarzeń dual; nie obsługują ich ani visual basic, ani internet explorer.

## <a name="see-also"></a>Zobacz też

[Dwa interfejsy i ATL](../atl/dual-interfaces-and-atl.md)
