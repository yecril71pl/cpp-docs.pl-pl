---
title: 'Porady: kompilowanie komponentów COM bez rejestrowania'
ms.date: 11/04/2016
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
ms.openlocfilehash: 4f4ebf121b761c37969fa3f9788bda52d913f340
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463534"
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