---
title: Klasy modułów ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CComModule class, what's changed
- ATL, module classes
- module classes
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e067b1d72b80950b4ed33fbae8cac7333ac0438
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083079"
---
# <a name="atl-module-classes"></a>Klasy modułów ALT

W tym temacie omówiono klasy modułu, które wprowadzono nowe ATL 7.0.

## <a name="ccommodule-replacement-classes"></a>Ccommodule — zastąpienie klas

Wcześniejszych wersjach ATL używane `CComModule`. W wersji 7.0 ATL `CComModule` funkcje zostały zastąpione przez kilka klas:

- [CAtlBaseModule](../atl/reference/catlbasemodule-class.md) zawiera informacje wymagane przez większość aplikacji, które używają ATL. Zawiera HINSTANCE moduł i wystąpienia zasobów.

- [CAtlComModule](../atl/reference/catlcommodule-class.md) zawiera informacje wymagane przez klasy modelu COM w ATL.

- [CAtlWinModule](../atl/reference/catlwinmodule-class.md) zawiera informacje wymagane przez klasy obsługi okien w ATL.

- [CAtlDebugInterfacesModule](../atl/reference/catldebuginterfacesmodule-class.md) zawiera obsługę debugowania interfejsu.

- [CAtlModule](../atl/reference/catlmodule-class.md) następujące `CAtlModule`-klas pochodnych są dostosowane do zawierają informacje wymagane w typie określonej aplikacji. Większość elementów członkowskich w ramach tych zajęć, może zostać przesłonięta:

   - [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) używanych w aplikacjach biblioteki DLL. Zawiera kod eksportu standardowego.

   - [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) używanych w aplikacjach EXE. Zawiera kod jest wymagany w pliku EXE.

   - [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md) zapewnia obsługę tworzenia systemu Windows NT i Windows 2000 usług.

`CComModule` jest wciąż dostępna na potrzeby zgodności z poprzednimi wersjami.

## <a name="reasons-for-distributing-ccommodule-functionality"></a>Powody dystrybucja ccommodule — funkcja

Funkcje `CComModule` została dystrybuowana do kilku nowych klas z następujących powodów:

- Wprowadź funkcji w `CComModule` szczegółowe.

   Obsługa modelu COM, obsługi okien, debugowanie interfejsu i funkcje specyficzne dla aplikacji (plik DLL lub EXE) znajduje się w osobnych klas.

- Automatycznie deklarują globalnego wystąpienia każdej z tych modułów.

   Globalne wystąpienie klasy wymaganych modułów jest połączony z projektem.

- Usuń konieczność wywoływania metody Init i czas trwania.

   Metody init i czas trwania zostały przeniesione do konstruktory i destruktory klas modułu; nie ma już konieczności wywołać Init i czas trwania.

## <a name="see-also"></a>Zobacz też

[Pojęcia](../atl/active-template-library-atl-concepts.md)<br/>
[Klasa — Przegląd](../atl/atl-class-overview.md)

