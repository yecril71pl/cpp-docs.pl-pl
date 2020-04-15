---
title: Marshaling
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: 83cf29fb45347b7bfcfc1644546684f074061d25
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319353"
---
# <a name="marshaling"></a>Marshaling

Technika COM organizowania umożliwia interfejsy udostępniane przez obiekt w jednym procesie, które mają być używane w innym procesie. W kierowaniu COM udostępnia kod (lub używa kodu dostarczonego przez realizatora interfejsu) zarówno do pakowania parametrów metody do formatu, który może być przenoszony między procesami (jak również przez przewod do procesów uruchomionych na innych komputerach) i rozpakować te parametry na drugim końcu. Podobnie COM musi wykonać te same kroki po powrocie z wywołania.

> [!NOTE]
> Kierowanie zazwyczaj nie jest konieczne, gdy interfejs dostarczony przez obiekt jest używany w tym samym procesie co obiekt. Jednak kierowanie może być potrzebne między wątkami.

## <a name="see-also"></a>Zobacz też

[Wprowadzenie do modelu COM](../atl/introduction-to-com.md)<br/>
[Szczegóły dotyczące marshalingu](/windows/win32/com/marshaling-details)
