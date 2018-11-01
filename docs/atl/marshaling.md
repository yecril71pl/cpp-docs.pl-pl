---
title: marshaling
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: a6129ba96cf3ac11339a8ab953e0838127f8fb3f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569796"
---
# <a name="marshaling"></a>marshaling

Technika COM marshalingu umożliwia interfejsów udostępnianych przez obiekt w jednym procesie ma być używany w innym procesie. Organizowanie, COM zawiera kod (lub korzysta z kodu dostarczane przez obiekt implementujący interfejs) zarówno pakiet parametrów metody do formatu, który można przenosić między procesami (a także, faktycznie dla procesów uruchomionych na innych komputerach), jak i rozpakowania tych parametrów na końcu. Podobnie COM, należy wykonać te same kroki na powrót z wywołania.

> [!NOTE]
>  Marshaling zwykle nie jest konieczne po interfejsie udostępnianym przez obiekt jest używany w tym samym procesie co obiekt. Jednak przekazywanie może być potrzebny między wątkami.

## <a name="see-also"></a>Zobacz też

[Wprowadzenie do modelu COM](../atl/introduction-to-com.md)<br/>
[Organizowanie informacji](/windows/desktop/com/marshaling-details)

