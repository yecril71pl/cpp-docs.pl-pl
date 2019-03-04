---
title: Obsługa interfejsu IDispEventImpl
ms.date: 11/04/2016
f1_keywords:
- IDispEventImpl
helpviewer_keywords:
- event sink maps, declaring
- IDispEventImpl class, advising and unadvising
- SINK_ENTRY macro
- type libraries, importing
- ATL, IDispEventImpl support in COM objects
- BEGIN_SINK_MAP macro
- IDispEventImpl class, declaring
ms.assetid: b957f930-6a5b-4598-8e4d-8027759957e7
ms.openlocfilehash: fcc3be5d905bf3f5680902e2f480472c6251aa7f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273819"
---
# <a name="supporting-idispeventimpl"></a>Obsługa interfejsu IDispEventImpl

Klasa szablonu [IDispEventImpl](../atl/reference/idispeventimpl-class.md) może służyć do zapewnienia obsługi ujścia punktu połączenia w klasie ATL. Obiekt sink punktu połączenia umożliwia klasy do obsługi zdarzeń wyzwalanych z zewnętrznych obiektów COM. Te obiekty sink punktu połączenia są mapowane z mapą obiekt sink zdarzenia dostarczane przez klasy.

Aby prawidłowo zaimplementować ujście punkt połączenia dla swojej klasy, być wykonywane następujące czynności:

- Importowanie biblioteki typów dla każdego obiektu zewnętrznego

- Zadeklaruj `IDispEventImpl` interfejsów

- Zadeklaruj mapę ujścia zdarzeń

- Powiadomienia i unadvise punkty połączenia

Etapy implementacji ujścia punktu połączenia są realizowane przez zmodyfikowanie tylko pliku nagłówka (.h) klasy.

## <a name="importing-the-type-libraries"></a>Importowanie bibliotek typów

Dla każdego obiektu zewnętrznego do obsługi zdarzeń należy zaimportować bibliotekę typów. Ten krok określa zdarzenia, które są obsługiwane i zawiera informacje, które jest używane podczas deklarowania Mapa ujścia zdarzeń. [#Import](../preprocessor/hash-import-directive-cpp.md) dyrektywy można to osiągnąć. Dodaj niezbędne `#import` dyrektywy wierszy dla każdego interfejs ekspedycji będzie obsługiwać do pliku nagłówka (.h) klasy.

Następujący przykład importuje biblioteki typów z zewnętrznego serwera COM (`MSCAL.Calendar.7`):

[!code-cpp[NVC_ATL_Windowing#141](../atl/codesnippet/cpp/supporting-idispeventimpl_1.h)]

> [!NOTE]
>  Konieczne jest posiadanie oddzielnego `#import` instrukcji dla każdego zewnętrzną bibliotekę typów będzie obsługiwać.

## <a name="declaring-the-idispeventimpl-interfaces"></a>Deklarowanie interfejsów interfejsu IDispEventImpl

Po zaimportowaniu type libraries każdy interfejs ekspedycji należy zadeklarować oddzielnych `IDispEventImpl` interfejsy, dla każdego interfejsu, wysyłania zewnętrznych. Zmodyfikuj deklarację klasy, dodając `IDispEventImpl` interfejsu deklarację dla każdego obiektu zewnętrznego. Aby uzyskać więcej informacji na temat parametrów, zobacz [IDispEventImpl](../atl/reference/idispeventimpl-class.md).

Poniższy kod deklaruje dwie sink punktu połączenia dla `DCalendarEvents` interfejs dla obiektu COM, zaimplementowany przez klasę `CMyCompositCtrl2`:

[!code-cpp[NVC_ATL_Windowing#142](../atl/codesnippet/cpp/supporting-idispeventimpl_2.h)]

## <a name="declaring-an-event-sink-map"></a>Deklarowanie mapę ujścia zdarzeń

Aby powiadomienia o zdarzeniach mają być obsługiwane przez funkcję właściwe klasa musi kierować każdego zdarzenia do jego prawidłowe procedury obsługi. Jest to osiągane przez zadeklarowanie mapę ujścia zdarzeń.

ATL udostępnia kilka makra [BEGIN_SINK_MAP](reference/composite-control-macros.md#begin_sink_map), [END_SINK_MAP](reference/composite-control-macros.md#end_sink_map), i [SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex), który ułatwić tego mapowania. Standardowy format jest następujący:

```cpp
BEGIN_SINK_MAP(comClass)
  SINK_ENTRY_EX(id, iid, dispid, func)
  . . . //additional external event entries
END_SINK_MAP()
```

Poniższy przykład deklaruje mapę ujścia zdarzeń za pomocą dwóch programów obsługi zdarzeń:

[!code-cpp[NVC_ATL_Windowing#136](../atl/codesnippet/cpp/supporting-idispeventimpl_3.h)]

Implementacja jest prawie gotowy. Ostatni krok dotyczy informacją i unadvising zewnętrznych interfejsów.

## <a name="advising-and-unadvising-the-idispeventimpl-interfaces"></a>Doradztwa i Unadvising interfejsów interfejsu IDispEventImpl

Ostatnim krokiem jest zaimplementować metodę, która będzie wykonać funkcji advise (lub unadvise) wszystkie punkty połączenia w czasie właściwe. Tego wniosku musi odbywać się przed komunikacji między klientami zewnętrznymi i obiekt może mieć miejsce. Zanim obiekt staje się widoczny, każdy interfejs zewnętrzny wysyłania obsługiwane przez obiekt zostaje przesłane zapytanie wychodzących interfejsów. Połączenie jest nawiązywane i odwołanie do interfejsu wychodzącego jest używana do obsługi zdarzeń z obiektu. Ta procedura jest nazywana "wniosku."

Po zakończeniu obiektu za pomocą zewnętrzne interfejsy interfejsów wychodzące powiadomienia, czy są one już używane przez klasy. Ten proces jest nazywany "unadvising".

Ze względu na unikatowy charakter obiektów COM ta procedura różni się w szczegóły i wykonanie, między implementacjami. Te szczegółowe informacje wykraczają poza zakres tego tematu i nie zostały opisane.

## <a name="see-also"></a>Zobacz także

[Podstawowe informacje na temat obiektów COM ATL](../atl/fundamentals-of-atl-com-objects.md)
