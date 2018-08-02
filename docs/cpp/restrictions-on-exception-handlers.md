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
ms.openlocfilehash: 8775f752a541d2a250e9c1c5a0c325b684335988
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464603"
---
# <a name="restrictions-on-exception-handlers"></a>Ograniczenia dotyczące obsługi wyjątków
Główne ograniczenie używania programów obsługi wyjątków w kodzie jest, że nie można użyć **goto** instrukcję, aby przejść do **__try** blok instrukcji. Zamiast tego musisz wprowadzić blok instrukcji za pomocą Normalny przepływ sterowania. Możesz przejść z **__try** instrukcji zablokować, a także zagnieżdżać obsługi wyjątków, jak możesz wybrać.  
  
## <a name="see-also"></a>Zobacz także  
 [Pisanie programu do obsługi wyjątków](../cpp/writing-an-exception-handler.md)   
 [Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)