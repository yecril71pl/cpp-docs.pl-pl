---
title: COM + 1.0 pomocy technicznej w projektach ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.MTS
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, COM+ 1.0 support
ms.assetid: 51fb08ac-d632-4657-a4e0-d3f989f0b6f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 64046eab403dca8da630c9c5324d320e0c79d4cc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054301"
---
# <a name="com-10-support-in-atl-projects"></a>COM + 1.0 pomocy technicznej w projektach ATL

Możesz użyć [Kreator projektów ATL](../../atl/reference/creating-an-atl-project.md) Tworzenie projektu z podstawowej pomocy technicznej dla składników modelu COM + 1.0.

COM + 1.0 jest przeznaczona do tworzenia aplikacji rozproszonych oparty na komponentach. Wdrażanie i zarządzanie nimi te aplikacje są również zapewnia infrastrukturę czasu wykonywania.

Jeśli wybierzesz **Obsługa modelu COM + 1.0** pole wyboru, Kreator modyfikuje skryptu kompilacji w kroku łącza. W szczególności modelu COM + 1.0 projektu linki do następujących bibliotek:

- Comsvcs.lib

- Mtxguid.lib

Jeśli wybierzesz **Obsługa modelu COM + 1.0** pole wyboru, możesz również wybrać **rejestratora składników obsługi**. Rejestratora składników umożliwia obiektu modelu COM + 1.0 listę składników, rejestrować składników lub wyrejestrować komponenty (pojedynczo lub wszystkie na raz).

## <a name="see-also"></a>Zobacz też

[Podstawowe informacje na temat obiektów COM ATL](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Programowanie za pomocą kodu ATL i C Run-Time](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Domyślne konfiguracje projektu ATL](../../atl/reference/default-atl-project-configurations.md)

