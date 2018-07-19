---
title: Ograniczenia funkcji Main | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Main
dev_langs:
- C++
helpviewer_keywords:
- main function, restrictions on using
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3114f1ef379495f36f4231dbad6fd41ac145bcfe
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941749"
---
# <a name="main-function-restrictions"></a>Ograniczenia funkcji main
Kilku ograniczeniom `main` funkcji, które nie mają zastosowanie do innych funkcji w języku C++. `main` Funkcji:  
  
-   Nie mogą być przeciążone (zobacz [przeciążanie funkcji](function-overloading.md)).  
  
-   Nie można zadeklarować jako **wbudowane**.  
  
-   Nie można zadeklarować jako **statyczne**.  
  
-   Nie można jej adres miały.  
  
-   Nie można wywołać.  
  
## <a name="see-also"></a>Zobacz też  
 [main: uruchamianie programu](../cpp/main-program-startup.md)