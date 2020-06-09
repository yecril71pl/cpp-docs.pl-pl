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
ms.openlocfilehash: 0ff9178679792929bbd6eb92bb6148cfa008dcad
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621695"
---
# <a name="handlers-for-message-map-ranges"></a>Programy obsługi dla zakresów map komunikatów

W tym artykule wyjaśniono, jak mapować zakres komunikatów do jednej funkcji obsługi komunikatów (zamiast mapowania jednej wiadomości tylko do jednej funkcji).

Istnieją sytuacje, w których konieczne jest przetworzenie więcej niż jednego komunikatu lub powiadomienia kontroli w taki sam sposób. W takim przypadku warto zmapować wszystkie komunikaty do jednej funkcji obsługi. Zakresy map wiadomości umożliwiają wykonywanie tych czynności w przypadku ciągłego zakresu komunikatów:

- Zakresy identyfikatorów poleceń można mapować do:

  - Funkcja obsługi poleceń.

  - Funkcja obsługi aktualizacji polecenia.

- W celu zamapowania komunikatów sterujących kontroli dla zakresu identyfikatorów sterowania do funkcji obsługi komunikatów.

Tematy omówione w tym artykule obejmują:

- [Zapisywanie wpisu mapy komunikatów](#_core_writing_the_message.2d.map_entry)

- [Deklarowanie funkcji obsługi](#_core_declaring_the_handler_function)

- [Przykład dla zakresu identyfikatorów poleceń](#_core_example_for_a_range_of_command_ids)

- [Przykład dla zakresu identyfikatorów sterowania](#_core_example_for_a_range_of_control_ids)

## <a name="writing-the-message-map-entry"></a><a name="_core_writing_the_message.2d.map_entry"></a>Zapisywanie wpisu mapy komunikatów

W. Plik CPP, Dodaj wpis mapy wiadomości, jak pokazano w następującym przykładzie:

[!code-cpp[NVC_MFCMessageHandling#6](codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]

Wpis mapy komunikatów składa się z następujących elementów:

- Makro zakresu mapy komunikatów:

  - [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)

  - [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)

  - [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)

- Parametry do makra:

  Pierwsze dwa makra mają trzy parametry:

  - Identyfikator polecenia, który uruchamia zakres

  - Identyfikator polecenia kończącego zakres

  - Nazwa funkcji obsługi komunikatów

  Zakres identyfikatorów poleceń musi być ciągły.

  Trzecie makro, `ON_CONTROL_RANGE` Pobiera dodatkowy pierwszy parametr: komunikat kontrolny kontroli, taki jak **EN_CHANGE**.

## <a name="declaring-the-handler-function"></a><a name="_core_declaring_the_handler_function"></a>Deklarowanie funkcji obsługi

Dodaj deklarację funkcji procedury obsługi w. Plik H. Poniższy kod pokazuje, jak to może wyglądać, jak pokazano poniżej:

[!code-cpp[NVC_MFCMessageHandling#7](codesnippet/cpp/handlers-for-message-map-ranges_2.h)]

Funkcje obsługi dla pojedynczych poleceń zazwyczaj nie przyjmują żadnych parametrów. Z wyjątkiem funkcji obsługi aktualizacji, funkcje obsługi dla zakresów map komunikatów wymagają dodatkowego parametru, *NID*, typu **uint**. Ten parametr jest pierwszym parametrem. Dodatkowy parametr uwzględnia dodatkowy identyfikator polecenia, który jest wymagany do określenia polecenia, które użytkownik rzeczywiście wybiera.

Aby uzyskać więcej informacji na temat wymagań parametrów dotyczących aktualizacji funkcji programu obsługi, zobacz [przykład dla zakresu identyfikatorów poleceń](#_core_example_for_a_range_of_command_ids).

## <a name="example-for-a-range-of-command-ids"></a><a name="_core_example_for_a_range_of_command_ids"></a>Przykład dla zakresu identyfikatorów poleceń

Kiedy można używać zakresów jeden przykład jest w trakcie obsługi poleceń, takich jak powiększenie, w przykładowej [HIERSVR](../overview/visual-cpp-samples.md)MFC. To polecenie powoduje powiększanie widoku, skalowanie go w zakresie od 25% do 300% normalnego rozmiaru. Klasa widoku HIERSVR używa zakresu do obsługi poleceń powiększenia z wpisem mapy komunikatów podobnym do poniższego:

[!code-cpp[NVC_MFCMessageHandling#8](codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]

Podczas pisania wpisu mapy wiadomości należy określić:

- Dwa identyfikatory poleceń, początek i zakończenie ciągłego zakresu.

   Poniżej znajdują się **ID_VIEW_ZOOM25** i **ID_VIEW_ZOOM300**.

- Nazwa funkcji obsługi poleceń.

   Jest to możliwe `OnZoom` .

Deklaracja funkcji będzie wyglądać następująco:

[!code-cpp[NVC_MFCMessageHandling#9](codesnippet/cpp/handlers-for-message-map-ranges_4.h)]

Sprawa funkcji procedury obsługi aktualizacji jest podobna i prawdopodobnie jest bardziej użyteczna. Jest dość często używane do pisania `ON_UPDATE_COMMAND_UI` programów obsługi dla wielu poleceń i znajdowania pisania lub kopiowania tego samego kodu w porównaniu z tym samym kodem. Rozwiązaniem jest zamapowanie zakresu identyfikatorów poleceń na jedną funkcję procedury obsługi aktualizacji za pomocą `ON_UPDATE_COMMAND_UI_RANGE` makra. Identyfikatory poleceń muszą stanowić ciągły zakres. Aby zapoznać się z przykładem, zapoznaj się z tematem `OnUpdateZoom` obsługi i jego `ON_UPDATE_COMMAND_UI_RANGE` wpisem w mapie wiadomości w klasie widoku próbki HIERSVR.

Funkcja obsługi aktualizacji dla pojedynczych poleceń zazwyczaj przyjmuje jeden parametr, *pCmdUI*, typu `CCmdUI*` . W przeciwieństwie do funkcji obsługi, funkcja programu obsługi aktualizacji dla zakresów map komunikatów nie wymaga dodatkowego parametru, *NID*typu **uint**. Identyfikator polecenia, który jest wymagany do określenia, które polecenie użytkownik rzeczywiście wybiera, znajduje się w `CCmdUI` obiekcie.

## <a name="example-for-a-range-of-control-ids"></a><a name="_core_example_for_a_range_of_control_ids"></a>Przykład dla zakresu identyfikatorów sterowania

Innym interesującym przypadkiem jest mapowanie komunikatów z powiadomieniem kontroli dla zakresu identyfikatorów sterowania do pojedynczej procedury obsługi. Załóżmy, że użytkownik może kliknąć dowolny z 10 przycisków. Aby zmapować wszystkie 10 przycisków na jedną procedurę obsługi, wpis mapy wiadomości będzie wyglądać następująco:

[!code-cpp[NVC_MFCMessageHandling#10](codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]

Podczas pisania `ON_CONTROL_RANGE` makra w mapie wiadomości należy określić:

- Określony komunikat kontroli — powiadomienie.

   Oto **BN_CLICKED**.

- Wartości identyfikatora formantu skojarzone z ciągłym zakresem kontrolek.

   Poniżej znajdują się **IDC_BUTTON1** i **IDC_BUTTON10**.

- Nazwa funkcji obsługi komunikatów.

   Jest to możliwe `OnButtonClicked` .

Podczas pisania funkcji obsługi należy określić dodatkowy parametr **uint** , jak pokazano na poniższym przykładzie:

[!code-cpp[NVC_MFCMessageHandling#11](codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]

`OnButtonClicked`Procedura obsługi dla pojedynczego komunikatu **BN_CLICKED** nie przyjmuje żadnych parametrów. Ta sama procedura obsługi dla zakresu przycisków przyjmuje jeden **uint**. Dodatkowy parametr umożliwia określenie konkretnej kontrolki odpowiedzialnej za generowanie komunikatu **BN_CLICKED** .

Kod pokazywany w przykładzie jest typowy: konwertowanie wartości przesłanej do `int` zakresu wiadomości i potwierdzenia, że jest to przypadek. Następnie można wykonać inną akcję w zależności od tego, który przycisk został kliknięty.

## <a name="see-also"></a>Zobacz też

[Deklarowanie funkcji obsługi komunikatów](declaring-message-handler-functions.md)
