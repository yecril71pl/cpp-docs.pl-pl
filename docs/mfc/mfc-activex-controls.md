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
ms.openlocfilehash: 58af2dc59aa6287ad01ace41cca54e615c48c0b6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618091"
---
# <a name="mfc-activex-controls"></a>Kontrolki ActiveX MFC

Kontrolka ActiveX to składnik oprogramowania wielokrotnego użytku oparty na Component Object Model (COM), który obsługuje szeroką gamę funkcji OLE i można go dostosować do potrzeb wielu programów.

>[!IMPORTANT]
> Kontrolka ActiveX to Starsza technologia, która nie powinna być używana do nowych celów programistycznych. Aby uzyskać więcej informacji, zobacz [kontrolki ActiveX](activex-controls.md).

Formanty ActiveX są przeznaczone do użycia zarówno w zwykłych kontenerach formantów ActiveX, jak i w Internecie, w World Wide Web stronach. Kontrolki ActiveX można utworzyć przy użyciu MFC, opisanego tutaj lub z [Active Template Library (ATL)](../atl/active-template-library-atl-concepts.md).

Formant ActiveX może być rysowany w osobnym oknie, odpowiadać na zdarzenia (takie jak kliknięcia myszą) i być zarządzany przez interfejs, który zawiera właściwości i metody podobne do tych w obiektach automatyzacji.

Te kontrolki można opracować dla wielu celów, takich jak dostęp do bazy danych, monitorowanie danych lub tworzenie wykresów. Oprócz ich przenośności kontrolki ActiveX nie obsługują funkcji, które wcześniej nie były dostępne dla formantów ActiveX, takich jak zgodność z istniejącymi kontenerami OLE i możliwość integrowania ich menu z menu kontenera OLE. Ponadto Kontrolka ActiveX w pełni obsługuje automatyzację, która umożliwia formantowi uwidocznienie właściwości read\write oraz zestawu metod, które mogą być wywoływane przez użytkownika formantu.

Można tworzyć bezokienkowe kontrolki ActiveX i kontrolki, które tworzą okno tylko wtedy, gdy stają się aktywne. Kontrolki bez okien przyspieszają wyświetlanie aplikacji i umożliwiają przezroczyste i nieprostokątne kontrolki. Możesz również ładować właściwości kontrolki ActiveX asynchronicznie.

Kontrolka ActiveX jest implementowana jako serwer wewnątrzprocesowe (zazwyczaj niewielki obiekt), którego można użyć w dowolnym kontenerze OLE. Należy zauważyć, że pełna funkcja kontrolki ActiveX jest dostępna tylko wtedy, gdy jest używana w kontenerze OLE zaprojektowanym tak, aby wiedzieć o kontrolkach ActiveX. Zobacz [kontrolki ActiveX portów do innych aplikacji](containers-for-activex-controls.md) , aby uzyskać listę kontenerów, które obsługują kontrolki ActiveX. Ten typ kontenera, zwany dalej "kontenerem sterowania", może obsługiwać kontrolkę ActiveX przy użyciu właściwości i metod kontrolki, a następnie odbiera powiadomienia z kontrolki ActiveX w formie zdarzeń. Na poniższej ilustracji przedstawiono tę interakcję.

![Współpraca kontrolki ActiveX i kontenera](../mfc/media/vc37221.gif "Współpraca kontrolki ActiveX i kontenera") <br/>
Interakcja między kontenerem kontrolki ActiveX i kontrolką okienkową ActiveX

Aby uzyskać najnowsze informacje na temat optymalizowania kontrolek ActiveX, zobacz [kontrolki ActiveX MFC: Optymalizacja](mfc-activex-controls-optimization.md).

Aby utworzyć kontrolkę ActiveX MFC, zobacz [Tworzenie projektu kontrolki ActiveX](reference/mfc-activex-control-wizard.md).

Aby uzyskać więcej informacji, zobacz:

- [Kontenery kontrolek ActiveX](activex-control-containers.md)

- [Dokumenty aktywne](active-documents.md)

- [Informacje o kontrolkach ActiveX](/windows/win32/com/activex-controls)

- [Uaktualnianie istniejącej kontrolki ActiveX do użycia w Internecie](upgrading-an-existing-activex-control.md)

## <a name="basic-components-of-an-activex-control"></a><a name="_core_basic_components_of_an_activex_control"></a>Podstawowe składniki kontrolki ActiveX

Kontrolka ActiveX używa kilku elementów programistycznych do wydajnej współpracy z kontenerem sterowania i użytkownikiem. Są to klasy [COleControl](reference/colecontrol-class.md), zestaw funkcji uruchamiania zdarzeń oraz mapa wysyłania.

Każdy obiekt formantu ActiveX, który tworzysz, dziedziczy zaawansowany zestaw funkcji z klasy podstawowej MFC `COleControl` . Te funkcje obejmują aktywację w miejscu i logikę automatyzacji. `COleControl`może dostarczyć obiekt sterowania z tą samą funkcjonalnością co obiekt okna MFC oraz możliwość uruchamiania zdarzeń. `COleControl`może również udostępniać [bezokienkowe kontrolki](providing-windowless-activation.md), które są zależne od ich kontenera, aby uzyskać pomoc dotyczącą niektórych funkcji dostępnych w oknie (przechwytywanie myszy, fokus klawiatury, przewijanie), ale oferują znacznie szybsze wyświetlanie.

Ponieważ Klasa formantów pochodzi z `COleControl` , dziedziczy możliwość wysyłania komunikatów (nazywanych zdarzeniami) do kontenera kontroli po spełnieniu określonych warunków. Te zdarzenia są używane do powiadamiania kontenera kontroli, gdy jakaś istotna występuje w formancie. Można wysłać dodatkowe informacje o zdarzeniu do kontenera kontroli przez dołączenie parametrów do zdarzenia. Aby uzyskać więcej informacji na temat zdarzeń kontrolki ActiveX, zobacz artykuł [kontrolki ActiveX MFC: zdarzenia](mfc-activex-controls-events.md).

Końcowy element to mapa wysyłania, która jest używana do ujawnienia zestawu funkcji (nazywanych metodami) i atrybutów (nazywanych właściwościami) użytkownikowi kontrolki. Właściwości umożliwiają kontenerowi sterowania lub użytkownikowi kontrolce manipulowanie kontrolką na różne sposoby. Użytkownik może zmienić wygląd kontrolki, zmienić niektóre wartości kontrolki lub wykonać żądania kontrolki, takie jak dostęp do określonego fragmentu danych obsługiwanego przez formant. Ten interfejs jest określany przez dewelopera kontroli i jest definiowany przy użyciu **Widok klasy**. Aby uzyskać więcej informacji na temat metod i właściwości kontrolki ActiveX, zobacz artykuły [formanty ActiveX MFC: metody](mfc-activex-controls-methods.md) i [Właściwości](mfc-activex-controls-properties.md).

## <a name="interaction-between-controls-with-windows-and-activex-control-containers"></a><a name="_core_interaction_between_controls_with_windows_and_activex_control_containers"></a>Interakcja między kontrolkami przy użyciu kontenerów formantów systemu Windows i ActiveX

Gdy kontrolka jest używana w kontenerze sterowania, używa dwóch mechanizmów do komunikowania: ujawnia właściwości i metody oraz wyzwala zdarzenia. Na poniższej ilustracji pokazano, jak te dwa mechanizmy są implementowane.

![Kontrolka ActiveX komunikuje się z jej kontenerem](../mfc/media/vc37222.gif "Kontrolka ActiveX komunikuje się z jej kontenerem") <br/>
Komunikacja między kontenerem kontrolki ActiveX i kontrolką ActiveX

Na powyższym rysunku pokazano również, jak inne interfejsy OLE (oprócz automatyzacji i zdarzeń) są obsługiwane przez formanty.

Cała komunikacja formantu z kontenerem jest wykonywana przez `COleControl` . Aby obsłużyć niektóre żądania kontenera, `COleControl` program wywoła funkcje członkowskie, które są zaimplementowane w klasie kontrolki. Wszystkie metody i niektóre właściwości są obsługiwane w ten sposób. Klasa kontrolki może również inicjować komunikację z kontenerem przez wywoływanie funkcji składowych `COleControl` . Zdarzenia są generowane w ten sposób.

## <a name="active-and-inactive-states-of-an-activex-control"></a><a name="_core_active_and_inactive_states_of_an_activex_control"></a>Aktywne i nieaktywne Stany kontrolki ActiveX

Kontrolka ma dwa stany podstawowe: aktywne i nieaktywne. Tradycyjnie te Stany były rozróżniane, niezależnie od tego, czy formant miał okno. Aktywna kontrolka miała okno; nieaktywna kontrolka. W przypadku wprowadzenia aktywacji bezokienkowej tego rozróżnienia nie jest już uniwersalne, ale nadal dotyczy wielu kontrolek.

Gdy [sterowanie bezokienkowe](providing-windowless-activation.md) jest aktywne, wywołuje funkcję przechwytywania myszy, fokus klawiatury, przewijanie i inne usługi okna z jego kontenera. Możesz również [zapewnić interakcję myszy z nieaktywnymi kontrolkami](providing-mouse-interaction-while-inactive.md), a także tworzyć kontrolki, które [oczekują na utworzenie okna](turning-off-the-activate-when-visible-option.md).

Gdy kontrolka z oknem stanie się aktywna, można w pełni korzystać z kontenera kontroli, użytkownika i systemu Windows. Na poniższym rysunku przedstawiono ścieżki komunikacji między kontrolką ActiveX, kontenerem sterowania i systemem operacyjnym.

![Przetwarzanie komunikatów w aktywnym oknie kontrolki ActiveX](../mfc/media/vc37223.gif "Przetwarzanie komunikatów w aktywnym oknie kontrolki ActiveX") <br/>
Przetwarzanie komunikatów systemu Windows w oknie kontrolki ActiveX (gdy jest aktywny)

## <a name="serialization"></a><a name="_core_serializing_activex_elements"></a>Serializacji

Możliwość serializowania danych, czasami określana jako trwałość, umożliwia kontrolce zapisanie wartości właściwości do magazynu trwałego. Kontrolki można następnie odtworzyć przez odczytanie stanu obiektu z magazynu.

Należy zauważyć, że formant nie jest odpowiedzialny za uzyskanie dostępu do nośnika magazynu. Zamiast tego kontener kontrolki jest odpowiedzialny za zapewnienie kontroli z nośnikiem magazynującym do użycia w odpowiednim czasie. Aby uzyskać więcej informacji na temat serializacji, zobacz artykuł [MFC ActiveX formantów: serializacji](mfc-activex-controls-serializing.md). Aby uzyskać informacje na temat optymalizowania serializacji, zobacz [Optymalizacja trwałości i inicjalizacji](optimizing-persistence-and-initialization.md) w kontrolkach ActiveX: Optymalizacja.

## <a name="installing-activex-control-classes-and-tools"></a><a name="_core_installing_activex_control_classes_and_tools"></a>Instalowanie klas i narzędzi formantów ActiveX

Podczas instalowania Visual C++ klasy kontrolek ActiveX MFC i sieci sprzedaży i debugowania formantów ActiveX czasu wykonywania są instalowane automatycznie, jeśli kontrolki ActiveX są wybrane w instalatorze (domyślnie są wybrane).

Domyślnie klasy formantów ActiveX i narzędzia są instalowane w następujących podkatalogach w folderze \Program Files\Microsoft Visual Studio .NET:

- **\Common7\Tools**

   Zawiera pliki kontenera testowego (TstCon32. exe, a także jego pliki pomocy).

- **\Vc7\atlmfc\include**

   Zawiera pliki dołączane, które są konieczne do opracowania formantów ActiveX z MFC

- **\Vc7\atlmfc\src\mfc**

   Zawiera kod źródłowy dla określonych klas formantów ActiveX w MFC

- **\Vc7\atlmfc\lib**

   Zawiera biblioteki wymagane do opracowania formantów ActiveX z MFC

Istnieją także przykłady dla kontrolek ActiveX MFC. Aby uzyskać więcej informacji na temat tych przykładów, zobacz [przykłady formantów: formanty ActiveX oparte na MFC](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>Zobacz też

[Elementy interfejsu użytkownika](user-interface-elements-mfc.md)
