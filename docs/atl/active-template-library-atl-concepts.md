---
title: Pojęcia biblioteki Active Template Library (ALT)
ms.date: 05/06/2019
helpviewer_keywords:
- ATL, about ATL
ms.assetid: a3960991-4d76-4da5-9568-3fa7fde53ff4
ms.openlocfilehash: cc96b5ed931713ca64a0582ca1cc18a8526ea8af
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616684"
---
# <a name="active-template-library-atl-concepts"></a>Pojęcia biblioteki Active Template Library (ALT)

Active Template Library (ATL) to zestaw klas C++ opartych na szablonach, które umożliwiają tworzenie małych i szybkich obiektów Component Object Model (COM). Ma ona specjalne wsparcie dla kluczowych funkcji COM, w tym implementacje giełdowe, podwójne interfejsy, standardowe interfejsy modułu wyliczającego COM, punkty połączeń, interfejsy odrywające i formanty ActiveX.

W przypadku korzystania z wielu programów ATL można dowiedzieć się więcej na temat atrybutów COM i .NET, które mają na celu uproszczenie programowania obiektów COM. Aby uzyskać więcej informacji, zobacz [programowanie z atrybutami](../windows/attributed-programming-concepts.md). (Atrybuty COM i .NET nie należy mylić z \[ \[ atrybut]] funkcja w standardzie C++.)

## <a name="in-this-section"></a>W tej sekcji

[Wprowadzenie do modelu COM i ATL](introduction-to-com-and-atl.md)<br/>
Wprowadza najważniejsze pojęcia związane z Component Object Model (COM). W tym artykule krótko opisano, co ATL jest i kiedy należy z niego korzystać.

[Podstawowe informacje o obiektach COM ATL](fundamentals-of-atl-com-objects.md)<br/>
Omawia relacje między różnymi klasami ATL i sposobem implementacji tych klas.

[Podwójne interfejsy i ATL](dual-interfaces-and-atl.md)<br/>
Opisuje dwa interfejsy z perspektywy ATL.

[Kolekcje i moduły wyliczające ATL](atl-collections-and-enumerators.md)<br/>
Opisuje implementację i tworzenie kolekcji oraz modułów wyliczających w ATL.

[Podstawy kontroli złożonej](atl-composite-control-fundamentals.md)<br/>
Zawiera instrukcje krok po kroku dotyczące tworzenia kontrolki złożonej. Formant złożony jest typem kontrolki ActiveX, która może zawierać inne kontrolki ActiveX lub formanty systemu Windows.

[Zawiera często zadawane pytania dotyczące kontrolki ATL](atl-control-containment-faq.md)<br/>
Obejmuje podstawowe pytania związane z kontrolkami hostingu z ATL.

[Strony właściwości ATL COM](atl-com-property-pages.md)<br/>
Pokazuje, jak określać i implementować strony właściwości COM.

[Obsługa ALT dla kontrolek DHTML](atl-support-for-dhtml-controls.md)<br/>
Zawiera instrukcje krok po kroku dotyczące tworzenia kontrolki DHTML.

[Punkty połączenia ATL](atl-connection-points.md)<br/>
Wyjaśnia, które punkty połączenia są i jak są implementowane przez ATL.

[Obsługa zdarzeń i ATL](event-handling-and-atl.md)<br/>
Zawiera opis czynności, które należy wykonać, aby obsługiwać zdarzenia COM przy użyciu klas [IDispEventImpl](reference/idispeventimpl-class.md) i [IDispEventSimpleImpl](reference/idispeventsimpleimpl-class.md) ATL.

[ATL i organizator trybu wolnych wątków](atl-and-the-free-threaded-marshaler.md)<br/>
Zawiera szczegółowe informacje na temat opcji Kreatora prostych obiektów ATL, która umożliwia klasy agregowanie organizatora wolnych wątków (FTM).

[Określanie modelu wątkowości projektu](specifying-the-threading-model-for-a-project-atl.md)<br/>
Opisuje makra, które są dostępne do kontrolowania wydajności czasu wykonywania związanego z wątkiem w projekcie.

[Klasy modułów ALT](atl-module-classes.md)<br/>
Omawia klasy modułów nowość dla ATL 7,0. Klasy modułów implementują podstawowe funkcje wymagane przez ATL.

[Usługi ATL](atl-services.md)<br/>
Obejmuje serię zdarzeń występujących podczas implementacji usługi. Ponadto nastąpi kilka koncepcji związanych z tworzeniem usługi.

[Klasy okien ATL](atl-window-classes.md)<br/>
Opisuje sposób tworzenia, superklasy i podklas systemu Windows w ATL. Klasy okien ATL nie są klasami COM.

[Klasy kolekcji ATL](atl-collection-classes.md)<br/>
Opisuje sposób używania tablic i map w ATL.

[Składnik rejestru ATL (Rejestrator)](atl-registry-component-registrar.md)<br/>
Omawia składnię skryptów ATL i parametry wymienne. Wyjaśniono również, jak skonfigurować łącze statyczne do rejestratora.

[Programowanie za pomocą kodu ATL i C Run-Time](programming-with-atl-and-c-run-time-code.md)<br/>
W tym artykule omówiono zalety łączenia statycznie lub dynamicznie z biblioteką wykonawczą C (CRT).

[Programowanie przy użyciu CComBSTR](programming-with-ccombstr-atl.md)<br/>
Omawia kilka sytuacji, w których należy zachować ostrożność podczas programowania w programie `CComBSTR` .

[Odwołanie do kodowania](atl-encoding-reference.md)<br/>
Program udostępnia funkcje i makra, które obsługują kodowanie w wielu typowych standardach internetowych, takich jak UUENCODE, szesnastkowe i UTF8, w atlenc. h.

[Dokumentacja narzędzi](atl-utilities-reference.md)<br/>
Zawiera kod służący do manipulowania ścieżkami i adresami URL w postaci [CPathT](reference/cpatht-class.md) i [zwinięcie](reference/curl-class.md). Puli wątków [CThreadPool](reference/cthreadpool-class.md)można używać we własnych aplikacjach. Ten kod można znaleźć w atlpath. h i atlutil. h.

## <a name="related-sections"></a>Sekcje pokrewne

[Samouczek ATL](active-template-library-atl-tutorial.md)<br/>
Poprowadzi Cię przez proces tworzenia kontrolki i pokazuje niektóre podstawowe informacje o ATL w procesie.

[Przykłady ATL](../overview/visual-cpp-samples.md)<br/>
Zawiera opisy i linki do przykładowych programów ATL.

[Tworzenie projektu ATL](reference/creating-an-atl-project.md)<br/>
Zawiera informacje na temat Kreatora projektu ATL.

[Kreator kontrolki ATL](reference/atl-control-wizard.md)<br/>
W tym artykule omówiono sposób dodawania klas.

[Programowanie w atrybutach](../windows/attributed-programming-concepts.md)<br/>
Zawiera omówienie używania atrybutów do uproszczenia programowania COM oraz listę linków do bardziej szczegółowych tematów.

[Omówienie klasy ATL](atl-class-overview.md)<br/>
Zawiera informacje referencyjne i linki do klas ATL.
