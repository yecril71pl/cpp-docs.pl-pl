---
title: Kreator klas MFC
ms.date: 09/06/2019
f1_keywords:
- vc.wizards.classwizard
helpviewer_keywords:
- MFC Class Wizard
ms.assetid: 8b0dd867-5d07-4214-99be-2a1c1995e6d9
ms.openlocfilehash: be829156d8fea8188a217b2c0a189ac5d6057a7e
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908007"
---
# <a name="mfc-class-wizard"></a>Kreator klas MFC

Użyj **kreatora klas** , aby utworzyć nowe klasy MFC lub dodać komunikaty i procedury obsługi komunikatów do istniejących klas w projekcie.

Istnieją trzy sposoby otwierania **kreatora klas**:

- W menu **projekt** wybierz **kreatora klas**.
- Wpisz **Ctrl** > ShiftX > .
- W **Widok klasy**kliknij prawym przyciskiem myszy klasę lub węzeł projektu, a następnie wybierz polecenie **Kreator klas**.

![Kreator klas](media/class-wizard.png "Kreator klas MFC")

## <a name="uielement-list"></a>Lista elementów UI

- **Project**

   Nazwa projektu w rozwiązaniu.

   W polu listy rozwijanej można wybrać inne projekty w rozwiązaniu.

- **Nazwa klasy**

   Nazwa klasy w projekcie.

   Po wybraniu klasy z listy **Nazwa klasy** dane z klasy wypełniają formanty w **Kreatorze klas MFC**. Zmiana wartości kontrolki wpłynie na dane w wybranej klasie.

- **Dodaj klasę**

   Umożliwia dodanie nowej klasy do projektu MFC.

- **Klasa bazowa**

   Klasa bazowa klasy, która jest wyświetlana w polu **Nazwa klasy**.

- **Deklaracja klasy**

   Klasa, w której zadeklarowana jest Klasa **nazwy klasy** .

   Pole **deklaracji klasy** jest wyświetlane tylko wtedy, gdy nazwa w niej różni się od nazwy w **implementacji klasy**.

- **Zasób**

   Identyfikator zasobu w **nazwie klasy**, jeśli istnieje. W przeciwnym razie pole **zasobu** jest puste.

- **Implementacja klasy**

   Nazwa pliku, który zawiera implementację klasy w **nazwie klasy**.

   Możesz wybrać inny plik implementacji, klikając strzałkę. W poniższej tabeli wymieniono dostępne opcje.

   |Opcja|Opis|
   |------------|-----------------|
   |**Otwórz plik**|Zamyka kreatora klas i otwiera bieżący plik implementacji klasy.|
   |**Otwórz folder zawierający**|Otwiera folder zawierający bieżący plik implementacji klasy.|
   |**Kopiuj pełną ścieżkę do schowka**|Kopiuje ścieżkę bieżącego pliku implementacji do Schowka.|

- **Polecenia**

   Umożliwia dodawanie, usuwanie, edytowanie lub wyszukiwanie poleceń i obsługi komunikatów.

   Aby dodać procedurę obsługi, kliknij pozycję **Dodaj program obsługi**lub kliknij dwukrotnie element na liście **identyfikatorów obiektów** lub **komunikatów** . Nazwa funkcji, identyfikator i komunikat są wyświetlane na liście **funkcji Członkowskich** .

   Aby usunąć procedurę obsługi, zaznacz element na liście **funkcje członkowskie** , a następnie kliknij polecenie **Usuń procedurę obsługi**.

   Aby zmodyfikować procedurę obsługi, kliknij dwukrotnie odpowiedni element na liście **funkcji Członkowskich** . Lub wybierz element w polu listy, a następnie kliknij pozycję **Edytuj kod**.

- **Komunikaty**

   Umożliwia dodawanie, usuwanie, edytowanie lub wyszukiwanie wiadomości oraz obsługę komunikatów.

   Aby dodać procedurę obsługi, kliknij pozycję **Dodaj obsługę**lub kliknij dwukrotnie element na liście **komunikaty** .

   Aby dodać wiadomość niestandardową, kliknij przycisk **Dodaj wiadomość niestandardową** lub naciśnij klawisz ENTER, a następnie określ wartości w oknie dialogowym **Dodaj komunikat niestandardowy** . W tym oknie dialogowym możesz również wybrać **zarejestrowany komunikat** , aby obsłużyć komunikat okna, który ma być unikatowy w całym systemie operacyjnym.

- **Funkcje wirtualne**

   Umożliwia dodawanie, usuwanie, edytowanie lub Wyszukiwanie funkcji wirtualnej lub przesłoniętą funkcję wirtualną.

- **Zmienne składowe**

   Umożliwia dodawanie, usuwanie, edytowanie lub wyszukiwanie zmiennej składowej.

- **Metody**

   Umożliwia dodanie, usunięcie lub wyszukanie metody, a także przejście do definicji lub deklaracji metody.

   Aby dodać metodę, kliknij przycisk **Dodaj metodę**, a następnie określ wartości w oknie dialogowym **Dodaj metodę** .

   Aby usunąć metodę, wybierz element na liście **metody** , a następnie kliknij pozycję **Usuń metodę**.

   Aby wyświetlić deklarację, wybierz element na liście **metody** , a następnie kliknij pozycję **Przejdź do deklaracji.**

   Aby wyświetlić definicję, kliknij dwukrotnie element na liście **metody** . Lub wybierz element na liście **metody** , a następnie kliknij przycisk **Przejdź do definicji** .

## <a name="see-also"></a>Zobacz także

[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)
