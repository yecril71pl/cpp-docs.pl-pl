---
title: Pisanie programu obsługi wyjątku | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structured exception handling [C++], exception handlers
- exception handling [C++], exception handlers
ms.assetid: 71473fee-f773-4a34-bf12-82a3af79579c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bb06c23e17f16bdf33fe469327351105d6a4571c
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461052"
---
# <a name="writing-an-exception-handler"></a>Pisanie programu do obsługi wyjątku
Programy obsługi wyjątków są zwykle używane w odpowiedzi dla określonych błędów. Składnia obsługi wyjątków można użyć, aby odfiltrować wszystkie wyjątki inne niż te wiedzieć jak je obsługiwać. Inne wyjątki powinien zostać przekazany do innych programów obsługi (prawdopodobnie w bibliotece wykonawczej lub systemu operacyjnego) zapisywane do wyszukania tych określonych wyjątków.  
  
 Programy obsługi wyjątków używać instrukcji try-except, instrukcja.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?  
  
-   [Try-except — instrukcja](../cpp/try-except-statement.md)  
  
-   [Pisanie filtra wyjątku](../cpp/writing-an-exception-filter.md)  
  
-   [Występowanie wyjątków programowych](../cpp/raising-software-exceptions.md)  
  
-   [Wyjątki sprzętowe](../cpp/hardware-exceptions.md)  
  
-   [Ograniczenia dotyczące obsługi wyjątków](../cpp/restrictions-on-exception-handlers.md)  
  
## <a name="see-also"></a>Zobacz także  
 [Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)