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
ms.openlocfilehash: 2cc85c7ca47d5d1226ffc3089e01c0755ef6c6ac
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850557"
---
# <a name="what-is-the-atl-control-hosting-api"></a>Co to jest ATL Hosting kontrolki interfejsu API?
ATL użytkownika hosting kontrolki interfejsu API to zestaw funkcji, który umożliwia dowolnym oknie jako kontener formantu ActiveX. Te funkcje mogą być statycznie lub dynamicznie połączone do projektu, ponieważ są one dostępne jako kod źródłowy i udostępnianych przez ATL90.dll. Funkcje hostingu kontrolek są wymienione w poniższej tabeli.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|Tworzy obiekt hosta, łączy się ono podane okna, a następnie dołącza istniejącej kontrolki.|  
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|Tworzy obiekt hosta, łączy się ono podane okna, a następnie ładuje formantu.|  
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|Tworzy licencjonowany formant ActiveX, inicjuje go i umieszcza w określonym oknie, podobnie jak [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol).|  
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|Tworzy obiekt hosta, łączy się ono podane okna, a następnie ładuje kontrolki (również pozwala wychwytywanie zdarzeń do skonfigurowania).|  
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|Tworzy licencjonowany formant ActiveX, inicjuje go i umieszcza w określonym oknie, podobnie jak [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic).|  
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|Tworzy niemodalne okno dialogowe z zasobu okna dialogowego i zwraca uchwyt okna.|  
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|Tworzy modalne okno dialogowe z zasobu okna dialogowego.|  
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|Zwraca `IUnknown` wskaźnika interfejsu tego formantu w oknie.|  
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|Zwraca `IUnknown` wskaźnika interfejsu tego obiektu hosta jest podłączony do okna.|  
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|Inicjuje kod hostingu formantu.|  
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|Deinicjuje kod hostingu formantu.|  
  
 `HWND` Parametrów w pierwszych trzech funkcji musi być istniejącym oknie (prawie) dowolnego typu. Jeśli dowolny z tych trzech funkcji jawnie wywołać (zazwyczaj nie trzeba), nie przekazuj dojścia do okna, która już działa jako host (Jeśli to zrobisz, istniejący obiekt hosta nie można zwolnić).  
  
 Wywołaj najpierw siedmiu funkcji [klasy AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) niejawnie.  
  
> [!NOTE]
>  Interfejs API hostingu kontrolek stanowi podstawę ATL obsługę zawierania kontrolek ActiveX. Istnieje jednak zwykle nieco trzeba bezpośrednio wywoływać tych funkcji, jeśli korzystanie z zalet lub wykorzystać ATL klasy otoki. Aby uzyskać więcej informacji, zobacz [której klasy ułatwienia ActiveX zawieranie kontrolek ATL](which-atl-classes-facilitate-activex-control-containment-q.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zawieranie kontrolek — często zadawane pytania](which-atl-classes-facilitate-activex-control-containment-q.md)
