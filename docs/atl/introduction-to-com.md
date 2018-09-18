---
title: Wprowadzenie do COM | Dokumentacja firmy Microsoft
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- COM
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a98c7bb473e36e53e8cbe0f90f9dd94f655392d6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073229"
---
# <a name="introduction-to-com"></a>Wprowadzenie do modelu COM

COM jest podstawowy "model obiektu", na które kontrolki ActiveX i OLE są tworzone. COM umożliwia obiektu do udostępnienia jej funkcjonalność do innych składników oraz obsługi aplikacji. Definiuje, jak obiekt udostępnia sam i działania to narażenie na różnych procesów i w całej sieci. COM definiuje również obiektu cyklu życia.

Podstawowe znaczenie dla modelu COM są te pojęcia:

- [Interfejsy](../atl/interfaces-atl.md) — mechanizm, za pomocą którego obiekt udostępnia funkcję.

- [IUnknown](../atl/iunknown.md) — podstawowy interfejs pozostałe oparte. Implementuje zliczaniu odwołań i interfejs zapytań mechanizmów uruchomiony za pomocą modelu COM.

- [Zliczanie odwołań](../atl/reference-counting.md) — technika, za pomocą którego obiektu (lub ściśle, interfejs) decyduje, gdy jest już używany i w związku z tym jest bezpłatna, można usunąć samego.

- [QueryInterface](../atl/queryinterface.md) — metoda umożliwia tworzenie zapytań dotyczących obiektu dla danego interfejsu.

- [Marshaling](../atl/marshaling.md) — mechanizm, który umożliwia użycie w wątku, procesy i granice sieci, co zapewnia niezależność od lokalizacji obiektów.

- [Agregacja](../atl/aggregation.md) — użycie innego sposobu, w którym można zmienić jeden obiekt.

## <a name="see-also"></a>Zobacz też

[Wprowadzenie do modelu COM i ATL](../atl/introduction-to-com-and-atl.md)<br/>
[Model Component Object Model](/windows/desktop/com/the-component-object-model)

