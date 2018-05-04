---
title: Klasy modułów ALT | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 777d81fbe1de48289863fda00591a5328b40cf4c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="atl-module-classes"></a>Klasy modułów ALT
W tym temacie omówiono klasy modułów, które były nowe ATL 7.0.  
  
## <a name="ccommodule-replacement-classes"></a>Ccommodule — zastąpienie klas  
 Starsze niż ATL używane `CComModule`. 7.0 ATL `CComModule` funkcje zostały zastąpione przez kilka klas:  
  
-   [CAtlBaseModule](../atl/reference/catlbasemodule-class.md) zawiera informacje wymagane przez większość aplikacji, które używają ATL. Zawiera wystąpienie HINSTANCE modułu i wystąpienia zasobu.  
  
-   [CAtlComModule](../atl/reference/catlcommodule-class.md) zawiera informacje wymagane przez klasy COM w ATL.  
  
-   [CAtlWinModule](../atl/reference/catlwinmodule-class.md) zawiera informacje wymagane przez klasy okien w ATL.  
  
-   [CAtlDebugInterfacesModule](../atl/reference/catldebuginterfacesmodule-class.md) zawiera obsługę debugowania interfejsu.  
  
-   [CAtlModule](../atl/reference/catlmodule-class.md) następujące `CAtlModule`-klas pochodnych są dostosowane do zawierają informacje wymagane w typie określonej aplikacji. Większość elementów członkowskich w tych klas może zostać zastąpiona:  
  
    -   [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) używany w aplikacjach biblioteki DLL. Zawiera kod standardowe eksportu.  
  
    -   [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) używany w aplikacjach EXE. Zawiera kod wymagany w pliku EXE.  
  
    -   [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md) zapewnia obsługę tworzenia systemu Windows NT i usług systemu Windows 2000.  
  
 `CComModule` jest wciąż dostępna na potrzeby zgodności z poprzednimi wersjami.  
  
## <a name="reasons-for-distributing-ccommodule-functionality"></a>Ze względu na potrzeby rozpowszechnienia ccommodule — funkcja  
 Funkcje `CComModule` został wydany w kilku nowe klasy z następujących powodów:  
  
-   Utworzyć funkcji w `CComModule` szczegółowego.  
  
     Obsługa modelu COM, okien interfejsu debugowania i funkcje specyficzne dla aplikacji (plik DLL lub EXE) znajduje się w osobnych klas.  
  
-   Automatycznie Zadeklaruj globalne wystąpienie tych modułów.  
  
     Globalne wystąpienie klasy modułu wymagane jest połączony z projektem.  
  
-   Usuń konieczność podczas wywoływania metody Init i terminu.  
  
     Metody init i termin zostały przeniesione do konstruktory i destruktory dla klas modułu; nie ma potrzeby wywołanie Init i termin.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../atl/active-template-library-atl-concepts.md)   
 [Przegląd klas](../atl/atl-class-overview.md)

