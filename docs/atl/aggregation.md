---
title: Agregacji
ms.date: 11/04/2016
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
ms.openlocfilehash: 2eec7a801f9fe16bc48fc888d10ce413ec7e79db
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265434"
---
# <a name="aggregation"></a>Agregacji

Istnieją terminy, gdy obiekt implementujący chcesz korzystać z usług oferowanych przez inną, wstępnie utworzonym obiekt. Ponadto chcesz ten drugi obiekt do są wyświetlane jako fizyczną część pierwsza. COM osiąga obu tych celów poprzez zawierania i agregacji.

Agregacja oznacza, że zawierającego go obiektu (zewnętrznego) tworzy zawartego w nim obiektu (wewnętrzny) w ramach procesu tworzenia i interfejsy obiekt wewnętrzny są udostępniane przez zewnętrzny. Obiekt umożliwia sam można było agregować, czy nie. Jeśli tak jest, należy go wykonać niektóre zasady w celu agregacji zapewnić prawidłowe działanie.

Przede wszystkim wszystkie `IUnknown` wywołania metody na przechowywany obiekt musi delegować do obiektu zawierającego.

## <a name="see-also"></a>Zobacz także

[Wprowadzenie do modelu COM](../atl/introduction-to-com.md)<br/>
[Ponowne używanie obiektów](/windows/desktop/com/reusing-objects)
