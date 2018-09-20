---
title: Programy obsługi dla zakresów Map komunikatów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ca420ce09cae5bf7c11dcfb0ad384e0002bdc4b1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403584"
---
# <a name="handlers-for-message-map-ranges"></a>Programy obsługi dla zakresów map komunikatów

W tym artykule opisano sposób mapowania szeroką gamę komunikatów do funkcji obsługi pojedynczy komunikat (zamiast mapowanie jeden komunikat do tylko jednej funkcji —).

Są potrzebne do przetwarzania więcej niż jedno powiadomienie wiadomości lub formantu w taki sam sposób. W takich przypadkach może chcesz mapować wszystkie wiadomości do funkcji pojedynczy program obsługi. Zakresy map wiadomości pozwalają w tym celu dla ciągłego zakresu wiadomości:

- Można mapować zakresy identyfikatorów poleceń do:

   - Funkcja obsługi polecenia.

   - Funkcja obsługi polecenia update.

- Powiadamianie kontrolki komunikaty w zakresie kontroli identyfikatorów można mapować do funkcji obsługi wiadomości.

Tematy omówione w tym artykule obejmują:

- [Zapisywanie wpis mapy komunikatów](#_core_writing_the_message.2d.map_entry)

- [Deklarowanie funkcji obsługi](#_core_declaring_the_handler_function)

- [Przykład dla zakresu identyfikatorów poleceń](#_core_example_for_a_range_of_command_ids)

- [Przykład dla zakresu kontroli identyfikatorów](#_core_example_for_a_range_of_control_ids)

##  <a name="_core_writing_the_message.2d.map_entry"></a> Zapisywanie wpis mapy komunikatów

W. CPP Dodaj wpis mapy komunikatów, jak pokazano w poniższym przykładzie:

[!code-cpp[NVC_MFCMessageHandling#6](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]

Wpis mapy komunikatów składa się z następujących elementów:

- Makra mapy komunikatów zakresu:

   - [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)

   - [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)

   - [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)

- Parametry do makra:

     Pierwsze dwa makra nie przyjmują trzy parametry:

   - Identyfikator polecenia, który rozpoczyna zakres

   - Identyfikator polecenia kończącym zakres

   - Nazwa funkcji obsługi wiadomości

     Zakres identyfikatorów poleceń muszą być ciągłe.

     Trzeci makro `ON_CONTROL_RANGE`, zajmuje dodatkowy parametr pierwszy: komunikat powiadamianie kontrolki, takie jak **EN_CHANGE**.

##  <a name="_core_declaring_the_handler_function"></a> Deklarowanie funkcji obsługi

Dodaj swoje obsługi deklaracji funkcji w. Plik H. Poniższy kod pokazuje, jak to wygląda, jak pokazano poniżej:

[!code-cpp[NVC_MFCMessageHandling#7](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_2.h)]

Funkcje programu obsługi dla poleceń pojedynczego zwykle nie mają żadnych parametrów. Z wyjątkiem funkcji obsługi aktualizacji, funkcji obsługi dla zakresów map komunikatów wymagają dodatkowego parametru *nID*, typu **UINT**. Ten parametr jest pierwszym parametrem. Identyfikator polecenia dodatkowe wymagane, aby określić polecenie, które użytkownik faktycznie wybrał jest przystosowana do dodatkowym parametrem.

Aby uzyskać więcej informacji o wymaganiach parametrów dla funkcji obsługi aktualizacji, zobacz [przykład dla zakres polecenia identyfikatorów](#_core_example_for_a_range_of_command_ids).

##  <a name="_core_example_for_a_range_of_command_ids"></a> Przykład polecenia zakres identyfikatorów

Może być zastosowania zakresów przykładem jest obsługi poleceń, takich jak polecenia Powiększenie próbki MFC w [HIERSVR](../visual-cpp-samples.md). To polecenie powiększa widok skalowanie od 25% i % 300 normalne rozmiaru. Klasa widoku HIERSVR firmy używa zakresu do obsługi poleceń powiększenia wpis mapy komunikatów, podobne do tego:

[!code-cpp[NVC_MFCMessageHandling#8](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]

Podczas zapisywania wpisu mapy komunikatów, należy określić:

- Dwa identyfikatory poleceń, rozpoczęcia i zakończenia ciągły zakres.

     Poniżej przedstawiono **ID_VIEW_ZOOM25** i **ID_VIEW_ZOOM300**.

- Nazwa funkcji obsługi dla poleceń.

     W tym miejscu ma `OnZoom`.

Deklaracja funkcji będzie wyglądać następująco:

[!code-cpp[NVC_MFCMessageHandling#9](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_4.h)]

W przypadku funkcji obsługi aktualizacji jest podobny, które mogą być bardziej przydatne. Dość często, aby zapisać `ON_UPDATE_COMMAND_UI` programy obsługi dla pewną liczbę poleceń i okaże się, że pisanie lub kopiowania, ten sam kod wiele razy. Rozwiązaniem jest mapowanie zakresu identyfikatorów do jednej aktualizacji, funkcję obsługi za pomocą polecenia `ON_UPDATE_COMMAND_UI_RANGE` makra. Identyfikatory poleceń muszą tworzyć ciągły zakres. Aby uzyskać przykład, zobacz `OnUpdateZoom` obsługi i jego `ON_UPDATE_COMMAND_UI_RANGE` wpis mapy komunikatów w klasie widoku przykładowe HIERSVR.

Aktualizuj funkcje programu obsługi dla pojedynczego polecenia zwykle przyjmować jeden parametr, *pCmdUI*, typu `CCmdUI*`. W przeciwieństwie do funkcji obsługi aktualizacji funkcji obsługi dla zakresów map komunikatów nie wymagają dodatkowego parametru *nID*, typu **UINT**. Identyfikator polecenia, który jest potrzebny, aby określić, które polecenie, użytkownik faktycznie wybrał, znajduje się w `CCmdUI` obiektu.

##  <a name="_core_example_for_a_range_of_control_ids"></a> Przykład dla identyfikatorów kontrolki zakresu

Inny interesujący przypadek jest mapowanie komunikatów powiadamianie kontrolki w zakresie kontroli identyfikatory pojedynczy program obsługi. Załóżmy, że użytkownik może kliknąć dowolny z 10 przycisków. Aby zamapować wszystkie przyciski 10 do jednego programu obsługi, wpis mapy komunikatów będzie wyglądać następująco:

[!code-cpp[NVC_MFCMessageHandling#10](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]

Podczas wpisywania `ON_CONTROL_RANGE` makro w mapie komunikatów, które można określić:

- Komunikat określonego powiadamianie kontrolki.

     W tym miejscu ma **BN_CLICKED**.

- Wartości Identyfikatora kontrolki skojarzone z ciągły zakres formantów.

     W tym miejscu są **IDC_BUTTON1** i **IDC_BUTTON10**.

- Nazwa funkcji obsługi wiadomości.

     W tym miejscu ma `OnButtonClicked`.

Podczas pisania funkcji obsługi Określ nadmiarowe **UINT** parametru, jak pokazano poniżej:

[!code-cpp[NVC_MFCMessageHandling#11](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]

`OnButtonClicked` Obsługi dla pojedynczego **BN_CLICKED** komunikatu nie przyjmuje żadnych parametrów. Tę samą procedurę obsługi szeregu przycisków ma jedną **UINT**. Dodatkowy parametr umożliwia identyfikowanie określonego formantu odpowiedzialnego za wygenerowanie **BN_CLICKED** wiadomości.

Kodu pokazany w przykładzie jest typowy: Wartość przekazana do konwertowania `int` w ramach zakresu wiadomości i potwierdzające, że jest to możliwe. Następnie może potrwać kilka różne akcje, w zależności od tego, który został kliknięty przycisk.

## <a name="see-also"></a>Zobacz też

[Deklarowanie funkcji obsługi komunikatów](../mfc/declaring-message-handler-functions.md)
