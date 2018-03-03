---
title: "Porady: Tworzenie składników COM bez rejestrowania | Dokumentacja firmy Microsoft"
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
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 018a3ba707f4c5cff73b5a5c54f82400a79a8d46
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-build-registration-free-com-components"></a>Porady: kompilowanie komponentów COM bez rejestrowania
Składniki COM bez rejestrowania są składniki COM, które mają manifestów wbudowane bibliotek DLL.  
  
### <a name="to-build-manifests-into-com-components"></a>Aby utworzyć manifestów do składników COM  
  
1.  Otwieranie stron właściwości projektu dla składnika modelu COM.  
  
2.  Rozwiń węzeł **właściwości konfiguracji** węzeł, a następnie rozwiń węzeł **narzędziu manifestu** węzła.  
  
3.  Wybierz **wejściowa i wyjściowa** strony właściwości, a następnie ustawić **Osadź Manifest** równa właściwości **tak**.  
  
4.  Kliknij przycisk **OK**.  
  
5.  Skompiluj rozwiązanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Aplikacje izolowane](http://msdn.microsoft.com/library/aa375190)   
 [Informacje o zestawach Side-by-Side](http://msdn.microsoft.com/library/ff951640)   
 [Instrukcje: kompilowanie izolowanych aplikacji korzystających ze składników COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)