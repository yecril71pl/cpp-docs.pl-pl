---
title: "Pojęcia dotyczące programu Active Template Library (ATL) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: ATL, about ATL
ms.assetid: a3960991-4d76-4da5-9568-3fa7fde53ff4
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 01bd114c92b7056ead29b57c70801d2cbbacb554
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="active-template-library-atl-concepts"></a>Pojęcia biblioteki Active Template Library (ALT)
Active Template Library (ATL) to zestaw na podstawie szablonu klasy C++, które pozwalają tworzyć małe, szybkie obiekty składnika modelu COM (Object). Ma specjalną obsługę dla klucza funkcji COM, w tym implementacje standardowych, podwójne interfejsy standardowe interfejsy modułu wyliczającego COM, punkty połączenia, oderwania interfejsów i formantów ActiveX.  
  
 Czy partii ATL programowania, należy dowiedzieć się więcej o atrybuty, nowa funkcja programu Visual C++ .NET, zaprojektowana w celu uproszczenia programowania COM. Aby uzyskać więcej informacji, zobacz [programowania opartego na atrybutach](../windows/attributed-programming-concepts.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [ALT — samouczek](../atl/active-template-library-atl-tutorial.md)  
 Poprowadzi Cię przez tworzenie formantu i przedstawiono niektóre podstawowe założenia ATL w procesie.  
  
 [Wprowadzenie do COM i ATL](../atl/introduction-to-com-and-atl.md)  
 Pojęcia związane z głównych za składnika modelu COM (Object). W tym artykule krótko opisano również jest ATL i kiedy należy go używać.  
  
 [Podstawowe informacje na temat ATL COM — obiekty](../atl/fundamentals-of-atl-com-objects.md)  
 W tym artykule omówiono relacje między różnymi klasami ATL i implementowania tych klas.  
  
 [Podwójne interfejsy i ATL](../atl/dual-interfaces-and-atl.md)  
 W tym artykule opisano dwa interfejsy z perspektywy ATL.  
  
 [Kolekcje i wyliczenia ATL](../atl/atl-collections-and-enumerators.md)  
 W tym artykule opisano implementacji i tworzenie kolekcje i wyliczenia w ATL.  
  
 [Podstawy złożonych kontrolek](../atl/atl-composite-control-fundamentals.md)  
 Zawiera instrukcje krok po kroku dotyczące tworzenia złożonych kontrolek. Formantu złożonego jest typem formantu ActiveX, który może zawierać inne kontrolki ActiveX lub formantów systemu Windows.  
  
 [Zawieranie kontrolek ALT — często zadawane pytania](../atl/atl-control-containment-faq.md)  
 Obejmuje podstawowych kwestii związanych z hosting formantów za pomocą ATL.  
  
 [Strony właściwości Alt COM](../atl/atl-com-property-pages.md)  
 Pokazuje, jak określać i implementować strony właściwości COM.  
  
 [Obsługa ALT dla DHTML — formanty](../atl/atl-support-for-dhtml-controls.md)  
 Instrukcje krok po kroku do tworzenia kontrolek DHTML.  
  
 [Punkty połączenia ATL](../atl/atl-connection-points.md)  
 Wyjaśniono, co to są punkty połączenia i jak ATL implementuje je.  
  
 [Obsługa zdarzeń i ATL](../atl/event-handling-and-atl.md)  
 W tym artykule opisano kroki, które należy wykonać w celu obsługi zdarzeń COM za pomocą biblioteki ATL dla [IDispEventImpl](../atl/reference/idispeventimpl-class.md) i [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) klasy.  
  
 [ATL i Marshaler trybu wolnych wątków](../atl/atl-and-the-free-threaded-marshaler.md)  
 Zawiera szczegółowe informacje na opcję ATL prosty obiekt kreatora, umożliwiającą klasy agregacji Organizator trybu wolnych wątków (FTM).  
  
 [Określanie modelu wątkowości projektu](../atl/specifying-the-threading-model-for-a-project-atl.md)  
 W tym artykule opisano makra, które są dostępne do kontrolowania wydajności w czasie wykonywania związanych z wątków w projekcie.  
  
 [Klasy modułów ALT](../atl/atl-module-classes.md)  
 Omówiono nowe klasy modułów ALT 7.0. Klasy modułów implementacji podstawowych funkcji wymaganych przez ATL.  
  
 [Usługi ATL](../atl/atl-services.md)  
 Omówiono szereg zdarzeń występujących w przypadku wdrożenia usługi. Ponadto omówiono niektóre założenia dotyczące tworzenia usługi.  
  
 [Klasy okien ALT](../atl/atl-window-classes.md)  
 Opisuje sposób tworzenia, superklasy i podklasy okna w ATL. Klasy okien ALT nie są klasy COM.  
  
 [Klasy kolekcji ATL](../atl/atl-collection-classes.md)  
 Informacje dotyczące używania tablic, a następnie mapuje w ATL.  
  
 [Składnik rejestru Alt (Rejestrator)](../atl/atl-registry-component-registrar.md)  
 W tym artykule omówiono ATL skryptów składnia i parametry wymienne. Wyjaśniono również, jak skonfigurować statyczne łącze do rejestratora.  
  
 [Programowanie za pomocą ALT i C Run-Time kodu](../atl/programming-with-atl-and-c-run-time-code.md)  
 W tym artykule omówiono korzyści wynikające z łączenia statycznie lub dynamicznie do biblioteki wykonawcze języka C (CRT).  
  
 [Programowanie przy użyciu CComBSTR](../atl/programming-with-ccombstr-atl.md)  
 W tym artykule omówiono kilku sytuacjach wymagających ostrożność podczas programowania z `CComBSTR`.  
  
 [Odwołanie kodowania](../atl/atl-encoding-reference.md)  
 Udostępnia funkcje i obsługa kodowania w szereg typowych standardy internetowe, takie jak uuencode szesnastkowych i UTF8 w atlenc.h makr.  
  
 [Odwołanie do narzędzi](../atl/atl-utilities-reference.md)  
 Udostępnia kod do manipulowania adresy URL i ścieżki w formie [CPathT](../atl/reference/cpatht-class.md) i [CUrl](../atl/reference/curl-class.md). Puli wątków [CThreadPool](../atl/reference/cthreadpool-class.md), mogą być używane w aplikacjach. Ten kod znajduje się w atlpath.h i atlutil.h.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [ATL — przykłady](../visual-cpp-samples.md)  
 Zawiera opisy i linki do ATL przykładowe programy.  
  
 [Tworzenie projektu ATL](../atl/reference/creating-an-atl-project.md)  
 Zawiera informacje dotyczące Kreator projektu ATL.  
  
 [Kreator formantu ATL](../atl/reference/atl-control-wizard.md)  
 W tym artykule omówiono sposób dodać klasy.  
  
 [Programowanie oparte na atrybutach](../windows/attributed-programming-concepts.md)  
 Zawiera omówienie na upraszczają programowanie COM plus listę łącza do bardziej szczegółowych tematów za pomocą atrybutów.  
  
 [Przegląd klasy ATL](../atl/atl-class-overview.md)  
 Zawiera informacje i linki do klasy ATL.

