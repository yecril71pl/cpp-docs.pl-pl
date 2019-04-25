---
title: 'Instrukcje: Kompilowanie komponentów COM bez rejestrowania'
ms.date: 11/04/2016
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
ms.openlocfilehash: 783677c97835acc98751fc4a19f9405af752b71a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188941"
---
# <a name="how-to-build-registration-free-com-components"></a>Instrukcje: Kompilowanie komponentów COM bez rejestrowania

Bez rejestracji składników COM są składniki COM, które mają manifesty wbudowaną biblioteki dll.

### <a name="to-build-manifests-into-com-components"></a>Aby skompilować manifesty w składników COM

1. Otwórz strony właściwości projektu dla składnika COM.

1. Rozwiń **właściwości konfiguracji** węzła, a następnie rozwiń węzeł **narzędziu manifestu** węzła.

1. Wybierz **danych wejściowych i wyjściowych** strony właściwości, a następnie ustaw **osadzanie manifestu** równa właściwości **tak**.

1. Kliknij przycisk **OK**.

1. Skompiluj rozwiązanie.

## <a name="see-also"></a>Zobacz także

[Instrukcje: kompilowanie izolowanych aplikacji korzystających ze składników COM](how-to-build-isolated-applications-to-consume-com-components.md)
