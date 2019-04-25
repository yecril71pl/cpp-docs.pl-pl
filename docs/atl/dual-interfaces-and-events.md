---
title: Podwójne interfejsy i zdarzenia
ms.date: 11/04/2016
helpviewer_keywords:
- events [C++], dual interfaces
- dual interfaces, events
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
ms.openlocfilehash: 01233edb63145d69d335349bb9dff91e6a4aca5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62198268"
---
# <a name="dual-interfaces-and-events"></a>Podwójne interfejsy i zdarzenia

Choć jest możliwe do projektowania interfejs zdarzenia jako procesory, istnieje wiele możliwych przyczyn dobrego projektowania nie Aby to zrobić. Podstawową przyczyną jest, źródło zdarzenia nastąpi tylko zdarzenia za pośrednictwem vtable lub za pośrednictwem `Invoke`, nie obie. Jeśli źródło zdarzenia wyzwala zdarzenie, jako wywołania metody bezpośredniej vtable `IDispatch` nigdy nie będzie można używać metod i jest jasne, czy interfejs powinien być interfejsem czystego vtable. Jeśli źródło zdarzenia generowane zdarzenie jako wywołanie `Invoke`, nigdy nie będzie można używać metod vtable i jest jasne, że interfejs powinien zostać dispinterface. Jeśli zdefiniujesz interfejsów zdarzeń jako duals, będzie można wymagających klientów do zaimplementowania częścią interfejsu, który nigdy nie będą używane.

> [!NOTE]
>  Ten argument nie obejmuje dwa interfejsy, ogólnie rzecz biorąc. Z perspektywy wdrożenia duals są szybkie, wygodne i dobrze obsługiwane sposób implementacji interfejsów, które są dostępne dla wielu klientów.

Istnieją dodatkowe powody, aby uniknąć interfejsów podwójną zdarzeń; Visual Basic ani programu Internet Explorer nie należy ich obsługi.

## <a name="see-also"></a>Zobacz także

[Podwójne interfejsy i ATL](../atl/dual-interfaces-and-atl.md)
