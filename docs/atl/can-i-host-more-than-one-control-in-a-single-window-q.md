---
title: Czy może zawierać więcej niż jeden formant w jednym oknie? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [ATL], hosting multiple
- windows [C++], hosting multiple controls
ms.assetid: 3a967a1a-7e7e-42e3-8eed-f7bde912363f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ceb9444b6371e261115bbf52ef5a249100772d1f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="can-i-host-more-than-one-control-in-a-single-window"></a>Czy może zawierać więcej niż jeden formant w jednym oknie?
Nie jest możliwe więcej niż jeden kontrolki w jednym oknie hosta ATL hosta. Każde okno hosta jest przeznaczony do przechowywania dokładnie jeden formant jednocześnie (umożliwia to prosty mechanizm obsługi wiadomości odbicie i -control właściwości otaczających). Jednak należy użytkownikowi na zobaczenie wielu formantów w jednym oknie jest proste sprawa można utworzyć wiele okien hosta jako elementy podrzędne tego okna.  
  
## <a name="see-also"></a>Zobacz też  
 [Zawierania kontrolek — często zadawane pytania](../atl/atl-control-containment-faq.md)

