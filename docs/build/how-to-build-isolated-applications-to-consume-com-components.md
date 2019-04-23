---
title: 'Instrukcje: Kompilowanie izolowanych aplikacji korzystających ze składników COM'
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
ms.openlocfilehash: 01b5c7056bd10a7c1f88df74b5c6b4aa78ff3fde
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417882"
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>Instrukcje: Kompilowanie izolowanych aplikacji korzystających ze składników COM

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

## <a name="see-also"></a>Zobacz także

[Aplikacje izolowane](/windows/desktop/SbsCs/isolated-applications)<br/>
[Informacje o zestawach Side-by-Side](/windows/desktop/SbsCs/about-side-by-side-assemblies-)
