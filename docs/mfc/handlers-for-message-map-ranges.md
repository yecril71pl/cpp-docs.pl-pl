---
title: "Programy obsługi dla zakresów Map komunikatów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 02b44288d21ab2df68468b0e39cb1ee35b7b8810
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2018
---
# <a name="handlers-for-message-map-ranges"></a>Programy obsługi dla zakresów map komunikatów
W tym artykule opisano sposób mapowania zakresu komunikatów do funkcji obsługi wiadomości (zamiast mapowanie jeden komunikat do tylko jednej funkcji).  
  
 Są potrzebne do przetwarzania powiadomienia o więcej niż jeden komunikat lub sterowania w taki sam sposób. W tych godzinach może chcieć zamapować wszystkich komunikatów do funkcji obsługi pojedynczego. Zakresy map wiadomości pozwala to zrobić w ciągły zakres wiadomości:  
  
-   Możesz mapować zakresy identyfikatorów poleceń:  
  
    -   Funkcja obsługi poleceń.  
  
    -   Funkcja obsługi aktualizacji poleceń.  
  
-   Komunikaty powiadomień dotyczących formantu dla zakresu kontroli identyfikatorów można mapować do funkcji obsługi wiadomości.  
  
 Omówione w tym artykule tematy obejmują:  
  
-   [Pisanie wpisu mapy komunikatów](#_core_writing_the_message.2d.map_entry)  
  
-   [Deklarowanie funkcji obsługi](#_core_declaring_the_handler_function)  
  
-   [Przykład dla zakresu identyfikatory poleceń](#_core_example_for_a_range_of_command_ids)  
  
-   [Przykład dla zakresu formantu identyfikatorów](#_core_example_for_a_range_of_control_ids)  
  
##  <a name="_core_writing_the_message.2d.map_entry"></a> Pisanie wpisu mapy komunikatów  
 W. CPP plików, Dodaj wpis mapy komunikatów, jak pokazano w poniższym przykładzie:  
  
 [!code-cpp[NVC_MFCMessageHandling#6](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]  
  
 Wpis mapy komunikatów obejmuje następujące elementy:  
  
-   Makra mapy komunikatów zakresu:  
  
    -   [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)  
  
    -   [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)  
  
    -   [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)  
  
-   Parametry do makra:  
  
     Pierwsze dwie makra podjąć trzy parametry:  
  
    -   Identyfikator polecenia, która rozpoczyna się zakres  
  
    -   Identyfikator polecenia, który kończy się zakres  
  
    -   Nazwa funkcji programu obsługi wiadomości  
  
     Zakres identyfikatorów poleceń musi mieć postać ciągłą.  
  
     Trzeci makra `ON_CONTROL_RANGE`, zajmuje dodatkowy parametr pierwszy: komunikatów powiadomień dotyczących formantu, takich jak **EN_CHANGE**.  
  
##  <a name="_core_declaring_the_handler_function"></a> Deklarowanie funkcji obsługi  
 Dodawanie deklaracji funkcji programu obsługi w. Plik godz. Poniższy kod przedstawia, jak to wygląda, jak pokazano poniżej:  
  
 [!code-cpp[NVC_MFCMessageHandling#7](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_2.h)]  
  
 Funkcje programu obsługi dla poleceń pojedynczego zwykle nie mają żadnych parametrów. Z wyjątkiem funkcji programu obsługi aktualizacji, funkcje programu obsługi dla zakresów map komunikatów wymaga dodatkowego parametru `nID`, typu **UINT**. Ten parametr jest pierwszym parametrem. Dodatkowy parametr bierze pod uwagę identyfikator polecenia dodatkowe wymagane, aby określić polecenie, które faktycznie wybranym przez użytkownika.  
  
 Aby uzyskać więcej informacji o wymaganiach dotyczących parametrów dla funkcji programu obsługi aktualizacji, zobacz [przykład dla zakres polecenia identyfikatorów](#_core_example_for_a_range_of_command_ids).  
  
##  <a name="_core_example_for_a_range_of_command_ids"></a> Przykład dla identyfikatorów zakresu polecenia  
 Może używając zakresów przykładem jest podczas obsługi poleceń, takich jak polecenia Powiększenie w przykładowym MFC [HIERSVR](../visual-cpp-samples.md). To polecenie zmienia Powiększenie widoku skalowanie go od 25% do 300% normalnego rozmiaru. Klasy widoku dla HIERSVR używa zakresu do obsługi poleceń powiększenia do wpisu mapy komunikatów przypominające to:  
  
 [!code-cpp[NVC_MFCMessageHandling#8](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]  
  
 Podczas zapisu mapy komunikatów, należy określić:  
  
-   Dwa identyfikatory poleceń, otwierające i zamykające ciągły zakres.  
  
     Poniżej przedstawiono `ID_VIEW_ZOOM25` i `ID_VIEW_ZOOM300`.  
  
-   Nazwa funkcji obsługi dla poleceń.  
  
     W tym miejscu ma `OnZoom`.  
  
 Deklaracja funkcji będzie wyglądać następująco:  
  
 [!code-cpp[NVC_MFCMessageHandling#9](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_4.h)]  
  
 W przypadku funkcji programu obsługi aktualizacji jest podobny, które mogą być bardziej użyteczne. Dość często zapisu `ON_UPDATE_COMMAND_UI` obsługi pewną liczbę poleceń i okaże się, że zapisywania lub kopiowania, ten sam kod samodzielnego. Rozwiązanie to zmapować zakres identyfikatorów do jednej aktualizacji przy użyciu funkcji obsługi polecenia `ON_UPDATE_COMMAND_UI_RANGE` makra. Identyfikatory poleceń muszą tworzyć ciągły zakres. Na przykład zobacz **OnUpdateZoom** obsługi i jego `ON_UPDATE_COMMAND_UI_RANGE` wpisu mapy wiadomości w klasie widoku próbki HIERSVR.  
  
 Zaktualizuj funkcje programu obsługi dla pojedynczego polecenia zwykle mają jeden parametr `pCmdUI`, typu **CCmdUI\***. W przeciwieństwie do funkcji programu obsługi aktualizacji funkcji programu obsługi dla zakresów map komunikatów nie wymagają dodatkowy parametr `nID`, typu **UINT**. Identyfikator polecenia, który jest wymagany do określenia, które polecenia faktycznie wybranym przez użytkownika, znajduje się w `CCmdUI` obiektu.  
  
##  <a name="_core_example_for_a_range_of_control_ids"></a> Przykład dla identyfikatorów kontrolki zakresu  
 Innym przypadku interesujące jest mapowanie komunikatów powiadomień dotyczących formantu zakresu kontroli identyfikatorów do pojedynczego programu obsługi. Załóżmy, że użytkownik może kliknąć jeden z przycisków 10. Aby mapować wszystkie przyciski 10 jednej procedury obsługi, wpis mapy wiadomości będzie wyglądać następująco:  
  
 [!code-cpp[NVC_MFCMessageHandling#10](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]  
  
 Podczas zapisu `ON_CONTROL_RANGE` makro na mapie komunikatów, określ:  
  
-   Komunikat określonego powiadomień dotyczących formantu.  
  
     W tym miejscu ma **BN_CLICKED**.  
  
-   Wartości Identyfikatora formantu skojarzone z ciągły zakres kontrolki.  
  
     W tym miejscu są `IDC_BUTTON1` i `IDC_BUTTON10`.  
  
-   Nazwa funkcji obsługi wiadomości.  
  
     W tym miejscu ma `OnButtonClicked`.  
  
 Podczas pisania funkcji obsługi Określ nadmiarowe **UINT** parametru, jak pokazano poniżej:  
  
 [!code-cpp[NVC_MFCMessageHandling#11](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]  
  
 `OnButtonClicked` Obsługi z jednym **BN_CLICKED** wiadomości nie przyjmuje żadnych parametrów. Program obsługi tego samego zakresu przycisków przyjmuje jeden **UINT**. Dodatkowy parametr umożliwia identyfikowanie określonego formantu odpowiedzialny za wygenerowanie **BN_CLICKED** wiadomości.  
  
 Kodu pokazano w przykładzie jest typowy: konwertowanie wartości przekazanych do `int` w zakresie wiadomości i potwierdzające, że jest to możliwe. Następnie może potrwać niektórych inną akcję w zależności od tego, który został kliknięty przycisk.  
  
## <a name="see-also"></a>Zobacz też  
 [Deklarowanie funkcji obsługi komunikatów](../mfc/declaring-message-handler-functions.md)
