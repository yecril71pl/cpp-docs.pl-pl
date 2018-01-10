---
title: "Makra i język C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- macros, C++
- macros
ms.assetid: 83a344c1-73c9-4ace-8b93-cccfb62c6133
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7af092d31fb4495be47c88aaaf8830cc05db2bc7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="macros-and-c"></a>Makra i język C++
C++ oferuje nowe możliwości, niektóre z nich ograniczyć te udostępniane przez preprocesora C ANSI. Te nowe funkcje zwiększyć bezpieczeństwo typów i przewidywalności języka:  
  
-   W języku C++ obiektów zadeklarowany jako **const** można używać w wyrażeniach stałej. Dzięki temu programy, aby zadeklarować stałe, które mają typ i wartość informacji i wyliczenia, które mogą być wyświetlane symbolicznie z debugera. Przy użyciu preprocesora `#define` dyrektywy do definiowania stałe nie jest dokładnych. Brak magazynu przypisany do **const** obiektów, chyba że wyrażenie, które ma adres znajduje się w programie.  
  
-   Możliwości funkcji wbudowanej C++ otrzymuje makra typu funkcji. Zalety korzystania z funkcji śródwierszowych za pośrednictwem makra są:  
  
    -   Bezpieczeństwo typu. Funkcje śródwierszowe podlegają ten sam typ sprawdzenia jako normalnej pracy. Makra nie są bezpieczne dla typu.  
  
    -   Usuń obsługę argumenty, które ma efekty uboczne. Funkcje śródwierszowe obliczać wyrażeń, podana jako argumenty przed wprowadzeniem treści funkcji. Dlatego nie jest bez możliwości, że wyrażenie z efektami ubocznymi będzie niebezpieczne.  
  
 Aby uzyskać więcej informacji o funkcji śródwierszowych, zobacz [w tekście, __inline, \__forceinline](../cpp/inline-functions-cpp.md).  
  
 W celu zapewnienia zgodności z poprzednimi wersjami wszystkich preprocesora urządzeń istniejących w ANSI C i C++ specyfikacjach wcześniejszych zostaną zachowane dla Microsoft C++.  
  
## <a name="see-also"></a>Zobacz też  
 [Wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md)   
 [Makra (C/C++)](../preprocessor/macros-c-cpp.md)