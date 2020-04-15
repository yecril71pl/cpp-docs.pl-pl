---
title: Programy obsługi dla zakresów map komunikatów
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- handlers [MFC], message-map ranges
- message maps [MFC], message handler functions
- message maps [MFC], ranges
- control-notification messages [MFC]
- command IDs [MFC], message mapping
- message-map ranges [MFC]
- handlers [MFC]
- message handling [MFC], message handler functions
- mappings [MFC], message ranges
- command handling [MFC], command update handlers
- controls [MFC], notifications
- handler functions [MFC], message-map ranges
- handler functions [MFC]
- command update handlers [MFC]
- command routing [MFC], command update handlers
- message ranges [MFC]
- handler functions [MFC], declaring
- message ranges [MFC], mapping
ms.assetid: a271478b-5e1c-46f5-9f29-e5be44b27d08
ms.openlocfilehash: fc33df6957beab6e4e8de3093dfc00cf2651780e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370506"
---
# <a name="handlers-for-message-map-ranges"></a>Programy obsługi dla zakresów map komunikatów

W tym artykule wyjaśniono, jak mapować zakres wiadomości do funkcji obsługi pojedynczej wiadomości (zamiast mapowania jednej wiadomości tylko do jednej funkcji).

Istnieją chwile, kiedy trzeba przetworzyć więcej niż jedną wiadomość lub powiadomienie kontroli w dokładnie taki sam sposób. W takich momentach można mapować wszystkie komunikaty do jednej funkcji obsługi. Zakresy mapy wiadomości umożliwiają to w przypadku ciągłego zakresu komunikatów:

- Zakresy identyfikatorów poleceń można mapować w:

  - Funkcja obsługi poleceń.

  - Funkcja obsługi aktualizacji polecenia.

- Można mapować komunikaty powiadomień o kontroli dla zakresu identyfikatorów kontroli do funkcji obsługi wiadomości.

Tematy omówione w tym artykule obejmują:

- [Pisanie wpisu mapy wiadomości](#_core_writing_the_message.2d.map_entry)

- [Deklarowanie funkcji programu obsługi](#_core_declaring_the_handler_function)

- [Przykład zakresu identyfikatorów poleceń](#_core_example_for_a_range_of_command_ids)

- [Przykład zakresu identyfikatorów sterowania](#_core_example_for_a_range_of_control_ids)

## <a name="writing-the-message-map-entry"></a><a name="_core_writing_the_message.2d.map_entry"></a>Pisanie wpisu mapy wiadomości

W. CPP, dodaj wpis mapy wiadomości, jak pokazano w poniższym przykładzie:

[!code-cpp[NVC_MFCMessageHandling#6](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]

Wpis mapy wiadomości składa się z następujących elementów:

- Makro zakresu mapy wiadomości:

  - [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)

  - [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)

  - [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)

- Parametry do makra:

  Pierwsze dwa makra mają trzy parametry:

  - Identyfikator polecenia, który uruchamia zakres

  - Identyfikator polecenia, który kończy zakres

  - Nazwa funkcji obsługi wiadomości

  Zakres identyfikatorów poleceń musi być ciągły.

  Trzecie makro `ON_CONTROL_RANGE`przyjmuje dodatkowy pierwszy parametr: komunikat z powiadomieniem o kontroli, taki jak **EN_CHANGE**.

## <a name="declaring-the-handler-function"></a><a name="_core_declaring_the_handler_function"></a>Deklarowanie funkcji obsługi

Dodaj deklarację funkcji obsługi w pliku . H. Poniższy kod pokazuje, jak to może wyglądać, jak pokazano poniżej:

[!code-cpp[NVC_MFCMessageHandling#7](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_2.h)]

Funkcje obsługi dla pojedynczych poleceń zwykle nie przyjmują żadnych parametrów. Z wyjątkiem funkcji obsługi aktualizacji, funkcje obsługi dla zakresów mapy komunikatów wymagają dodatkowego parametru, *nID*, typu **UINT**. Ten parametr jest pierwszym parametrem. Dodatkowy parametr obsługuje dodatkowy identyfikator polecenia potrzebny do określenia, które polecenie użytkownik faktycznie wybrał.

Aby uzyskać więcej informacji na temat wymagań dotyczących parametrów dotyczących aktualizowania funkcji programu obsługi, zobacz [Przykład zakresu identyfikatorów poleceń](#_core_example_for_a_range_of_command_ids).

## <a name="example-for-a-range-of-command-ids"></a><a name="_core_example_for_a_range_of_command_ids"></a>Przykład zakresu identyfikatorów poleceń

Kiedy można użyć zakresów Jednym z przykładów jest obsługa poleceń, takich jak polecenie Zoom w przykładzie MFC [HIERSVR](../overview/visual-cpp-samples.md). To polecenie powiększa widok, skalując go między 25% a 300% jego normalnego rozmiaru. Klasa widoku programu HIERSVR używa zakresu do obsługi poleceń Zoom z wpisem mapy wiadomości przypominającym ten:

[!code-cpp[NVC_MFCMessageHandling#8](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]

Podczas pisania wpisu mapy wiadomości należy określić:

- Dwa identyfikatory poleceń, rozpoczynające i kończące ciągły zakres.

   Tutaj są **ID_VIEW_ZOOM25** i **ID_VIEW_ZOOM300**.

- Nazwa funkcji obsługi dla poleceń.

   Oto `OnZoom`.

Deklaracja funkcji będzie przypominać następującą:

[!code-cpp[NVC_MFCMessageHandling#9](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_4.h)]

W przypadku funkcji obsługi aktualizacji jest podobny i może być bardziej przydatne. Jest to dość powszechne, aby napisać `ON_UPDATE_COMMAND_UI` programy obsługi dla wielu poleceń i znaleźć się pisanie lub kopiowanie tego samego kodu w kółko. Rozwiązaniem jest mapowanie zakresu identyfikatorów poleceń na jedną `ON_UPDATE_COMMAND_UI_RANGE` funkcję obsługi aktualizacji przy użyciu makra. Identyfikatory poleceń muszą tworzyć ciągły zakres. Na przykład zobacz `OnUpdateZoom` program obsługi `ON_UPDATE_COMMAND_UI_RANGE` i jego wpis mapy wiadomości w klasie widoku próbki PROGRAMU HIERSVR.

Funkcje obsługi aktualizacji dla pojedynczych poleceń zwykle przyjmują pojedynczy `CCmdUI*`parametr, *pCmdUI*, typu . W przeciwieństwie do funkcji obsługi, funkcje obsługi aktualizacji dla zakresów mapy wiadomości nie wymagają dodatkowego parametru, *nID*, typu **UINT**. Identyfikator polecenia, który jest potrzebny do określenia, które polecenie użytkownik `CCmdUI` faktycznie wybrał, znajduje się w obiekcie.

## <a name="example-for-a-range-of-control-ids"></a><a name="_core_example_for_a_range_of_control_ids"></a>Przykład zakresu identyfikatorów sterowania

Innym interesującym przypadkiem jest mapowanie komunikatów powiadomień o kontroli dla zakresu identyfikatorów kontroli do jednego programu obsługi. Załóżmy, że użytkownik może kliknąć dowolny z 10 przycisków. Aby zamapować wszystkie 10 przycisków na jeden program obsługi, wpis mapy wiadomości będzie wyglądał następująco:

[!code-cpp[NVC_MFCMessageHandling#10](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]

Podczas pisania `ON_CONTROL_RANGE` makra na mapie wiadomości należy określić:

- Określony komunikat z powiadomieniem o kontroli.

   Tutaj jest **BN_CLICKED**.

- Wartości identyfikatora formantu skojarzone z ciągłym zakresem formantów.

   Oto **IDC_BUTTON1** i **IDC_BUTTON10**.

- Nazwa funkcji obsługi wiadomości.

   Oto `OnButtonClicked`.

Podczas pisania funkcji obsługi należy określić dodatkowy parametr **UINT,** jak pokazano w następujących czynnościach:

[!code-cpp[NVC_MFCMessageHandling#11](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]

Program `OnButtonClicked` obsługi pojedynczego **BN_CLICKED** wiadomości nie przyjmuje żadnych parametrów. Ten sam program obsługi dla zakresu przycisków ma jeden **UINT**. Dodatkowy parametr umożliwia identyfikację określonego formantu odpowiedzialnego za generowanie **komunikatu BN_CLICKED.**

Kod pokazany w przykładzie jest typowy: konwertowanie wartości przekazywane do `int` zakresu komunikatów i twierdząc, że jest to przypadek. Następnie możesz podjąć różne działania w zależności od tego, który przycisk został kliknięty.

## <a name="see-also"></a>Zobacz też

[Deklarowanie funkcji obsługi komunikatów](../mfc/declaring-message-handler-functions.md)
