---
title: Wprowadzenie do modelu COM
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- COM
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
ms.openlocfilehash: 7631ba98b0e2cb00310400206b0b442ab7a23dd7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262375"
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

## <a name="see-also"></a>Zobacz także

[Wprowadzenie do modelu COM i ATL](../atl/introduction-to-com-and-atl.md)<br/>
[Model Component Object Model](/windows/desktop/com/the-component-object-model)
