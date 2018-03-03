---
title: "Ostrzeżenie prj0049 dotyczące kompilacji projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- PRJ0049
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f87bc7e26fd7cc50defbc086594c92a3ea339ef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-warning-prj0049"></a>Ostrzeżenie PRJ0049 dotyczące kompilacji projektu
Przywoływany docelowego "\<odwołania >" wymaga programu .NET Framework \<MinFrameworkVersion > i nie będzie można uruchamiać na platformę docelową tego projektu  
  
 Aplikacje utworzone przy użyciu programu Visual Studio 2008 można określić, która wersja [!INCLUDE[dnprdnshort](../../error-messages/tool-errors/includes/dnprdnshort_md.md)] powinny ich elementami docelowymi. Jeśli możesz dodać odwołania do zestawu lub projektu, który jest zależny od wersji [!INCLUDE[dnprdnshort](../../error-messages/tool-errors/includes/dnprdnshort_md.md)] jest nowsza niż wersja docelowa, wyświetlone zostanie ostrzeżenie w czasie kompilacji.  
  
### <a name="to-correct-this-warning"></a>Aby naprawić tego ostrzeżenia  
  
1.  Wybierz jedną z następujących opcji:  
  
    -   Zmień docelową platformę projektu **strony właściwości** okna dialogowego, dzięki czemu jest późniejsza lub taka sama do wersji framework minimalnego wszystkich przywoływanych zestawów i projektów. Aby uzyskać więcej informacji, zobacz [Dodawanie odwołań](../../ide/adding-references-in-visual-cpp-projects.md).  
  
    -   Usuń odwołanie do zestawu lub projekt, który ma minimalny framework w wersji, która jest nowsza niż docelową platformę. Te elementy zostaną oznaczone ikoną ostrzeżenia w projekcie **strony właściwości**.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy i ostrzeżenia kompilowania projektu (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)