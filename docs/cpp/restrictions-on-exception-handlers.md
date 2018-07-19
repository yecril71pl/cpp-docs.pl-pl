---
title: Ograniczenia dotyczące obsługi wyjątków | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 13971ede3aef6d223b1c631c4a28f8bf190e7174
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37938786"
---
# <a name="restrictions-on-exception-handlers"></a>Ograniczenia dotyczące obsługi wyjątków
Główne ograniczenie używania programów obsługi wyjątków w kodzie jest, że nie można użyć **goto** instrukcję, aby przejść do **__try** blok instrukcji. Zamiast tego musisz wprowadzić blok instrukcji za pomocą Normalny przepływ sterowania. Możesz przejść z **__try** instrukcji zablokować, a także zagnieżdżać obsługi wyjątków, jak możesz wybrać.  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie programu do obsługi wyjątków](../cpp/writing-an-exception-handler.md)   
 [Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)