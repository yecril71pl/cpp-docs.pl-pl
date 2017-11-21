---
title: "Czy może zawierać więcej niż jeden formant w jednym oknie? | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- controls [ATL], hosting multiple
- windows [C++], hosting multiple controls
ms.assetid: 3a967a1a-7e7e-42e3-8eed-f7bde912363f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5fa1a1b914d7d9725e8f2d9858f0481bb7aa24a4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="can-i-host-more-than-one-control-in-a-single-window"></a>Czy może zawierać więcej niż jeden formant w jednym oknie?
Nie jest możliwe więcej niż jeden kontrolki w jednym oknie hosta ATL hosta. Każde okno hosta jest przeznaczony do przechowywania dokładnie jeden formant jednocześnie (umożliwia to prosty mechanizm obsługi wiadomości odbicie i -control właściwości otaczających). Jednak należy użytkownikowi na zobaczenie wielu formantów w jednym oknie jest proste sprawa można utworzyć wiele okien hosta jako elementy podrzędne tego okna.  
  
## <a name="see-also"></a>Zobacz też  
 [Zawierania kontrolek — często zadawane pytania](../atl/atl-control-containment-faq.md)

