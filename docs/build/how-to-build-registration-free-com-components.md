---
title: 'Porady: kompilowanie komponentów COM bez rejestrowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1eaf9417f4d2b3b825933589556055772b84e057
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197416"
---
# <a name="how-to-build-registration-free-com-components"></a>Porady: kompilowanie komponentów COM bez rejestrowania
Bez rejestracji składników COM są składniki COM, które mają manifesty wbudowaną biblioteki dll.  
  
### <a name="to-build-manifests-into-com-components"></a>Aby skompilować manifesty w składników COM  
  
1.  Otwórz strony właściwości projektu dla składnika COM.  
  
2.  Rozwiń **właściwości konfiguracji** węzła, a następnie rozwiń węzeł **narzędziu manifestu** węzła.  
  
3.  Wybierz **danych wejściowych i wyjściowych** strony właściwości, a następnie ustaw **osadzanie manifestu** równa właściwości **tak**.  
  
4.  Kliknij przycisk **OK**.  
  
5.  Skompiluj rozwiązanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Aplikacje izolowane](/windows/desktop/SbsCs/isolated-applications)   
 [Informacje o zestawach Side-by-Side](/windows/desktop/SbsCs/about-side-by-side-assemblies-)   
 [Instrukcje: kompilowanie izolowanych aplikacji korzystających ze składników COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)