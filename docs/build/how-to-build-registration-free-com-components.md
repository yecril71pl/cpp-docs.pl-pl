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
ms.openlocfilehash: e0a9e1769ff0ba9a0589f9d59c3d1f1ed2fc5bcb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699858"
---
# <a name="how-to-build-registration-free-com-components"></a>Porady: kompilowanie komponentów COM bez rejestrowania

Bez rejestracji składników COM są składniki COM, które mają manifesty wbudowaną biblioteki dll.

### <a name="to-build-manifests-into-com-components"></a>Aby skompilować manifesty w składników COM

1. Otwórz strony właściwości projektu dla składnika COM.

1. Rozwiń **właściwości konfiguracji** węzła, a następnie rozwiń węzeł **narzędziu manifestu** węzła.

1. Wybierz **danych wejściowych i wyjściowych** strony właściwości, a następnie ustaw **osadzanie manifestu** równa właściwości **tak**.

1. Kliknij przycisk **OK**.

1. Skompiluj rozwiązanie.

## <a name="see-also"></a>Zobacz też

[Aplikacje izolowane](/windows/desktop/SbsCs/isolated-applications)<br/>
[Informacje o zestawach Side-by-Side](/windows/desktop/SbsCs/about-side-by-side-assemblies-)<br/>
[Instrukcje: kompilowanie izolowanych aplikacji korzystających ze składników COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)