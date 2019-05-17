---
title: Pojęcia biblioteki Active Template Library (ALT)
ms.date: 05/06/2019
helpviewer_keywords:
- ATL, about ATL
ms.assetid: a3960991-4d76-4da5-9568-3fa7fde53ff4
ms.openlocfilehash: a7b6a40eaed05462f3aa5c877a1c4da3e19c0b03
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65836997"
---
# <a name="active-template-library-atl-concepts"></a>Pojęcia biblioteki Active Template Library (ALT)

Active Template Library (ATL) to zbiór opartych na szablonach klas języka C++, które pozwalają na tworzenie małych, szybkich obiektów Component Object Model (COM). Ma specjalne Obsługa kluczy funkcji COM, w tym implementacje magazynu, dwa interfejsy, standardowe interfejsy modułu wyliczającego COM, punkty połączenia, interfejsy odrywania i formantów ActiveX.

Jeśli zrobisz mnóstwo ATL programowania, można dowiedzieć się więcej na temat atrybutów COM i .NET, który upraszcza programowanie COM. Aby uzyskać więcej informacji, zobacz [programowania opartego na atrybutach](../windows/attributed-programming-concepts.md). (Atrybuty COM i .NET, to nie należy mylić z \[ \[atrybut]] są wyposażone w C++ standardowe.)

## <a name="in-this-section"></a>W tej sekcji

[Wprowadzenie do modelu COM i ATL](../atl/introduction-to-com-and-atl.md)<br/>
Wprowadza główne pojęcia za Component Object Model (COM). W tym artykule krótko opisano również ATL jest i kiedy należy go używać.

[Podstawowe informacje na temat obiektów COM ATL](../atl/fundamentals-of-atl-com-objects.md)<br/>
W tym artykule omówiono relacje między różnymi klasy ATL i implementacji tych klas.

[Podwójne interfejsy i ATL](../atl/dual-interfaces-and-atl.md)<br/>
W tym artykule opisano dwa interfejsy z perspektywy ATL.

[Kolekcje i wyliczenia ATL](../atl/atl-collections-and-enumerators.md)<br/>
W tym artykule opisano implementację i tworzenie kolekcje i wyliczenia w ATL.

[Podstawy złożonych kontrolek](../atl/atl-composite-control-fundamentals.md)<br/>
Instrukcje krok po kroku do tworzenia złożonych kontrolek. Kontrolki złożonej jest typem formantu ActiveX, który może zawierać inne kontrolki ActiveX lub formanty Windows.

[Zawieranie kontrolek ATL — często zadawane pytania](../atl/atl-control-containment-faq.md)<br/>
Obejmuje podstawowych kwestii związanych z hosting kontrolek za pomocą ATL.

[Strony właściwości ALT COM](../atl/atl-com-property-pages.md)<br/>
Pokazuje, jak określić i implementowanie strony właściwości COM.

[Obsługa ATL dla kontrolek DHTML](../atl/atl-support-for-dhtml-controls.md)<br/>
Instrukcje krok po kroku dotyczące tworzenia kontrolki DHTML.

[Punkty połączenia ATL](../atl/atl-connection-points.md)<br/>
Wyjaśnia, czym są punkty połączenia i ATL Implementowanie je.

[Obsługa zdarzeń i ATL](../atl/event-handling-and-atl.md)<br/>
W tym artykule opisano kroki, które należy wykonać w celu obsługi zdarzeń COM za pomocą ATL [IDispEventImpl](../atl/reference/idispeventimpl-class.md) i [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) klasy.

[ATL i organizator trybu wolnych wątków](../atl/atl-and-the-free-threaded-marshaler.md)<br/>
Zawiera szczegółowe informacje na temat opcji ATL prostego obiektu kreatora, umożliwiająca klasy agregacji marshaler trybu (programu FTM).

[Określanie modelu wątkowości projektu](../atl/specifying-the-threading-model-for-a-project-atl.md)<br/>
W tym artykule opisano makra, które są dostępne do kontrolowania wydajności w czasie wykonywania związanych z wątków w projekcie.

[Klasy modułów ATL](../atl/atl-module-classes.md)<br/>
W tym artykule omówiono nowe klasy modułów ATL 7.0. Klasy modułów implementuje podstawowe funkcje wymagane przez ATL.

[Usługi ATL](../atl/atl-services.md)<br/>
Obejmuje szereg zdarzeń, które występują, gdy usługa jest zaimplementowana. Również opowiada o niektóre pojęcia związane z tworzenia usługi.

[Klasy okien ATL](../atl/atl-window-classes.md)<br/>
W tym artykule opisano sposób tworzenia, superklasie i oknach podklasy ATL. Klasy okien ATL nie są klasy COM.

[Kolekcje klas ATL](../atl/atl-collection-classes.md)<br/>
Opisuje sposób używania tablic i mapy w ATL.

[Składnik rejestru Alt (Rejestrator)](../atl/atl-registry-component-registrar.md)<br/>
W tym artykule omówiono ATL skryptów składnię i parametry wymienne. Wyjaśniono także, jak Konfigurowanie statycznego linku do rejestratora.

[Programowanie za pomocą kodu ATL i C Run-Time](../atl/programming-with-atl-and-c-run-time-code.md)<br/>
W tym artykule omówiono zalety łączenia statycznie lub dynamicznie do biblioteki wykonawczej C (CRT).

[Programowanie przy użyciu CComBSTR](../atl/programming-with-ccombstr-atl.md)<br/>
W tym artykule omówiono kilka sytuacji, które wymagają ostrożność podczas programowania przy użyciu `CComBSTR`.

[Odwołanie kodowania](../atl/atl-encoding-reference.md)<br/>
Udostępnia funkcje i makra, które obsługuje kodowania w szereg typowych standardy internetowe, takie jak uuencode szesnastkową i UTF8 w atlenc.h.

[Odwołanie do narzędzi](../atl/atl-utilities-reference.md)<br/>
Zawiera kod do manipulowania ścieżek i adresów URL w postaci [CPathT](../atl/reference/cpatht-class.md) i [CUrl](../atl/reference/curl-class.md). Z puli wątków [CThreadPool](../atl/reference/cthreadpool-class.md), mogą być używane we własnych aplikacjach. Ten kod można znaleźć w atlpath.h i atlutil.h.

## <a name="related-sections"></a>Sekcje pokrewne

[ALT — samouczek](../atl/active-template-library-atl-tutorial.md)<br/>
Poprowadzi Cię przez tworzenie formantu i pokazuje podstawowe informacje dotyczące niektórych ATL w procesie.

[Przykłady ATL](../overview/visual-cpp-samples.md)<br/>
Zawiera opisy i linki do przykładowych programów ATL.

[Tworzenie projektu ATL](../atl/reference/creating-an-atl-project.md)<br/>
Zawiera informacje na temat Kreator projektów ATL.

[Kreator kontrolki ATL](../atl/reference/atl-control-wizard.md)<br/>
W tym artykule omówiono sposób dodawania klasy.

[Programowanie oparte na atrybutach](../windows/attributed-programming-concepts.md)<br/>
Zawiera omówienie na przy użyciu atrybutów, aby uprościć programowanie COM plus listę łącza do bardziej szczegółowych tematów.

[Przegląd klas ATL](../atl/atl-class-overview.md)<br/>
Zawiera informacje i łącza do klas ATL.
