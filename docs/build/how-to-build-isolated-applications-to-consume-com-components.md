---
title: "Porady: kompilowanie izolowanych aplikacji korzystających ze składników COM | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aaeef56f122d10f983313ab1c839db40f4e92aa4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>Porady: kompilowanie izolowanych aplikacji korzystających ze składników COM
Aplikacje izolowane są aplikacje, które mają wbudowane w program manifestów. Można utworzyć izolowanych aplikacji korzystających ze składników COM.  
  
### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>Aby dodać odwołań COM do manifestów aplikacje izolowane  
  
1.  Otwórz projekt strony właściwości dla aplikacji izolowanych.  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzeł, a następnie rozwiń węzeł **narzędziu manifestu** węzła.  
  
3.  Wybierz **izolowanego COM** strony właściwości, a następnie ustawić **nazwę pliku składnika** dla właściwości nazwy składnika modelu COM, interesujące izolowanych aplikacji używać.  
  
4.  Kliknij przycisk **OK**.  
  
### <a name="to-build-manifests-into-isolated-applications"></a>Aby utworzyć manifesty w izolowanych aplikacji  
  
1.  Otwórz projekt strony właściwości dla aplikacji izolowanych.  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzeł, a następnie rozwiń węzeł **narzędziu manifestu** węzła.  
  
3.  Wybierz **wejściowa i wyjściowa** strony właściwości, a następnie ustawić **Osadź Manifest** równa właściwości **tak**.  
  
4.  Kliknij przycisk **OK**.  
  
5.  Skompiluj rozwiązanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Aplikacje izolowane](http://msdn.microsoft.com/library/aa375190)   
 [Informacje o zestawach Side-by-Side](http://msdn.microsoft.com/library/ff951640)