---
title: Kreator klas MFC
ms.date: 11/04/2016
f1_keywords:
- vc.wizards.classwizard
helpviewer_keywords:
- wizards (MFC)
- MFC Class Wizard
ms.assetid: 8b0dd867-5d07-4214-99be-2a1c1995e6d9
ms.openlocfilehash: 59f0b39afe467267d61d7b851e654cc8bddc7b36
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412731"
---
# <a name="mfc-class-wizard"></a>Kreator klas MFC

Umożliwia dodanie komunikaty i procedury obsługi komunikatów do klas w projekcie. Można również uruchamiania kreatorów innych lub dodać klasę do projektu.

Aby otworzyć **Kreator klas MFC**na **projektu** menu, kliknij przycisk **Kreator klas**. Aby otworzyć kreatora, za pomocą skrótu klawiaturowego, należy wpisać CTRL + SHIFT + X.

## <a name="uielement-list"></a>Lista elementów UI

- **Project**

   Nazwa projektu w rozwiązaniu.

   Możesz wybrać inne projekty w rozwiązaniu w polu listy rozwijanej.

- **Nazwa klasy**

   Nazwa klasy w projekcie.

   Po wybraniu klasy w **Nazwa klasy** listy wypełnienie danych z klasy kontrolek w **Kreator klas MFC**. Po zmianie wartości formantu w wybranej klasy to miało wpływu na dane.

- **Dodaj klasę**

   Umożliwia dodawanie klasy z jednego z wielu źródeł.

   W zależności od wybranej opcji **Kreator dodawania klasy w MFC**, **klasy z Typelib Kreatora dodawania**, **dodawania klasy z Kreatora kontrolek ActiveX**, lub **MFC ODBC Kreator konsumenta** została uruchomiona.

- **Klasa bazowa**

   Klasa bazowa klasa, która jest wyświetlana w **Nazwa klasy**.

- **Deklaracja klasy**

   Klasy, w której **Nazwa klasy** zadeklarowano klasę.

   **Deklarację klasy** pojawia się tylko wtedy, gdy nazwa w niej różni się od nazwy **Implementacja klasy**.

- **Zasób**

   Identyfikator zasobu w **Nazwa klasy**, jeśli są dostępne. W przeciwnym razie **zasobów** pole jest puste.

- **Implementacja klasy**

   Nazwa pliku, który zawiera implementację klasy w **Nazwa klasy**.

   Plik inną implementację można wybrać, klikając strzałkę. Poniższa tabela zawiera listę dostępnych opcji.

   |Opcja|Opis|
   |------------|-----------------|
   |**Otwórz plik**|Zamyka Kreator klas i otwiera bieżącego pliku implementacji klasy.|
   |**Otwórz Folder zawierający**|Zostanie otwarty folder, który zawiera bieżącego pliku implementacji klasy.|
   |**Kopiuj pełną ścieżkę do Schowka**|Ścieżka bieżącego pliku implementacji kopiuje do Schowka.|

- **Polecenia**

   Pozwala dodać, usunąć, edytować lub Wyszukaj polecenie i jego obsługi wiadomości.

   Aby dodać program obsługi, kliknij **Dodaj obsługę**, lub kliknij dwukrotnie element **identyfikatory obiektów** listy lub **wiadomości** listy. Wynikowa nazwa funkcji, identyfikator i wiadomości są wyświetlane w **elementów członkowskich** listy.

   Aby usunąć program obsługi, wybierz element w **elementów członkowskich** listy, a następnie kliknij przycisk **usuwania programu obsługi**.

   Aby zmodyfikować program obsługi, kliknij dwukrotnie odpowiedni element na **elementów członkowskich** listy. Lub, zaznacz element w polu listy, a następnie kliknij przycisk **Edytuj kod**.

- **Komunikaty**

   Pozwala dodać, usunąć, edytować lub Wyszukaj komunikat i jego obsługi wiadomości.

   Aby dodać program obsługi, kliknij **Dodaj obsługę**, lub kliknij dwukrotnie element **wiadomości** listy.

   Aby dodać niestandardowy komunikat, kliknij **dodać niestandardowy komunikat** lub naciśnij klawisz Enter, a następnie określ wartości w **dodać niestandardowy komunikat** okno dialogowe. W tym oknie dialogowym możesz również wybrać **zarejestrowany komunikat** do obsługi komunikatów okien, która może być unikatowe w obrębie całej systemu operacyjnego.

- **Funkcje wirtualne**

   Umożliwia dodawanie, usuwanie, edytować lub wyszukiwanie funkcję wirtualną lub zastąpiona funkcja wirtualna.

- **Zmienne Członkowskie**

   Umożliwia dodawanie, usuwanie, edytować lub Wyszukaj zmienną składową.

- **Metody**

   Pozwala dodać, usunąć, lub Wyszukaj metody, a także przejść do definicji lub deklaracji metody.

   Aby dodać metodę, kliknij przycisk **Dodaj metodę**, a następnie określ wartości w **Dodaj metodę** okno dialogowe.

   Aby usunąć metodę, wybierz element w **metody** listy, a następnie kliknij przycisk **Usuń metodę**.

   Aby wyświetlić deklarację, zaznacz element w **metody** listy, a następnie kliknij przycisk **przejdź do deklaracji.**

   Aby wyświetlić definicji, kliknij dwukrotnie element **metody** listy. Lub wybierz element w **metody** listy, a następnie kliknij przycisk **przejdź do definicji** przycisku.

## <a name="see-also"></a>Zobacz także

[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)
