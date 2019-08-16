---
title: Wprowadzenie do modelu COM
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- COM
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
ms.openlocfilehash: e29f761e0380357bc999af82cc4bde8bfbaf4d6e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492358"
---
# <a name="introduction-to-com"></a>Wprowadzenie do modelu COM

COM to podstawowy "model obiektów", na którym są zbudowane kontrolki ActiveX i OLE. Model COM umożliwia obiektowi uwidocznienie jego funkcjonalności innym składnikom i hostowanie aplikacji. Definiuje zarówno sposób ujawniania obiektu, jak i sposób działania tego narażenia między procesami i sieciami. Model COM definiuje również cykl życia obiektu.

Podstawowe dla modelu COM są następujące pojęcia:

- [Interfejsy](../atl/interfaces-atl.md) — mechanizm, za pomocą którego obiekt uwidacznia jego funkcjonalność.

- [IUnknown](../atl/iunknown.md) — podstawowy interfejs, na którym bazują wszystkie inne. Implementuje zliczanie odwołań i mechanizmy zapytań interfejsu uruchomione za pomocą COM.

- [Zliczanie odwołań](../atl/reference-counting.md) — technika, za pomocą której obiekt (lub, ściśle, interfejs) decyduje, gdy nie jest już używany, i dlatego jest bezpłatny do samodzielnego usuwania.

- [QueryInterface](../atl/queryinterface.md) — Metoda używana do wykonywania zapytań względem obiektu dla danego interfejsu.

- [Kierowanie](../atl/marshaling.md) — mechanizm, który umożliwia obiekty, które mają być używane w granicach wątków, procesów i sieci, co zapewnia niezależność lokalizacji.

- [Agregacja](../atl/aggregation.md) — sposób, w jaki jeden obiekt może korzystać z innego.

## <a name="see-also"></a>Zobacz także

[Wprowadzenie do modelu COM i ATL](../atl/introduction-to-com-and-atl.md)<br/>
[Component Object Model](/windows/win32/com/the-component-object-model)
