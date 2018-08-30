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
ms.openlocfilehash: ac4bb35d29d74f0e66337dc6c3999df66a63d254
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212694"
---
# <a name="marshaling"></a>marshaling
Technika COM marshalingu umożliwia interfejsów udostępnianych przez obiekt w jednym procesie ma być używany w innym procesie. Organizowanie, COM zawiera kod (lub korzysta z kodu dostarczane przez obiekt implementujący interfejs) zarówno pakiet parametrów metody do formatu, który można przenosić między procesami (a także, faktycznie dla procesów uruchomionych na innych komputerach), jak i rozpakowania tych parametrów na końcu. Podobnie COM, należy wykonać te same kroki na powrót z wywołania.  
  
> [!NOTE]
>  Marshaling zwykle nie jest konieczne po interfejsie udostępnianym przez obiekt jest używany w tym samym procesie co obiekt. Jednak przekazywanie może być potrzebny między wątkami.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do modelu COM](../atl/introduction-to-com.md)   
 [Organizowanie informacji](/windows/desktop/com/marshaling-details)

