---
title: COM + 1.0 pomocy technicznej w projektach ATL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.MTS
helpviewer_keywords:
- ATL projects, COM+ 1.0 support
ms.assetid: 51fb08ac-d632-4657-a4e0-d3f989f0b6f8
ms.openlocfilehash: 39a3597b8df833d89942e31b361f791b14ceb8c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62278478"
---
# <a name="com-10-support-in-atl-projects"></a>COM + 1.0 pomocy technicznej w projektach ATL

Możesz użyć [Kreator projektów ATL](../../atl/reference/creating-an-atl-project.md) Tworzenie projektu z podstawowej pomocy technicznej dla składników modelu COM + 1.0.

COM + 1.0 jest przeznaczona do tworzenia aplikacji rozproszonych oparty na komponentach. Wdrażanie i zarządzanie nimi te aplikacje są również zapewnia infrastrukturę czasu wykonywania.

Jeśli wybierzesz **Obsługa modelu COM + 1.0** pole wyboru, Kreator modyfikuje skryptu kompilacji w kroku łącza. W szczególności modelu COM + 1.0 projektu linki do następujących bibliotek:

- comsvcs.lib

- Mtxguid.lib

Jeśli wybierzesz **Obsługa modelu COM + 1.0** pole wyboru, możesz również wybrać **rejestratora składników obsługi**. Rejestratora składników umożliwia obiektu modelu COM + 1.0 listę składników, rejestrować składników lub wyrejestrować komponenty (pojedynczo lub wszystkie na raz).

## <a name="see-also"></a>Zobacz także

[Podstawowe informacje na temat obiektów COM ATL](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Programowanie za pomocą kodu ATL i C Run-Time](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Domyślne konfiguracje projektu ATL](../../atl/reference/default-atl-project-configurations.md)
