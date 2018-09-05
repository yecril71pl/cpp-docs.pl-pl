---
title: Marshaling | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f9e8e080837ed109a786c2123ab90624d994cd1
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753737"
---
# <a name="marshaling"></a>marshaling

Technika COM marshalingu umożliwia interfejsów udostępnianych przez obiekt w jednym procesie ma być używany w innym procesie. Organizowanie, COM zawiera kod (lub korzysta z kodu dostarczane przez obiekt implementujący interfejs) zarówno pakiet parametrów metody do formatu, który można przenosić między procesami (a także, faktycznie dla procesów uruchomionych na innych komputerach), jak i rozpakowania tych parametrów na końcu. Podobnie COM, należy wykonać te same kroki na powrót z wywołania.

> [!NOTE]
>  Marshaling zwykle nie jest konieczne po interfejsie udostępnianym przez obiekt jest używany w tym samym procesie co obiekt. Jednak przekazywanie może być potrzebny między wątkami.

## <a name="see-also"></a>Zobacz też

[Wprowadzenie do modelu COM](../atl/introduction-to-com.md)   
[Organizowanie informacji](/windows/desktop/com/marshaling-details)

