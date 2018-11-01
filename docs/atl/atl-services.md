---
title: Usługi ATL
ms.date: 11/04/2016
f1_keywords:
- CServiceModule
helpviewer_keywords:
- CServiceModule class
- COM objects, ATL
- services, ATL
- ATL services
ms.assetid: 8c09d1a8-7548-4d2c-947c-9d795a81659b
ms.openlocfilehash: 50a3eecf210cacc35cd80ad82da079b18c998c8b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456111"
---
# <a name="atl-services"></a>Usługi ATL

Aby utworzyć obiekt ATL COM, tak, aby była uruchamiana w ramach usługi, po prostu wybierz z listy opcji serwera w Kreatorze projektu ATL usługa (EXE). Kreator automatycznie utworzy klasę pochodną `CAtlServiceModuleT` wdrażania usługi.

Po utworzeniu obiektu ATL COM jako usługa będzie można rejestrować tylko jako serwera lokalnego, a nie pojawi się na liście usługi w Panelu sterowania. Jest to spowodowane ułatwia debugowanie usługi jako serwera lokalnego niż jako usługa. Aby zainstalować go jako usługę, uruchom następujące polecenie w wierszu polecenia:

`YourEXE``.exe /Service`

Aby odinstalować go, uruchom następujące polecenie:

`YourEXE``.exe /UnregServer`

Pierwsze cztery tematy w tej sekcji omówiono akcje, które występują podczas wykonywania `CAtlServiceModuleT` funkcji elementów członkowskich. Te tematy są wyświetlane w takiej samej kolejności jak funkcje są zwykle nazywane. Aby poprawić zrozumienie tych tematów, to dobry pomysł, aby użyć kodu źródłowego, generowane przez kreatora ATL projektu jako odwołania. Te tematy pierwsze cztery są:

- [Funkcja CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)

- [Funkcja CAtlServiceModuleT::ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)

- [Funkcja CAtlServiceModuleT::Run](../atl/reference/catlservicemodulet-class.md#run)

- [Funkcja CAtlServiceModuleT::Handler](../atl/reference/catlservicemodulet-class.md#handler)

Ostatnie trzy tematach opisano pojęcia związane z tworzenia usługi:

- [Wpisy rejestru](../atl/registry-entries.md) usługi ATL

- [DCOMCNFG](../atl/dcomcnfg.md)

- [Wskazówki dotyczące debugowania](../atl/debugging-tips.md) usługi ATL

## <a name="see-also"></a>Zobacz też

[Pojęcia](../atl/active-template-library-atl-concepts.md)

