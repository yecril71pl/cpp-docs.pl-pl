---
title: Klasy modułów ALT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CComModule class, what's changed
- ATL, module classes
- module classes
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b254edfe75cfcdaee7ab15351f7c05c3d163e301
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
  
 `CComModule`jest wciąż dostępna na potrzeby zgodności z poprzednimi wersjami.  
  
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

