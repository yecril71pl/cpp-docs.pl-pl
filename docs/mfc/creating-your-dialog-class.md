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
ms.openlocfilehash: bacedc49fcdabdd5dc7fb0f392a66afd3baadd06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241768"
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

## <a name="see-also"></a>Zobacz także

[Tworzenie klasy okien dialogowych za pomocą kreatorów kodu](../mfc/creating-a-dialog-class-with-code-wizards.md)<br/>
[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)
