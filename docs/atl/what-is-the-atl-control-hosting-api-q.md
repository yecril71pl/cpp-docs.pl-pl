---
title: Co to jest ATL Hosting kontrolki interfejsu API? | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- APIs [C++], hosting
- control-hosting API
- controls [ATL], hosting APIs
ms.assetid: 75b27e45-cfba-4950-aa35-96cc7d8da753
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 30b104e21259006da41c236c168431d85b43e0d4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363249"
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
