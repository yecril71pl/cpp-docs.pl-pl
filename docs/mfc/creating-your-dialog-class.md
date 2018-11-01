---
title: Tworzenie klasy okien dialogowych
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- files [MFC], creating
- dialog classes [MFC], Add Class Wizard
- dialog classes [MFC], creating
ms.assetid: d5321741-da41-47a8-bb1c-6a0e8b28c4c1
ms.openlocfilehash: 924cf2d79056d958aad775f92a6d0df2d45c8a70
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536584"
---
# <a name="creating-your-dialog-class"></a>Tworzenie klasy okien dialogowych

Dla każdego okna dialogowego w swoim programie Utwórz nową klasę okna dialogowego do pracy z zasobu okna dialogowego.

[Dodawanie klasy](../ide/adding-a-class-visual-cpp.md) wyjaśnia, jak utworzyć nową klasę okna dialogowego. Po utworzeniu klasy okien dialogowych za pomocą Kreatora dodawania klasy zapisuje następujące elementy w. Godz. i. CPP określone pliki:

W. Plik H:

- Deklarację klasy dla klasy okien dialogowych. Klasa jest pochodną [CDialog](../mfc/reference/cdialog-class.md).

W. Plik CPP:

- Mapy komunikatów dla klasy.

- Konstruktor standardowy dla okna dialogowego.

- Zastępowanie [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) funkcja elementu członkowskiego. Edytuj tę funkcję. Jest on używany do możliwości wymiana i Walidacja danych okna dialogowego, zgodnie z opisem w dalszej części w [wymiana danych okna dialogowego i sprawdzanie poprawności](../mfc/dialog-data-exchange-and-validation.md).

## <a name="see-also"></a>Zobacz też

[Tworzenie klasy okien dialogowych za pomocą kreatorów kodu](../mfc/creating-a-dialog-class-with-code-wizards.md)<br/>
[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

