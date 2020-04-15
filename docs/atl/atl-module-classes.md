---
title: Klasy modułów ALT
ms.date: 11/04/2016
helpviewer_keywords:
- CComModule class, what's changed
- ATL, module classes
- module classes
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
ms.openlocfilehash: 2b72cac0da06b70a40e01fcc75da52f1678f3f64
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317372"
---
# <a name="atl-module-classes"></a>Klasy modułów ALT

W tym temacie omówiono klasy modułu, które były nowe w ATL 7.0.

## <a name="ccommodule-replacement-classes"></a>Klasy wymiany CComModule

Wcześniejsze wersje ATL `CComModule`używane . W ATL 7.0 `CComModule` funkcjonalność jest zastępowana przez kilka klas:

- [CAtlBaseModule](../atl/reference/catlbasemodule-class.md) Zawiera informacje wymagane przez większość aplikacji korzystających z atl. Zawiera hinstance modułu i wystąpienia zasobu.

- [CAtlComModule ( CAtlComModule )](../atl/reference/catlcommodule-class.md) Zawiera informacje wymagane przez klasy COM w ATL.

- [CAtlWinModule](../atl/reference/catlwinmodule-class.md) Zawiera informacje wymagane przez klasy okien w ATL.

- [CAtlDebugInterfacesModule](../atl/reference/catldebuginterfacesmodule-class.md) Zawiera obsługę debugowania interfejsu.

- [CAtlModule](../atl/reference/catlmodule-class.md) Następujące `CAtlModule`klasy pochodne są dostosowywane do informacji wymaganych w określonym typie aplikacji. Większość członków w tych klasach może zostać zastąpiona:

  - [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) Używane w aplikacjach DLL. Zawiera kod dla eksportu standardowego.

  - [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) Używany w aplikacjach EXE. Zawiera kod wymagany w exe.

  - [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md) Zapewnia obsługę tworzenia usług Windows NT i Windows 2000.

`CComModule`jest nadal dostępna dla zgodności z powrotem.

## <a name="reasons-for-distributing-ccommodule-functionality"></a>Powody dystrybucji funkcji CComModule

Funkcjonalność `CComModule` została rozdzielona na kilka nowych klas z następujących powodów:

- Upewnij się, `CComModule` że funkcjonalność w ziarniste.

   Obsługa funkcji COM, windowing, debugowania interfejsu i specyficznych dla aplikacji (DLL lub EXE) jest teraz w oddzielnych klasach.

- Automatycznie deklaruj globalne wystąpienie każdego z tych modułów.

   Globalne wystąpienie wymaganych klas modułów jest połączone z projektem.

- Usuń konieczność wywoływania metod Init i Term.

   Metody Init i Term zostały przeniesione do konstruktorów i destruktorów dla klas modułów; nie ma już potrzeby wywoływania Init i Term.

## <a name="see-also"></a>Zobacz też

[Pojęcia](../atl/active-template-library-atl-concepts.md)<br/>
[Przegląd klas](../atl/atl-class-overview.md)
