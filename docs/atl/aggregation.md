---
title: Agregacja
ms.date: 11/04/2016
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
ms.openlocfilehash: 288af427bd6a8d9baf572dfad8e4a25452694ad9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491982"
---
# <a name="aggregation"></a>Agregacja

Istnieją przypadki, w których implementujący obiekt chce skorzystać z usług oferowanych przez inny, wstępnie skonstruowany obiekt. Ponadto chcemy, aby ten drugi obiekt pojawił się jako naturalna część pierwszego. COM realizuje oba te cele za poorednictwem zawierania i agregacji.

Agregacja oznacza, że obiekt zawierający (zewnętrzny) tworzy zawarty obiekt (wewnętrzny) jako część procesu tworzenia, a interfejsy obiektu wewnętrznego są uwidaczniane przez zewnętrzny. Obiekt umożliwia możliwość agregowania. Jeśli tak, to musi przestrzegać pewnych reguł, aby agregacja działała prawidłowo.

Przede wszystkim wywołania metody na zawartym obiekcie muszą delegować do obiektu zawierającego. `IUnknown`

## <a name="see-also"></a>Zobacz także

[Wprowadzenie do modelu COM](../atl/introduction-to-com.md)<br/>
[Używanie obiektów](/windows/win32/com/reusing-objects)
