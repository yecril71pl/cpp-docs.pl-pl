---
title: Kreator obsługi zdarzeń
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.eventhandler.overview
helpviewer_keywords:
- Event Handler Wizard [C++]
ms.assetid: af8e1835-94b1-4d9a-b353-c519e011d3a1
ms.openlocfilehash: e48d995aed0c59cc4ba7b645706448b5c3618b4a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654171"
---
# <a name="event-handler-wizard"></a>Kreator obsługi zdarzeń

Ten kreator dodaje program obsługi zdarzeń dla formantu pola okna dialogowego do klasy wybranych przez użytkownika. Po dodaniu programu obsługi zdarzeń z [okno właściwości](/visualstudio/ide/reference/properties-window), można go dodać tylko do klasy, która implementuje okno dialogowe. Zobacz [Dodawanie obsługi zdarzeń dla formantów okna dialogowego](../windows/adding-event-handlers-for-dialog-box-controls.md) Aby uzyskać więcej informacji.

- **Nazwa polecenia**

   Identyfikuje zaznaczonego formantu, do którego jest dodawany program obsługi zdarzeń. To pole jest niedostępne.

- **Typ komunikatu**

   Wyświetla listę bieżącej obsługi komunikatów możliwe dla zaznaczonej kontrolki.

- **Nazwa procedury obsługi — funkcja**

   Wyświetla nazwę funkcji, który jest dodawany do obsługi zdarzeń. Domyślnie nazwa opiera się na typ komunikatu i polecenia dołączony przez "Włączone". Na przykład dla przycisku o nazwie `IDC_BUTTON1`, typ komunikatu `BN_CLICKED` Wyświetla nazwę procedury obsługi funkcji `OnBnClickedButton1`.

- **Lista klas**

   Wyświetla dostępne klasy, do których można dodać program obsługi zdarzeń. Klasa wybranego okna dialogowego jest wyświetlany w kolorze czerwonym.

- **Opis procedury obsługi**

   Zawiera opis elementu zaznaczonego w **typ komunikatu** pole. To pole jest niedostępne.

- **Dodawanie i edytowanie**

   Dodaje program obsługi komunikatów do wybranej klasy lub obiekt, a następnie otwiera edytor tekstu na nową funkcję, więc można dodać kod procedury obsługi powiadamiania kontrolki.

- **Edytowanie kodu**

   Zostanie otwarty Edytor tekstów, aby wybrane istniejącą funkcję, dzięki czemu można dodawać lub edytować kod procedury obsługi powiadamiania kontrolki.

## <a name="see-also"></a>Zobacz też

[Dodawanie obsługi zdarzeń](../ide/adding-an-event-handler-visual-cpp.md)