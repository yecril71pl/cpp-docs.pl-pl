---
title: marshaling
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: 0661a4cdde0a3a875cf27221e884f6c65b9fea55
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57269684"
---
# <a name="marshaling"></a>marshaling

Technika COM marshalingu umożliwia interfejsów udostępnianych przez obiekt w jednym procesie ma być używany w innym procesie. Organizowanie, COM zawiera kod (lub korzysta z kodu dostarczane przez obiekt implementujący interfejs) zarówno pakiet parametrów metody do formatu, który można przenosić między procesami (a także, faktycznie dla procesów uruchomionych na innych komputerach), jak i rozpakowania tych parametrów na końcu. Podobnie COM, należy wykonać te same kroki na powrót z wywołania.

> [!NOTE]
>  Marshaling zwykle nie jest konieczne po interfejsie udostępnianym przez obiekt jest używany w tym samym procesie co obiekt. Jednak przekazywanie może być potrzebny między wątkami.

## <a name="see-also"></a>Zobacz także

[Wprowadzenie do modelu COM](../atl/introduction-to-com.md)<br/>
[Organizowanie informacji](/windows/desktop/com/marshaling-details)
