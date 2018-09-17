---
title: 'Porady: kompilowanie izolowanych aplikacji korzystających ze składników COM | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d2acabb6a5e9c35029b346097a66eaf1311826c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704031"
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>Porady: kompilowanie izolowanych aplikacji korzystających ze składników COM

Aplikacje izolowane to aplikacje, które mają wbudowane w program manifestów. Można utworzyć izolowanych aplikacji korzystających ze składników COM.

### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>Aby dodać odwołania COM do manifestów aplikacji izolowanych

1. Otwórz strony właściwości projektu dla aplikacji izolowanych.

1. Rozwiń **właściwości konfiguracji** węzła, a następnie rozwiń węzeł **narzędziu manifestu** węzła.

1. Wybierz **COM izolowany** strony właściwości, a następnie ustaw **nazwa pliku komponentu** właściwość na nazwę składnik COM, który ma izolowane aplikacji używać.

1. Kliknij przycisk **OK**.

### <a name="to-build-manifests-into-isolated-applications"></a>Aby skompilować manifesty w aplikacje izolowane

1. Otwórz strony właściwości projektu dla aplikacji izolowanych.

1. Rozwiń **właściwości konfiguracji** węzła, a następnie rozwiń węzeł **narzędziu manifestu** węzła.

1. Wybierz **danych wejściowych i wyjściowych** strony właściwości, a następnie ustaw **osadzanie manifestu** równa właściwości **tak**.

1. Kliknij przycisk **OK**.

1. Skompiluj rozwiązanie.

## <a name="see-also"></a>Zobacz też

[Aplikacje izolowane](/windows/desktop/SbsCs/isolated-applications)<br/>
[Informacje o zestawach Side-by-Side](/windows/desktop/SbsCs/about-side-by-side-assemblies-)