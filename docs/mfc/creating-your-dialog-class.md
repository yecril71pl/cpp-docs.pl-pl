---
title: Tworzenie klasy okien dialogowych
ms.date: 09/06/2019
helpviewer_keywords:
- dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- files [MFC], creating
- dialog classes [MFC], Add Class Wizard
- dialog classes [MFC], creating
ms.assetid: d5321741-da41-47a8-bb1c-6a0e8b28c4c1
ms.openlocfilehash: 424d18196063456245e2a4841b42e6e447bded17
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907326"
---
# <a name="creating-your-dialog-class"></a>Tworzenie klasy okien dialogowych

Dla każdego okna dialogowego w programie Utwórz nową klasę okna dialogowego do pracy z zasobem okna dialogowego.

[Dodanie klasy](../ide/adding-a-class-visual-cpp.md) wyjaśnia, jak utworzyć nową klasę okna dialogowego. Podczas tworzenia klasy okien dialogowych za pomocą [kreatora klas](reference/mfc-class-wizard.md)zapisuje następujące elementy w określonych plikach. h i. cpp:

W pliku h:

- Deklaracja klasy dla klasy okna dialogowego. Klasa pochodzi od [CDialog](../mfc/reference/cdialog-class.md).

W pliku. cpp:

- Mapa komunikatów dla klasy.

- Standardowy Konstruktor dla okna dialogowego.

- Przesłonięcie funkcji składowej [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) . Edytuj tę funkcję. Służy do wymiany i sprawdzania poprawności danych w oknie dialogowym zgodnie z opisem w dalszej części [okna dialogowego wymiana danych i sprawdzanie poprawności](../mfc/dialog-data-exchange-and-validation.md).

## <a name="see-also"></a>Zobacz także

[Tworzenie klasy okien dialogowych za pomocą kreatorów kodu](../mfc/creating-a-dialog-class-with-code-wizards.md)<br/>
[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)
