---
title: "Biblioteka szablonów C++ środowiska wykonawczego systemu Windows (WRL) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: b915afce-553b-44a7-b8dc-0ab601758eb0
caps.latest.revision: "32"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e742b5509fd9a7889321e5e8c576e4fa3c8401cd
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="windows-runtime-c-template-library-wrl"></a>Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows (WRL)
Zestaw Windows środowiska uruchomieniowego C++ szablonu biblioteki (WRL) jest Biblioteka szablonów, które niskiego poziomu umożliwia tworzenie i używanie składnika środowiska wykonawczego systemu Windows.  
  
## <a name="benefits"></a>Zalety  
 Biblioteka szablonów C++ środowiska wykonawczego systemu Windows pozwala na łatwiejsze wdrożenia i zużywać składniki modelu COM (Component Object). Zapewnia celów technik, takich jak liczenie odwołań do zarządzania okres istnienia obiektów i testowania `HRESULT` wartości, aby ustalić, czy operacja powiodła się, czy nie. Aby pomyślnie korzystać Biblioteka szablonów C++ środowiska wykonawczego systemu Windows, należy wykonać dokładnie te reguły i technik.  
  
 C + +/ CX jest wysokiego poziomu, opartych na języku sposobem użycia składników środowiska wykonawczego systemu Windows. Biblioteka szablonów C++ środowiska wykonawczego systemu Windows i C + +/ CX uprościć pisanie kodu dla środowiska uruchomieniowego systemu Windows przez automatyczne wykonywanie zadań celów w Twoim imieniu.  
  
 Biblioteka szablonów C++ środowiska wykonawczego systemu Windows i C + +/ CX zapewniają różne korzyści. Poniżej przedstawiono przyczyny, które możesz chcieć użyć Biblioteka szablonów C++ środowiska wykonawczego systemu Windows zamiast C + +/ CX:  
  
-   Biblioteka szablonów C++ środowiska wykonawczego systemu Windows dodaje małego abstrakcji za pośrednictwem systemu Windows Runtime aplikacji binarny interfejsu (ABI), umożliwiając możliwość kontrolowania podstawowy kod, aby lepiej utworzyć lub korzystanie z interfejsów API środowiska wykonawczego systemu Windows.  
  
-   C + +/ CX reprezentuje COM `HRESULT` wartości jako wyjątki. Jeśli określona ścieżka bazowa kodu korzystającą z modelu COM lub taki, który nie korzysta z wyjątków już dziedziczone, może się okazać, że biblioteka szablonów C++ środowiska wykonawczego systemu Windows jest bardziej naturalny sposób pracy z środowiska uruchomieniowego systemu Windows, ponieważ nie trzeba używać wyjątków.  
  
    > [!NOTE]
    >  Biblioteka szablonów C++ środowiska wykonawczego systemu Windows używa `HRESULT` wartości i nie zgłaszają wyjątki. Ponadto Biblioteka szablonów C++ środowiska wykonawczego systemu Windows używa wskaźniki inteligentne i wzorzec RAII w celu zagwarantowania, że obiekty zostały zniszczone prawidłowo po kodzie aplikacji zgłasza wyjątek. Aby uzyskać więcej informacji na temat wskaźniki inteligentne i RAII, zobacz [wskaźniki inteligentne](../cpp/smart-pointers-modern-cpp.md) i [obiektów własnych zasoby (RAII)](../cpp/objects-own-resources-raii.md).  
  
-   Cel i projektowania Biblioteka szablonów C++ środowiska wykonawczego systemu Windows jest podstawą przez ATL Active Template Library (), czyli zestawowi oparte na szablonach klas C++, które upraszczają programowanie obiektów COM. Ponieważ biblioteka szablonów C++ środowiska wykonawczego systemu Windows używa standardu C++ do opakowywania środowiska uruchomieniowego systemu Windows, można łatwiej portu i interakcję z wielu istniejących składników COM napisany w ATL do środowiska wykonawczego systemu Windows. Jeśli znasz już ATL, może się okazać, że programowania Biblioteka szablonów C++ środowiska wykonawczego systemu Windows jest łatwiejsze.  
  
## <a name="getting-started"></a>Wprowadzenie  
 Poniżej przedstawiono niektóre zasoby, które ułatwiają uzyskiwanie od razu Praca z Biblioteka szablonów C++ środowiska wykonawczego systemu Windows.  
  
 [Biblioteka środowiska uruchomieniowego systemu Windows (WRL)](http://channel9.msdn.com/Events/Windows-Camp/Developing-Windows-8-Metro-style-apps-in-Cpp/The-Windows-Runtime-Library-WRL-)  
 To wideo z witryny Channel 9 Dowiedz się więcej o tym, jak Biblioteka szablonów C++ środowiska wykonawczego systemu Windows pomaga pisania aplikacji platformy uniwersalnej systemu Windows oraz jak tworzyć i zużywać składników środowiska wykonawczego systemu Windows.  
  
 [Porady: uaktywnianie składnika środowiska wykonawczego systemu Windows i korzystanie](../windows/how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)  
 Przedstawia sposób użycia Biblioteka szablonów C++ środowiska wykonawczego systemu Windows, aby zainicjować środowiska uruchomieniowego systemu Windows i aktywować i używają składnika środowiska wykonawczego systemu Windows.  
  
 [Porady: wykonywanie operacji asynchronicznych](../windows/how-to-complete-asynchronous-operations-using-wrl.md)  
 Przedstawia sposób użycia Biblioteka szablonów C++ środowiska wykonawczego systemu Windows, aby uruchomić operacji asynchronicznych i wykonywania pracy po ukończeniu operacji.  
  
 [Porady: Obsługa zdarzeń](../windows/how-to-handle-events-using-wrl.md)  
 Przedstawia sposób użycia Biblioteka szablonów C++ środowiska wykonawczego systemu Windows, aby subskrybować usługę i obsługi zdarzeń obiektu środowiska wykonawczego systemu Windows.  
  
 [Wskazówki: Tworzenie składnika środowiska wykonawczego podstawowa systemu Windows](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md)  
 Przedstawia sposób umożliwia tworzenie podstawowego składnika środowiska wykonawczego systemu Windows, która dodaje dwie liczby Biblioteka szablonów C++ środowiska wykonawczego systemu Windows. Także przedstawiono sposób wywołania zdarzeń składnika i korzystanie z aplikacji platformy uniwersalnej systemu Windows, który używa języka JavaScript.  
  
 [Przewodnik: tworzenie aplikacji sklepu Windows Store z użyciem biblioteki WRL i platformy Media Foundation](../windows/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation.md)  
 Informacje o sposobie tworzenia aplikacji platformy uniwersalnej systemu Windows, który używa [Microsoft Media Foundation](http://msdn.microsoft.com/library/windows/apps/ms694197).  
  
 [Porady: tworzenie klasycznego składnika COM](../windows/how-to-create-a-classic-com-component-using-wrl.md)  
 Przedstawia sposób użycia Biblioteka szablonów C++ środowiska wykonawczego systemu Windows, aby utworzyć podstawowy składnik modelu COM i najprostszy sposób rejestrowania i zużywać składnik modelu COM z pulpitu aplikacji.  
  
 [Instrukcje: bezpośrednie tworzenie wystąpień składników biblioteki WRL](../windows/how-to-instantiate-wrl-components-directly.md)  
 Dowiedz się, jak używać [Microsoft::WRL::Make](../windows/make-function.md) i [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md) funkcji do utworzenia wystąpienia składnika z moduł, który definiuje ją.  
  
 [Instrukcje: Użyj winmdidl.exe i midlrt.exe, aby utworzyć pliki .h z metadanych systemu Windows](../windows/use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata.md)  
 Pokazuje, jak korzystać z niestandardowych składników środowiska wykonawczego systemu Windows z biblioteki WRL przez utworzenie pliku IDL z metadanych winmd.  
  
 [Przewodnik: łączenie za pomocą zadań i żądań XML HTTP](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)  
 Przedstawia sposób użycia [IXMLHTTPRequest2](http://msdn.microsoft.com/en-us/bbc11c4a-aecf-4d6d-8275-3e852e309908) i [IXMLHTTPRequest2Callback](http://msdn.microsoft.com/en-us/aa4b3f4c-6e28-458b-be25-6cce8865fc71) interfejsy wraz z zadań do wysyłania żądań HTTP GET i POST do usługi sieci web w aplikacji platformy uniwersalnej systemu Windows.  
  
 [Przykładowe Optymalizator podróży mapy Bing](http://code.msdn.microsoft.com/Bing-Maps-trip-optimizer-c4e037f7)  
 Używa `HttpRequest` klasy, która jest zdefiniowana w [wskazówki: łączenie za pomocą zadań i żądań XML HTTP](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md) w kontekście pełnej aplikacji platformy uniwersalnej systemu Windows.  
  
 [Tworzenie składników biblioteki DLL środowiska wykonawczego systemu Windows z przykład w języku C++](http://code.msdn.microsoft.com/windowsapps/Creating-a-Windows-Runtime-6c399797)  
 Przedstawia sposób użycia Biblioteka szablonów C++ środowiska wykonawczego systemu Windows do tworzenia składnika biblioteki DLL w trakcie i pobrać go z C + +/ CX, JavaScript i C#.  
  
 [Przykładowe gier Marmur Labirynt DirectX](http://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345)  
 Demonstracja umożliwia zarządzanie okresem istnienia składników COM, takie jak aplikacja DirectX i platformy Media Foundation w kontekście pełną gry 3-Biblioteka szablonów C++ środowiska wykonawczego systemu Windows.  
  
 [Wysyłanie wyskakujące powiadomienia z aplikacji komputerowych przykładu](http://code.msdn.microsoft.com/windowsdesktop/Sending-toast-notifications-71e230a2)  
 Pokazuje, jak pracować z wyskakujące powiadomienia z aplikacji komputerowej za pomocą Biblioteka szablonów C++ środowiska wykonawczego systemu Windows.  
  
## <a name="windows-runtime-c-template-library-compared-to-atl"></a>Biblioteka szablonów C++ środowiska wykonawczego systemu Windows w porównaniu do ATL  
 Biblioteka szablonów C++ środowiska wykonawczego systemu Windows jest podobny Active Template Library (ATL), ponieważ służy do tworzenia małe, szybkie obiektów COM. Biblioteka szablonów C++ środowiska wykonawczego systemu Windows i ATL również udostępniać pojęcia, takie jak definicji obiektów w modułach, jawnej rejestracji interfejsów, a następnie otwórz Tworzenie obiektów przy użyciu fabryki. Można doświadczenia z Biblioteka szablonów C++ środowiska wykonawczego systemu Windows, jeśli znasz ATL.  
  
 Biblioteka szablonów C++ środowiska wykonawczego systemu Windows obsługuje funkcje COM, które są wymagane dla aplikacji platformy uniwersalnej systemu Windows. W związku z tym różni się od ATL ponieważ pominięto bezpośrednią obsługę COM funkcje takie jak:  
  
-   Agregacji  
  
-   implementacje standardowych  
  
-   podwójne interfejsy (`IDispatch`)  
  
-   interfejsy modułu wyliczającego standardowe  
  
-   punkty połączenia  
  
-   oderwania interfejsów  
  
-   Osadzanie OLE  
  
-   kontrolki ActiveX  
  
-   COM+  
  
## <a name="concepts"></a>Pojęcia  
 Biblioteka szablonów C++ środowiska wykonawczego systemu Windows zawiera typy, które reprezentują kilka podstawowych pojęć. W poniższych sekcjach opisano tych typów.  
  
### <a name="comptr"></a>ComPtr  
 [Comptr —](../windows/comptr-class.md) jest *wskaźnika inteligentnego* typu, który reprezentuje interfejs, który jest określony przez parametr szablonu. Użyj `ComPtr` Aby zadeklarować zmienną, które mogą uzyskiwać dostęp do elementów członkowskich obiektu, który jest pochodną interfejsu. `ComPtr`automatycznie przechowuje licznika odwołań do podstawowej wskaźnika interfejsu i zwalnia interfejsu, gdy liczba odwołań do zera.  
  
### <a name="runtimeclass"></a>RuntimeClass  
 [Runtimeclass —](../windows/runtimeclass-class.md) reprezentuje wystąpień klasy, która dziedziczy zestaw określonych interfejsów. A `RuntimeClass` obiektu zapewniają kombinację obsługę jeden lub więcej interfejsów COM środowiska wykonawczego systemu Windows lub słabe odwołanie do składnika.  
  
### <a name="module"></a>Moduł  
 [Moduł](../windows/module-class.md) reprezentuje kolekcję obiektów pokrewnych. A `Module` zarządza obiekt fabryki klas, które tworzenia obiektów i rejestracji, dzięki czemu inne aplikacje, aby można było użyć obiektu.  
  
### <a name="callback"></a>Wywołanie zwrotne  
 [Wywołania zwrotnego](../windows/callback-function-windows-runtime-cpp-template-library.md) funkcja tworzy obiekt, którego funkcja członkowska jest program obsługi zdarzeń (Metoda wywołania zwrotnego). Użyj `Callback` funkcji asynchronicznych operacji zapisu.  
  
### <a name="eventsource"></a>EventSource  
 [Element EventSource](../windows/eventsource-class.md) służy do zarządzania *delegować* procedury obsługi zdarzeń. Biblioteka szablonów C++ środowiska wykonawczego systemu Windows umożliwia wdrożenie delegata, a za pomocą `EventSource` do dodania, usunięcia, a następnie wywołaj delegatów.  
  
### <a name="asyncbase"></a>AsyncBase  
 [Asyncbase —](../windows/asyncbase-class.md) udostępnia metody wirtualne, które reprezentują model programowania asynchronicznego środowiska wykonawczego systemu Windows. Zastąpienie członkowie w tej klasie do utworzenia niestandardowej klasy, które można uruchomić, zatrzymać lub sprawdzić postęp operacji asynchronicznej.  
  
### <a name="ftmbase"></a>FtmBase  
 [Ftmbase —](../windows/ftmbase-class.md) reprezentuje obiekt opcja. `FtmBase`tworzy tabelę interfejsu globalnego (GIT) i ułatwia zarządzanie obiektami organizowanie i serwera proxy.  
  
### <a name="weakref"></a>WeakRef  
 [Weakref —](../windows/weakref-class.md) jest typem wskaźnika inteligentnych, który reprezentuje *słabe odwołanie*, który odwołuje się do obiektu, który może lub nie mogą być niedostępne. A `WeakRef` obiekt może służyć za środowiska uruchomieniowego systemu Windows, a nie klasycznego modelu COM.  
  
 A `WeakRef` zazwyczaj obiekt reprezentuje obiekt, którego istnienie jest kontrolowany przez wątek zewnętrznych lub aplikacji. Na przykład `WeakRef` obiektu można odwołać obiektu pliku. Gdy plik jest otwarty, `WeakRef` jest prawidłowy i przywoływany plik jest dostępny. Jednak podczas zamykania pliku `WeakRef` jest nieprawidłowy i pliku nie jest dostępny.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|||  
|-|-|  
|[Szablon projektu biblioteki klas](../windows/wrl-class-library-project-template.md)|Opisuje sposób uzyskać dostęp do szablonu projektu biblioteki klas WRL. Ten szablon upraszcza zadanie do tworzenia składników środowiska wykonawczego systemu Windows za pomocą programu Visual Studio.|  
|[Kluczowe interfejsy API według kategorii](../windows/key-wrl-apis-by-category.md)|Omówiono podstawowe typy Biblioteka szablonów C++ środowiska wykonawczego systemu Windows, funkcje i makr.|  
|[Dokumentacja](../windows/wrl-reference.md)|Zawiera informacje dotyczące Biblioteka szablonów C++ środowiska wykonawczego systemu Windows.|  
|[Szybkie odwołanie (środowisko wykonawcze systemu Windows i program Visual C++)](http://go.microsoft.com/fwlink/p/?linkid=229180)|Krótko opisano C + +/ CX funkcje obsługi środowiska uruchomieniowego systemu Windows.|  
|[Przy użyciu składników środowiska wykonawczego systemu Windows w programie Visual C++](http://go.microsoft.com/fwlink/p/?linkid=229155)|Przedstawia sposób użycia C + +/ CX do Tworzenie podstawowego składnika środowiska wykonawczego systemu Windows.|