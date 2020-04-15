---
title: Obsługa interfejsu IDispEventImpl
ms.date: 11/04/2016
helpviewer_keywords:
- event sink maps, declaring
- IDispEventImpl class, advising and unadvising
- SINK_ENTRY macro
- type libraries, importing
- ATL, IDispEventImpl support in COM objects
- BEGIN_SINK_MAP macro
- IDispEventImpl class, declaring
ms.assetid: b957f930-6a5b-4598-8e4d-8027759957e7
ms.openlocfilehash: 31beff30a067416f71029c18051f214c8d4429de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329323"
---
# <a name="supporting-idispeventimpl"></a>Obsługa interfejsu IDispEventImpl

Klasa [szablonu IDispEventImpl](../atl/reference/idispeventimpl-class.md) może służyć do zapewnienia obsługi pochłaniaczy punktów połączenia w klasie ATL. Ujście punktu połączenia umożliwia klasie do obsługi zdarzeń uruchamianych z zewnętrznych obiektów COM. Te ujścia punktów połączenia są mapowane z mapą ujścia zdarzeń, dostarczone przez klasę.

Aby prawidłowo zaimplementować ujście punktu połączenia dla klasy, należy wykonać następujące kroki:

- Importowanie bibliotek typów dla każdego obiektu zewnętrznego

- Deklarowanie `IDispEventImpl` interfejsów

- Deklarowanie mapy ujścia zdarzeń

- Doradzanie i odłączanie przyłączy

Kroki związane z implementacji ujścia punktu połączenia są realizowane przez modyfikowanie tylko pliku nagłówka (.h) klasy.

## <a name="importing-the-type-libraries"></a>Importowanie bibliotek typów

Dla każdego obiektu zewnętrznego, którego zdarzenia chcesz obsłużyć, należy zaimportować bibliotekę typów. Ten krok definiuje zdarzenia, które mogą być obsługiwane i zawiera informacje, które są używane podczas deklarowania mapy ujścia zdarzeń. Do osiągnięcia tego celu można wykorzystać [dyrektywę #import.](../preprocessor/hash-import-directive-cpp.md) Dodaj niezbędne `#import` wiersze dyrektywy dla każdego interfejsu wysyłki, który będzie obsługiwany do pliku nagłówka (.h) klasy.

Poniższy przykład importuje bibliotekę typów zewnętrznego`MSCAL.Calendar.7`serwera COM ( ):

[!code-cpp[NVC_ATL_Windowing#141](../atl/codesnippet/cpp/supporting-idispeventimpl_1.h)]

> [!NOTE]
> Musisz mieć osobną `#import` instrukcję dla każdej biblioteki typów zewnętrznych, które będą obsługiwane.

## <a name="declaring-the-idispeventimpl-interfaces"></a>Deklarowanie interfejsów IDispEventImpl

Teraz, gdy zostały zaimportowane biblioteki typów każdego interfejsu `IDispEventImpl` wysyłki, należy zadeklarować oddzielne interfejsy dla każdego zewnętrznego interfejsu wysyłki. Zmodyfikuj deklarację `IDispEventImpl` klasy, dodając deklarację interfejsu dla każdego obiektu zewnętrznego. Aby uzyskać więcej informacji na temat parametrów, zobacz [IDispEventImpl](../atl/reference/idispeventimpl-class.md).

Poniższy kod deklaruje dwa ujścia punktu `DCalendarEvents` połączenia dla interfejsu dla obiektu `CMyCompositCtrl2`COM zaimplementowanego przez klasę:

[!code-cpp[NVC_ATL_Windowing#142](../atl/codesnippet/cpp/supporting-idispeventimpl_2.h)]

## <a name="declaring-an-event-sink-map"></a>Deklarowanie mapy ujścia zdarzeń

Aby powiadomienia o zdarzeniach były obsługiwane przez właściwą funkcję, klasa musi kierować każde zdarzenie do jego poprawnego programu obsługi. Osiąga się to poprzez zadeklarowanie mapy ujścia zdarzeń.

ATL udostępnia kilka makr, [BEGIN_SINK_MAP,](reference/composite-control-macros.md#begin_sink_map) [END_SINK_MAP](reference/composite-control-macros.md#end_sink_map)i [SINK_ENTRY_EX,](reference/composite-control-macros.md#sink_entry_ex)które ułatwiają to mapowanie. Standardowy format jest następujący:

```cpp
BEGIN_SINK_MAP(comClass)
  SINK_ENTRY_EX(id, iid, dispid, func)
  . . . //additional external event entries
END_SINK_MAP()
```

W poniższym przykładzie deklaruje mapę ujścia zdarzeń z dwoma programami obsługi zdarzeń:

[!code-cpp[NVC_ATL_Windowing#136](../atl/codesnippet/cpp/supporting-idispeventimpl_3.h)]

Implementacja jest prawie zakończona. Ostatni krok dotyczy doradztwa i nienadzorowania interfejsów zewnętrznych.

## <a name="advising-and-unadvising-the-idispeventimpl-interfaces"></a>Doradztwo i unadvising IDispEventImpl Interfejsy

Ostatnim krokiem jest wdrożenie metody, która będzie doradzać (lub unadvise) wszystkie punkty połączenia w odpowiednim czasie. To doradztwo musi być wykonane przed komunikacją między klientami zewnętrznymi a obiektem. Zanim obiekt stanie się widoczny, każdy interfejs wysyłki zewnętrznej obsługiwany przez obiekt jest wyszukiwany dla interfejsów wychodzących. Połączenie jest ustanawiane i odwołanie do interfejsu wychodzącego jest używany do obsługi zdarzeń z obiektu. Procedura ta jest określana jako "doradztwo".

Po zakończeniu obiektu za pomocą interfejsów zewnętrznych interfejsów wychodzących powinny być powiadamiane, że nie są już używane przez klasę. Proces ten jest określany jako "unadvising".

Ze względu na unikatowy charakter obiektów COM ta procedura różni się szczegółowo i wykonanie między implementacjami. Te szczegóły wykraczają poza zakres tego tematu i nie są adresowane.

## <a name="see-also"></a>Zobacz też

[Podstawy obiektów ATL COM](../atl/fundamentals-of-atl-com-objects.md)
