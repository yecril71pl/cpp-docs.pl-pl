---
title: Kontrolki ActiveX MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MFC ActiveX Controls (MFC)
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b94172d57bc21e7f747a5d0986ef28dbfb80e481
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428645"
---
# <a name="mfc-activex-controls"></a>Kontrolki ActiveX MFC

Kontrolki ActiveX jest składnik oprogramowania wielokrotnego użytku, oparte na Component Object Model (COM) obsługuje szeroki zakres funkcji OLE, który można dostosować do potrzeb wiele oprogramowania.

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji, zobacz [formantów ActiveX](activex-controls.md).

Kontrolki ActiveX są przeznaczone do użycia zarówno w zwykłych kontenery kontrolek ActiveX w Internecie, w strony sieci Web. Kontrolki ActiveX można utworzyć za pomocą MFC, opisane w tym miejscu lub za pomocą [Active Template Library (ATL)](../atl/active-template-library-atl-concepts.md).

Kontrolki ActiveX można narysować sam w osobnym oknie reagowania na zdarzenia (na przykład kliknięć myszą), a następnie można zarządzać za pomocą interfejsu, który zawiera właściwości i metod podobnych do tych obiektów automatyzacji.

Te kontrolki mogą być tworzone dla zastosowań, takich jak dostęp do bazy danych, dane monitorowania lub wykresów. Oprócz ich przenoszenia kontrolek ActiveX obsługuje funkcje wcześniej niedostępne do kontrolki ActiveX, takich jak zgodność z istniejących kontenerów OLE i możliwość integracji z ich menu z menu kontenera OLE. Ponadto kontrolki ActiveX w pełni obsługuje automatyzację, co umożliwia kontrolę do udostępnienia właściwości odczytem/zapisem i zestaw metod, które mogą być wywoływane przez formant użytkownika.

Można utworzyć kontrolek ActiveX bez okien i formantów, które tylko utworzyć okno, gdy tylko staną się aktywne. Od kontrolek bez okien przyspieszyć wyświetlanie aplikacji i umożliwia przejrzyste i nieprostokątne formantów. Można również załadować właściwości formantu ActiveX asynchronicznie.

Kontrolki ActiveX jest wdrażany jako serwer w trakcie (zazwyczaj małego obiektu), który może służyć w dowolnym kontenerze OLE. Należy pamiętać, że pełną funkcjonalność formantu ActiveX dostępne tylko wtedy, gdy jest używane w ramach kontener OLE, który jest zaprojektowany pod uwagę formantów ActiveX. Zobacz [portu kontrolek ActiveX do innych aplikacji](../mfc/containers-for-activex-controls.md) listę kontenerów, które obsługuje formantów ActiveX. Ten typ kontenera, zwany "kontener formantu" może działać formantu ActiveX przy użyciu właściwości i metod formantu i odbiera powiadomienia z kontrolek ActiveX w formularzu zdarzenia. Na poniższym rysunku pokazano ta interakcja.

![Wzajemne oddziaływania wykresów w kontenerze kontrolek ActiveX i kontroli](../mfc/media/vc37221.gif "vc37221") interakcji między kontener formantu ActiveX i okna formantu ActiveX

Aby uzyskać niektóre najnowsze informacje dotyczące optymalizacji formantów ActiveX, zobacz [kontrolki ActiveX MFC: Optymalizacja](../mfc/mfc-activex-controls-optimization.md).

Aby utworzyć formant MFC ActiveX, zobacz [Tworzenie projektu kontrolki ActiveX](../mfc/reference/mfc-activex-control-wizard.md).

Aby uzyskać więcej informacji, zobacz:

- [Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)

- [Dokumenty aktywne](../mfc/active-documents.md)

- [Opis kontrolek ActiveX](/windows/desktop/com/activex-controls)

- [Uaktualnianie istniejącego kontrolki ActiveX, który ma być używany w Internecie](../mfc/upgrading-an-existing-activex-control.md)

##  <a name="_core_basic_components_of_an_activex_control"></a> Podstawowe składniki formantu ActiveX

Kontrolki ActiveX używa kilku elementów programowe wchodzić w interakcje wydajnie z kontenera kontrolki i użytkownika. Są to klasy [COleControl](../mfc/reference/colecontrol-class.md), zestaw funkcji inicjowanie zdarzeń oraz wysyłania mapy.

Każdy obiekt formantu ActiveX, tworzysz dziedziczy jej klasa bazowa MFC bogaty zestaw funkcji `COleControl`. Funkcje te obejmują aktywacji w miejscu i logiki automatyzacji. `COleControl` można udostępnić obiekt formantu taką samą funkcjonalność jak obiekt okna MFC, a także możliwość wyzwalać zdarzeń. `COleControl` można też podać [kontrolek bez okien](../mfc/providing-windowless-activation.md), które polegają na ich kontenera, aby uzyskać pomoc dotyczącą niektóre z funkcji okna zapewnia (przechwytywanie myszy, klawiatury, przewijania), ale oferuje znacznie szybsze wyświetlanie.

Ponieważ klasa formantów wywodzi się z `COleControl`, dziedziczy on możliwość wysyłania lub "ogień", wiadomości, wywołuje zdarzenia, do kontenera kontrolki, gdy są spełnione określone warunki. Aby otrzymywać powiadomienia, kontenera kontrolki, gdy coś, co jest ważne się dzieje w kontrolce korzysta z tych zdarzeń. Dodatkowe informacje o zdarzeniu może wysyłać do kontenera kontrolki, dołączając parametrów do zdarzenia. Aby uzyskać więcej informacji na temat zdarzeń formantów ActiveX, zobacz artykuł [kontrolki ActiveX MFC: zdarzenia](../mfc/mfc-activex-controls-events.md).

Ostatnim elementem jest mapa wysyłania, który jest używany do udostępnienia zestaw funkcji (o nazwie metody) i atrybuty (nazywane właściwościami) do formantu użytkownika. Właściwości umożliwiają kontener formantu lub użytkownika kontrolki do manipulowania kontroli na różne sposoby. Użytkownika można zmienić wygląd kontrolki, zmienić niektóre wartości kontrolki lub wysyłać żądania kontrolki, takie jak uzyskiwanie dostępu do konkretne dane, które obsługuje formant. Ten interfejs jest określana przez dewelopera kontrolek i jest definiowana za pomocą **Widok klas**. Aby uzyskać więcej informacji na temat właściwości i metod formantu ActiveX, zobacz artykuły [kontrolki ActiveX MFC: metody](../mfc/mfc-activex-controls-methods.md) i [właściwości](../mfc/mfc-activex-controls-properties.md).

##  <a name="_core_interaction_between_controls_with_windows_and_activex_control_containers"></a> Interakcja między formantami za pomocą Windows i kontenery kontrolek ActiveX

Gdy formant jest używany w kontenerze kontrolki, używa dwóch mechanizmów do komunikowania się: udostępnia właściwości i metody, a jego wyzwala zdarzenia. Na poniższym rysunku pokazano, jak te dwa mechanizmy są implementowane.

![Kontrolki ActiveX, który komunikuje się z jego kontenerem](../mfc/media/vc37222.gif "vc37222") komunikacji między kontener formantu ActiveX i kontrolki ActiveX

Powyższy rysunek pokazuje również, jak inne interfejsy OLE (oprócz automatyzacji i zdarzenia) są obsługiwane przez formanty.

Wszystkie kontrolki komunikacji z kontenerem odbywa się przez `COleControl`. Do obsługi niektórych żądań kontenera `COleControl` wywoła element członkowski funkcji, które są implementowane w klasie kontrolki. Wszystkie metody i niektóre właściwości są obsługiwane w ten sposób. Przez wywołanie funkcji składowych klasy z kontrolki można także zainicjować komunikacji z kontenerem `COleControl`. Zdarzenia są uruchamiane w ten sposób.

##  <a name="_core_active_and_inactive_states_of_an_activex_control"></a> Stany aktywnych i nieaktywnych formantu ActiveX

Formant ma dwa podstawowe stany: aktywnych i nieaktywnych. Zazwyczaj te stany zostały rozróżnianych na podstawie tego, czy formant ma okna. Aktywny formant ma okna; nie kontrolkę, która jest nieaktywny. Wraz z wprowadzeniem aktywacji niepowiązanej z oknami wykonywania tego rozróżnienia nie jest już uniwersalne, ale nadal dotyczy wielu kontrolek.

Gdy [niepowiązanej z oknami kontroli](../mfc/providing-windowless-activation.md) zbliża się aktywny, wywołuje ono przechwytywanie myszy, fokus klawiatury, przewijania i innych usług okna z jego kontenerem. Możesz również [zapewniają interakcji z myszą z kontrolkami nieaktywne](../mfc/providing-mouse-interaction-while-inactive.md), jak również tworzyć formanty [poczekaj, aż uaktywniony można utworzyć okna](../mfc/turning-off-the-activate-when-visible-option.md).

Gdy stanie się aktywny formant z okna, jest w stanie w pełni korzystać z kontenera kontrolki, użytkownika i Windows. Na poniższym rysunku przedstawiono ścieżki komunikacji między formantu ActiveX, kontener formantu i systemu operacyjnego.

![Przetwarzanie w aktywny formant ActiveX okna komunikatów](../mfc/media/vc37223.gif "vc37223") Windows przetwarzania wiadomości w okna kontrolki ActiveX (jeśli aktywny)

##  <a name="_core_serializing_activex_elements"></a> Serializacja

Zdolność do serializowania danych, czasami nazywane trwałości, umożliwia formant do zapisu wartości właściwości w magazynie trwałym. Następnie można odtworzyć formantów, zapoznając się stan obiektu z magazynu.

Należy pamiętać, że kontrolka nie jest odpowiedzialna za uzyskiwanie dostępu do nośnika magazynowania. Zamiast tego należy kontener formantu jest odpowiedzialne za świadczenie kontrolki z nośnika magazynowania do użycia w odpowiednim czasie. Aby uzyskać więcej informacji na temat serializacji, zobacz artykuł [kontrolki ActiveX MFC: serializacja](../mfc/mfc-activex-controls-serializing.md). Aby uzyskać informacje dotyczące optymalizacji serializacji, zobacz [Optymalizacja stanu trwałego i inicjalizacji](../mfc/optimizing-persistence-and-initialization.md) w kontrolkach ActiveX: optymalizacji.

##  <a name="_core_installing_activex_control_classes_and_tools"></a> Instalowanie narzędzia i klasy kontrolki ActiveX

Po zainstalowaniu programu Visual C++, MFC ActiveX sterowania klasy i handel detaliczny i debugowanie kontrolki ActiveX, które biblioteki wykonawczej DLL są instalowane automatycznie, jeśli zaznaczono kontrolki ActiveX w Instalatorze (są one wybrane domyślnie).

Domyślnie klasy kontrolek ActiveX i narzędzia są instalowane w poniższych podkatalogach \Program Files\Microsoft programu Visual Studio .NET:

- **\Common7\Tools**

     Zawiera pliki kontenera testu (TstCon32.exe, a także jej pliki pomocy).

- **\Vc7\atlmfc\include**

     Zawiera pliki nagłówkowe potrzebne do tworzenia kontrolki ActiveX z MFC

- **\Vc7\atlmfc\src\mfc**

     Zawiera kod źródłowy dla określonej klasy kontrolek ActiveX w MFC

- **\Vc7\atlmfc\lib**

     Zawiera biblioteki wymagane do rozwoju formantów ActiveX MFC

Dostępne są także przykłady dla kontrolek MFC ActiveX. Aby uzyskać więcej informacji na temat tych przykładów, zobacz [przykłady formantów: MFC-Based kontrolek ActiveX](../visual-cpp-samples.md)

## <a name="see-also"></a>Zobacz też

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)
