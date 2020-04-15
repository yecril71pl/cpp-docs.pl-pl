---
title: Kontrolki ActiveX MFC
ms.date: 11/19/2018
f1_keywords:
- MFC ActiveX Controls (MFC)
helpviewer_keywords:
- COleControl class [MFC], MFC ActiveX controls
- ActiveX controls [MFC], MFC
- containers [MFC], MFC ActiveX controls
- MFC ActiveX controls [MFC], serializing
- MFC ActiveX controls [MFC], containers
- serialization [MFC], MFC ActiveX controls
- dispatch maps [MFC], for MFC ActiveX controls
- MFC ActiveX controls [MFC], active/inactive state
- events [MFC], ActiveX controls
- MFC ActiveX controls [MFC]
ms.assetid: c911fb74-3afc-4bf3-a0f5-7922b14d9a1b
ms.openlocfilehash: e9cc38eebed0b1f8e0932e89ef1452261aefd7dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365442"
---
# <a name="mfc-activex-controls"></a>Kontrolki ActiveX MFC

Formant ActiveX to składnik oprogramowania wielokrotnego pożytku oparty na modelu com (Component Object Model), który obsługuje szeroką gamę funkcji OLE i można go dostosować do wielu potrzeb oprogramowania.

>[!IMPORTANT]
> ActiveX to starsza technologia, która nie powinna być używana do nowego rozwoju. Aby uzyskać więcej informacji, zobacz [ActiveX Controls](activex-controls.md).

Formanty ActiveX są przeznaczone do użytku zarówno w zwykłych kontenerach sterowania ActiveX, jak i w Internecie, na stronach sieci World Wide Web. Formanty ActiveX można tworzyć za pomocą opisanego w tym miejscu pliku MFC lub [biblioteki aktywnych szablonów (ATL).](../atl/active-template-library-atl-concepts.md)

Formant ActiveX może rysować się we własnym oknie, reagować na zdarzenia (takie jak kliknięcia myszą) i być zarządzany za pośrednictwem interfejsu, który zawiera właściwości i metody podobne do tych w automatyzacji obiektów.

Te formanty mogą być opracowane dla wielu zastosowań, takich jak dostęp do bazy danych, monitorowania danych lub wykresów. Oprócz ich przenośności, ActiveX kontroluje funkcje wcześniej niedostępne dla formantów ActiveX, takie jak zgodność z istniejącymi kontenerami OLE i możliwość integracji ich menu z menu kontenerów OLE. Ponadto formant ActiveX w pełni obsługuje automatyzację, która umożliwia formancie uwidacznianie właściwości read\write i zestaw metod, które mogą być wywoływane przez użytkownika formantu.

Można tworzyć bezokietowe formanty ActiveX i formanty, które tworzą okno tylko wtedy, gdy staną się aktywne. Formanty bez okien przyspieszają wyświetlanie aplikacji i umożliwiają wyświetlanie przezroczystych i niepodkreślanych elementów sterujących. Można również załadować właściwości formantu ActiveX asynchronicznie.

Formant ActiveX jest implementowany jako serwer w trakcie (zazwyczaj mały obiekt), który może być używany w dowolnym kontenerze OLE. Należy zauważyć, że pełna funkcjonalność formantu ActiveX jest dostępna tylko wtedy, gdy jest używana w kontenerze OLE zaprojektowanym tak, aby być świadomym formantów ActiveX. Zobacz [Formanty Port ActiveX do innych aplikacji, aby](../mfc/containers-for-activex-controls.md) uzyskać listę kontenerów obsługujących formanty ActiveX. Ten typ kontenera, zwany dalej "kontenerem formantu", może obsługiwać formant ActiveX przy użyciu właściwości i metod formantu i odbiera powiadomienia z formantu ActiveX w postaci zdarzeń. Na poniższej ilustracji przedstawiono tę interakcję.

![Wzajemne oddziaływanie kontenera sterującego ActiveX i sterowania](../mfc/media/vc37221.gif "Wzajemne oddziaływanie kontenera sterującego ActiveX i sterowania") <br/>
Interakcja między kontenerem sterowania ActiveX a formantem ActiveX w oknie

Aby uzyskać najnowsze informacje na temat optymalizacji formantów ActiveX, zobacz [MFC ActiveX Controls: Optimization](../mfc/mfc-activex-controls-optimization.md).

Aby utworzyć kontrolę MFC ActiveX, zobacz [Tworzenie projektu sterowania ActiveX](../mfc/reference/mfc-activex-control-wizard.md).

Aby uzyskać więcej informacji, zobacz:

- [Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)

- [Dokumenty aktywne](../mfc/active-documents.md)

- [Opis formantów ActiveX](/windows/win32/com/activex-controls)

- [Uaktualnianie istniejącego formantu ActiveX do użycia w Internecie](../mfc/upgrading-an-existing-activex-control.md)

## <a name="basic-components-of-an-activex-control"></a><a name="_core_basic_components_of_an_activex_control"></a>Podstawowe składniki formantu ActiveX

Formant ActiveX używa kilku elementów programowych do wydajnej interakcji z kontenerem sterowania i z użytkownikiem. Są to klasy [COleControl](../mfc/reference/colecontrol-class.md), zestaw funkcji wywoływania zdarzeń i mapy wysyłki.

Każdy utworzony obiekt kontrolny ActiveX dziedziczy potężny zestaw funkcji z `COleControl`klasy podstawowej MFC. Funkcje te obejmują aktywację w miejscu i logikę automatyzacji. `COleControl`może zapewnić obiekt kontrolny z taką samą funkcjonalnością jak obiekt okna MFC, a także możliwość ognia zdarzeń. `COleControl`może również zapewnić [formanty bez okien,](../mfc/providing-windowless-activation.md)które polegają na ich kontenerze, aby uzyskać pomoc w niektórych funkcjach oferowanych przez okno (przechwytywanie myszy, ustawianie ostrości klawiatury, przewijanie), ale oferują znacznie szybszy wyświetlacz.

Ponieważ klasa formantu `COleControl`wywodzi się z , dziedziczy możliwość wysyłania lub "fire", wiadomości, o nazwie zdarzenia, do kontenera formantu, gdy spełnione są pewne warunki. Zdarzenia te są używane do powiadamiania kontenera formantu, gdy coś ważnego dzieje się w formancie. Można wysłać dodatkowe informacje o zdarzeniu do kontenera formantu, dołączając parametry do zdarzenia. Aby uzyskać więcej informacji na temat zdarzeń kontrolnych ActiveX, zobacz artykuł [MFC ActiveX Controls: Events](../mfc/mfc-activex-controls-events.md).

Ostatnim elementem jest mapa wysyłki, który jest używany do udostępnienia zestaw funkcji (tzw metody) i atrybuty (nazywane właściwości) do użytkownika kontroli. Właściwości umożliwiają kontenera formantu lub użytkownika formantu do manipulowania formantem na różne sposoby. Użytkownik może zmienić wygląd formantu, zmienić niektóre wartości formantu lub zażądać formantu, takich jak uzyskiwanie dostępu do określonego fragmentu danych, który utrzymuje formant. Ten interfejs jest określany przez dewelopera formantu i jest definiowany za pomocą **widoku klasy**. Aby uzyskać więcej informacji na temat metod i właściwości kontroli ActiveX, zobacz artykuły [MFC ActiveX Controls: Metody](../mfc/mfc-activex-controls-methods.md) i [właściwości](../mfc/mfc-activex-controls-properties.md).

## <a name="interaction-between-controls-with-windows-and-activex-control-containers"></a><a name="_core_interaction_between_controls_with_windows_and_activex_control_containers"></a>Interakcja między formantami z kontenerami sterowania Windows i ActiveX

Gdy formant jest używany w kontenerze formantu, używa dwóch mechanizmów do komunikowania się: udostępnia właściwości i metody i uruchamia zdarzenia. Poniższy rysunek pokazuje, w jaki sposób te dwa mechanizmy są implementowane.

![Formant ActiveX komunikuje się ze swoim kontenerem](../mfc/media/vc37222.gif "Formant ActiveX komunikuje się ze swoim kontenerem") <br/>
Komunikacja między kontenerem sterowania ActiveX a formantem ActiveX

Poprzedni rysunek ilustruje również, jak inne interfejsy OLE (oprócz automatyzacji i zdarzeń) są obsługiwane przez formanty.

Cała komunikacja formantu z kontenerem `COleControl`jest wykonywana przez . Aby obsłużyć niektóre `COleControl` żądania kontenera, wywoła funkcje członkowskie, które są implementowane w klasie formantu. Wszystkie metody i niektóre właściwości są obsługiwane w ten sposób. Klasa formantu może również inicjować komunikację `COleControl`z kontenerem, wywołując funkcje członkowskie . Zdarzenia są uruchamiane w ten sposób.

## <a name="active-and-inactive-states-of-an-activex-control"></a><a name="_core_active_and_inactive_states_of_an_activex_control"></a>Aktywne i nieaktywne stany formantu ActiveX

Formant ma dwa podstawowe stany: aktywny i nieaktywny. Tradycyjnie państwa te wyróżniały się tym, czy kontrola miała okno. Aktywny formant miał okno; nieaktywnej kontroli nie. Wraz z wprowadzeniem aktywacji bez okien, rozróżnienie to nie jest już uniwersalne, ale nadal ma zastosowanie do wielu formantów.

Gdy [formant bez okien](../mfc/providing-windowless-activation.md) idzie aktywny, wywołuje przechwytywanie myszy, fokus klawiatury, przewijanie i inne usługi okna z jego kontenera. Można również [zapewnić interakcję myszy do nieaktywnych formantów,](../mfc/providing-mouse-interaction-while-inactive.md)a także utworzyć formanty, które [czekają, aż uaktywnią się, aby utworzyć okno.](../mfc/turning-off-the-activate-when-visible-option.md)

Gdy formant z oknem staje się aktywny, jest w stanie w pełni współdziałać z kontenerem formantu, użytkownikiem i systemem Windows. Poniższy rysunek przedstawia ścieżki komunikacji między formantem ActiveX, kontenerem formantu i systemem operacyjnym.

![Przetwarzanie msg w aktywnym formancie ActiveX w oknach](../mfc/media/vc37223.gif "Przetwarzanie msg w aktywnym formancie ActiveX w oknach") <br/>
Przetwarzanie wiadomości systemu Windows w formancie ActiveX w oknie (gdy jest aktywne)

## <a name="serialization"></a><a name="_core_serializing_activex_elements"></a>Serializacji

Możliwość serializacji danych, czasami określane jako trwałość, umożliwia formantowi zapis wartości jego właściwości do magazynu trwałego. Formanty można następnie odtworzyć, odczytając stan obiektu z magazynu.

Należy zauważyć, że formant nie jest odpowiedzialny za uzyskanie dostępu do nośnika danych. Zamiast tego kontener formantu jest odpowiedzialny za zapewnienie kontroli z nośnikiem magazynowym do użycia w odpowiednim czasie. Aby uzyskać więcej informacji na temat serializacji, zobacz artykuł [MFC ActiveX Controls: Serializing](../mfc/mfc-activex-controls-serializing.md). Aby uzyskać informacje na temat optymalizacji serializacji, zobacz [Optymalizacja trwałości i inicjowania](../mfc/optimizing-persistence-and-initialization.md) w formantach ActiveX: Optymalizacja.

## <a name="installing-activex-control-classes-and-tools"></a><a name="_core_installing_activex_control_classes_and_tools"></a>Instalowanie klas i narzędzi sterowania ActiveX

Po zainstalowaniu visual C++, klasy kontroli MFC ActiveX i detalicznych i debugowania activex kontroli bibliotek DLL w czasie wykonywania są automatycznie instalowane, jeśli formanty ActiveX są zaznaczone w Instalatorze (są one zaznaczone domyślnie).

Domyślnie klasy i narzędzia sterujące ActiveX są instalowane w następujących podkatalogach w obszarze \Program Files\Microsoft Visual Studio .NET:

- **\Common7\Narzędzia**

   Zawiera pliki kontenera testowego (TstCon32.exe, a także jego pliki Pomocy).

- **\Vc7\atlmfc\include**

   Zawiera pliki dołączane potrzebne do tworzenia formantów ActiveX z MFC

- **\Vc7\atlmfc\src\mfc**

   Zawiera kod źródłowy określonych klas kontrolnych ActiveX w MFC

- **\Vc7\atlmfc\lib**

   Zawiera biblioteki wymagane do tworzenia formantów ActiveX za pomocą MFC

Istnieją również przykłady dla formantów MFC ActiveX. Aby uzyskać więcej informacji na temat tych przykładów, zobacz [Przykłady kontroleki: Formanty ActiveX oparte na MFC](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>Zobacz też

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)
