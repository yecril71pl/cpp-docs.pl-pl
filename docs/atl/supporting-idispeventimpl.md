---
title: "Obsługa IDispEventImpl | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDispEventImpl
dev_langs: C++
helpviewer_keywords:
- event sink maps, declaring
- IDispEventImpl class, advising and unadvising
- SINK_ENTRY macro
- type libraries, importing
- ATL, IDispEventImpl support in COM objects
- BEGIN_SINK_MAP macro
- IDispEventImpl class, declaring
ms.assetid: b957f930-6a5b-4598-8e4d-8027759957e7
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 81976652c14693c54980f6e0901f5db5576fbbe8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="supporting-idispeventimpl"></a>Obsługa IDispEventImpl
Klasy szablonów [IDispEventImpl](../atl/reference/idispeventimpl-class.md) może służyć do zapewnienia obsługi wychwytywanie punktu połączenia w klasie ATL. W zbiorniku punktu połączenia umożliwia klasy do obsługi zdarzenia wywoływane z zewnętrznych obiektów COM. Te wychwytywanie punktu połączenia są mapowane z mapą obiekt sink zdarzenia, pochodzącymi od swojej klasy.  
  
 Aby prawidłowo zaimplementować zbiorniku punktu połączenia dla klasy, musi wykonać następujące czynności:  
  
-   Importowanie biblioteki typów dla każdego obiektu zewnętrznego  
  
-   Deklarowanie `IDispEventImpl` interfejsów  
  
-   Deklarowanie mapy obiekt sink zdarzenia  
  
-   Powiadomienia i unadvise punkty połączenia  
  
 Etapy Implementowanie zbiornika punktu połączenia są realizowane przez zmodyfikowanie tylko plik nagłówka (.h) klasy.  
  
## <a name="importing-the-type-libraries"></a>Importowanie biblioteki typów  
 Dla każdego obiektu zewnętrznego do obsługi zdarzeń należy zaimportować bibliotekę typów. Ten krok definiuje zdarzenia, które są obsługiwane i udostępnia informacje, które jest używane podczas deklarowania map obiekt sink zdarzenia. [#Import](../preprocessor/hash-import-directive-cpp.md) w tym celu można użyć dyrektywy. Dodaj niezbędne `#import` dyrektywy wierszy dla każdego interfejsu wysyłania będzie obsługiwać do pliku nagłówka (.h) klasy.  
  
 Poniższy przykład importuje bibliotekę typów zewnętrznego serwera COM (`MSCAL.Calendar.7`):  
  
 [!code-cpp[NVC_ATL_Windowing#141](../atl/codesnippet/cpp/supporting-idispeventimpl_1.h)]  
  
> [!NOTE]
>  Musi działać oddzielny `#import` instrukcji dla każdej biblioteki typu zewnętrznego będzie obsługiwać.  
  
## <a name="declaring-the-idispeventimpl-interfaces"></a>Deklarowanie interfejsów IDispEventImpl  
 Zaimportowano biblioteki typów dla każdego interfejsu wysyłania, trzeba do deklarowania oddzielnych `IDispEventImpl` interfejsów dla każdego interfejsu wysyłania zewnętrznych. Modyfikowanie deklaracji klasy, dodając `IDispEventImpl` interfejsu deklaracji dla każdego obiektu zewnętrznego. Aby uzyskać więcej informacji o parametrach, zobacz [IDispEventImpl](../atl/reference/idispeventimpl-class.md).  
  
 Poniższy kod deklaruje dwóch sink punktu połączenia dla `DCalendarEvents` interfejsu dla obiektu COM zaimplementowany przez klasę `CMyCompositCtrl2`:  
  
 [!code-cpp[NVC_ATL_Windowing#142](../atl/codesnippet/cpp/supporting-idispeventimpl_2.h)]  
  
## <a name="declaring-an-event-sink-map"></a>Deklarowanie mapy obiekt Sink zdarzenia  
 Aby powiadomienia o zdarzeniach mają być obsługiwane przez funkcję właściwe klasy musi trasy każdego zdarzenia do jego obsługi poprawne. Jest to osiągane przez deklarowania map obiekt sink zdarzenia.  
  
 ATL udostępnia kilka makra [BEGIN_SINK_MAP](reference/composite-control-macros.md#begin_sink_map), [END_SINK_MAP](reference/composite-control-macros.md#end_sink_map), i [SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex), który ułatwić to mapowanie. Standardowy format jest następujący:  
  
 `BEGIN_SINK_MAP(comClass)`  
  
 `SINK_ENTRY_EX(id, iid, dispid, func)`  
  
 `. . . //additional external event entries`  
  
 `END_SINK_MAP()`  
  
 Poniższy przykład deklaruje Mapa obiekt sink zdarzenia z dwie procedury obsługi zdarzeń:  
  
 [!code-cpp[NVC_ATL_Windowing#136](../atl/codesnippet/cpp/supporting-idispeventimpl_3.h)]  
  
 Implementacja jest niemal ukończona. Ostatni krok dotyczy informacją i unadvising zewnętrznych interfejsów.  
  
## <a name="advising-and-unadvising-the-idispeventimpl-interfaces"></a>Udzielanie porad i Unadvising interfejsów IDispEventImpl  
 Ostatnim krokiem jest do implementacji metody, która będzie powiadomienia (lub unadvise) wszystkie punkty połączenia w odpowiednich momentach. Ta udzielanie porad należy wykonać przed komunikacji między klientami zewnętrznymi, a obiekt może mieć miejsce. Zanim obiekt staje się widoczna, każdy interfejs wysyłania zewnętrznych obsługiwane przez obiekt zostanie zapytany o interfejsy wychodzących. Jest nawiązywane połączenie, a odwołania do interfejsu wychodzącego jest używany do obsługi zdarzeń z obiektu. Ta procedura jest określany jako "udzielanie porad."  
  
 Po zakończeniu obiektu z zewnętrzne interfejsy interfejsy wychodzące powiadomienia nie są używane przez klasy. Ten proces jest nazywany "unadvising".  
  
 Ze względu na unikatowe charakter obiektów COM ta procedura różni się szczegółów i wykonanie, od implementacji. Te szczegóły wykraczają poza zakres tego tematu i nie zostały opisane.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje na temat ATL COM — obiekty](../atl/fundamentals-of-atl-com-objects.md)

