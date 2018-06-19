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
ms.openlocfilehash: 99dc173f3dde8ea81f6dc11d02298cd94673f999
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354070"
---
# <a name="dual-interfaces-and-events"></a>Podwójne interfejsy i zdarzenia
Jest możliwe do projektowania interfejsu zdarzenia jako dwuportową, istnieje wiele powodów dobry projekt nie w tym celu. Podstawowe przyczyny jest źródło zdarzenia uruchomią tylko zdarzenia za pośrednictwem vtable lub za pośrednictwem `Invoke`, nie oba. Jeśli źródło zdarzenia generowane zdarzenie jako vtable bezpośrednie wywołania metody `IDispatch` nigdy nie będzie można używać metod i jest jasne, czy interfejs powinien być interfejsem czysty vtable. Jeśli źródło zdarzenia generowane zdarzenie jako wywołanie `Invoke`, nigdy nie będzie można używać metod vtable i jest jasne, czy interfejs powinien być dispinterface. W przypadku definiowania interfejsów zdarzeń jako duals, będzie można wymagających klientów do zaimplementowania część interfejs, który nigdy nie będą używane.  
  
> [!NOTE]
>  Ten argument nie ma zastosowania do podwójne interfejsy ogólnie. Z perspektywy wdrożenia duals są szybkie, wygodne i dobrze obsługiwane sposób implementowania interfejsów, które są dostępne dla wielu klientów.  
  
 Dodatkowo są powodów, aby uniknąć interfejsów dwóch zdarzeń; Visual Basic ani programu Internet Explorer nie obsługuje ich.  
  
## <a name="see-also"></a>Zobacz też  
 [Podwójne interfejsy i ATL](../atl/dual-interfaces-and-atl.md)

