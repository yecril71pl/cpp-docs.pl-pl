---
title: Organizowanie | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ec8c85606f0f0ef3de67a61181ead6537fde179e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="marshaling"></a>Organizowanie
Organizowanie techniki COM umożliwia interfejsach udostępnionych za pomocą obiektu w jednym procesie do użycia w innym procesie. W przekazywanie, COM udostępnia kod (lub korzysta z kodu udostępniane przez osoby wdrażającej interfejs) do pakietu parametrów metod do formatu, który można przenosić między procesami (i wielu sieci dla procesów uruchomionych na innych komputerach) i Rozpakuj tych parametrów na drugim końcu. Podobnie COM, należy wykonać te same czynności na powrót z wywołania.  
  
> [!NOTE]
>  Organizowanie zwykle nie jest konieczne po interfejs dostarczony przez obiekt jest używany ten sam proces jako obiekt. Jednak organizowanie mogą być wymagane między wątkami.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do COM](../atl/introduction-to-com.md)   
 [Przekazywanie informacji](http://msdn.microsoft.com/library/windows/desktop/ms692621)

