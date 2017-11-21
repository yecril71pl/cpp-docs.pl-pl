---
title: Co to jest ATL Hosting kontrolki interfejsu API? | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- APIs [C++], hosting
- control-hosting API
- controls [ATL], hosting APIs
ms.assetid: 75b27e45-cfba-4950-aa35-96cc7d8da753
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4f04f5caa30ab860634f0f96ae18e9da03577ba2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="what-is-the-atl-control-hosting-api"></a>Co to jest ATL Hosting kontrolki interfejsu API?
ATL obiektu hosting kontrolki interfejsu API jest zestaw funkcji, które pozwalają dowolnego okna do działania jako kontenera formantu ActiveX. Funkcje te mogą być statycznie lub dynamicznie połączony do projektu, ponieważ są one dostępne jako kodu źródłowego i udostępniane przez ATL90.dll. Hosting kontrolki funkcje są wymienione w poniższej tabeli.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|Tworzy obiekt hosta, nawiązanie dostarczony okna, a następnie dołącza formant.|  
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|Tworzy obiekt hosta, nawiązanie dostarczony okna, a następnie ładuje formantu.|  
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|Tworzy licencjonowanego formantu ActiveX, inicjowane i znajduje się w określonym okna, podobnie jak [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol).|  
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|Tworzy obiekt hosta, nawiązanie dostarczony okna, a następnie ładuje formantu (umożliwia także można skonfigurować wychwytywanie zdarzeń).|  
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|Tworzy licencjonowanego formantu ActiveX, inicjowane i znajduje się w określonym okna, podobnie jak [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic).|  
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|Tworzy niemodalne okno dialogowe z zasobu okna dialogowego i zwraca uchwytu okna.|  
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|Tworzy modalne okno dialogowe z zasobu okna dialogowego.|  
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|Zwraca **IUnknown** wskaźnika interfejsu formantu hostowanej w oknie.|  
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|Zwraca **IUnknown** wskaźnika interfejsu obiektu hosta jest podłączony do okna.|  
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|Inicjuje kodu hosting kontrolki.|  
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|Uninitializes kod hosting kontrolki.|  
  
 `HWND` Parametrów w pierwszych trzech funkcji musi być istniejącego okna (prawie) dowolnego typu. Jeśli dowolne z tych trzech funkcji jawnie wywołana (zazwyczaj nie trzeba), nie są przekazywane uchwyt okna już działający jako host (Jeśli to zrobisz, istniejącego obiektu hosta nie można zwolnić).  
  
 Wywołaj najpierw siedmiu funkcji [AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) niejawnie.  
  
> [!NOTE]
>  Hosting kontrolki interfejsu API stanowi podstawę na ATL obsługę zawierania formantów ActiveX. Istnieje jednak zwykle małego należy bezpośrednio wywoływać te funkcje, jeśli pełni korzystać z klasy otoki dla biblioteki ATL lub korzystać z. Aby uzyskać więcej informacji, zobacz [które klasy ułatwienia ActiveX zawieranie kontrolek ALT](which-atl-classes-facilitate-activex-control-containment-q.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zawierania kontrolek — często zadawane pytania](which-atl-classes-facilitate-activex-control-containment-q.md)
