---
title: Podwójne interfejsy i zdarzenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- events [C++], dual interfaces
- dual interfaces, events
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a482486be66811954602849c4bdde5b8955c887f
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763217"
---
# <a name="dual-interfaces-and-events"></a>Podwójne interfejsy i zdarzenia

Choć jest możliwe do projektowania interfejs zdarzenia jako procesory, istnieje wiele możliwych przyczyn dobrego projektowania nie Aby to zrobić. Podstawową przyczyną jest, źródło zdarzenia nastąpi tylko zdarzenia za pośrednictwem vtable lub za pośrednictwem `Invoke`, nie obie. Jeśli źródło zdarzenia wyzwala zdarzenie, jako wywołania metody bezpośredniej vtable `IDispatch` nigdy nie będzie można używać metod i jest jasne, czy interfejs powinien być interfejsem czystego vtable. Jeśli źródło zdarzenia generowane zdarzenie jako wywołanie `Invoke`, nigdy nie będzie można używać metod vtable i jest jasne, że interfejs powinien zostać dispinterface. Jeśli zdefiniujesz interfejsów zdarzeń jako duals, będzie można wymagających klientów do zaimplementowania częścią interfejsu, który nigdy nie będą używane.

> [!NOTE]
>  Ten argument nie obejmuje dwa interfejsy, ogólnie rzecz biorąc. Z perspektywy wdrożenia duals są szybkie, wygodne i dobrze obsługiwane sposób implementacji interfejsów, które są dostępne dla wielu klientów.

Istnieją dodatkowe powody, aby uniknąć interfejsów podwójną zdarzeń; Visual Basic ani programu Internet Explorer nie należy ich obsługi.

## <a name="see-also"></a>Zobacz też

[Podwójne interfejsy i ATL](../atl/dual-interfaces-and-atl.md)

