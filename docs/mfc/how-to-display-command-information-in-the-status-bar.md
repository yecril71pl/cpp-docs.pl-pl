---
title: 'Porady: wyświetlanie informacji o poleceniu na pasku stanu jest | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- prompts [MFC]
- displaying command status [MFC]
- status bars [MFC], message area
- status bars [MFC], displaying command information
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 089e0fd8f1853a4e219309c0df7659f90e4f4b3d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405752"
---
# <a name="how-to-display-command-information-in-the-status-bar"></a>Porady: wyświetlanie informacji o poleceniu na pasku stanu

Po uruchomieniu Kreatora aplikacji, aby utworzyć szkielet aplikacji, możesz korzystać z paska narzędzi i pasek stanu. Tylko jedną z opcji w Kreatorze aplikacji obsługuje obie. Pasek stanu jest obecny, aplikacja automatycznie zapewnia przydatne opinii gdy użytkownik przesuwa wskaźnik myszy nad elementami na pasku menu. Program automatycznie wyświetla ciąg monitu na pasku stanu wyróżnionego elementu menu. Na przykład, gdy użytkownik przesuwa wskaźnik myszy **Wytnij** polecenie **Edytuj** menu na pasku stanu może być wyświetlany w obszarze wiadomości w pasku stanu "Wycina zaznaczenie i umieszcza je w Schowku". Monit pomaga użytkownika zrozumienie przeznaczenia elementu menu. Działa to również, gdy użytkownik kliknie przycisk paska narzędzi.

Możesz dodać tę pomoc pasek stanu, definiując monitu ciągi dla elementów menu, które dodajesz do programu. Aby to zrobić, podaj ciągi monitu podczas edytowania właściwości elementu menu, w edytorze menu. Ciągi znaków, jaką zdefiniujesz są przechowywane w pliku zasobów aplikacji; mają one takich samych identyfikatorów jako polecenia, które zawierają one objaśnienia.

Domyślnie Kreator aplikacja dodaje **AFX_IDS_IDLEMESSAGE**, identyfikator standardową wiadomość "Gotowe", która jest wyświetlana, gdy program oczekuje na nowe wiadomości. Jeśli określisz opcję Context-Sensitive Help w Kreatorze aplikacji wiadomości zostanie zmieniony na "Aby uzyskać pomoc, naciśnij klawisz F1".

## <a name="see-also"></a>Zobacz też

[Obsługa i mapowanie komunikatów](../mfc/message-handling-and-mapping.md)

