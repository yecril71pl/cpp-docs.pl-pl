---
title: Menu Plik w aplikacji bazy danych MFC
ms.date: 11/04/2016
helpviewer_keywords:
- File menu
- database applications [MFC], File menu commands
ms.assetid: 92dafb75-c1b3-4860-80a0-87a83bfc36f2
ms.openlocfilehash: ce56dd5f04312ae9e7b7f747ce81cb704f3d085d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629206"
---
# <a name="file-menu-in-an-mfc-database-application"></a>Menu Plik w aplikacji bazy danych MFC

Jeśli tworzenie aplikacji bazy danych MFC i nie należy używać serializacji, jak należy interpretować otwarte, Zamknij, Zapisz i Zapisz jako polecenia w menu Plik podczas nie wskazówki dotyczące stylu na to pytanie, poniżej przedstawiono kilka propozycji:

- Całkowicie wyeliminować polecenia Otwórz menu Plik.

- Interpretować polecenia Otwórz jako "otwarte bazy danych" i wyświetlanie listy źródeł danych, które rozpoznaje aplikacji użytkownika.

- Interpretowanie polecenie Otwórz, być może, "otwarte profilu." Zachowaj Otwórz plik Otwieranie pliku serializacji, ale służy do przechowywania Zserializowany dokument zawierający informacje "profil użytkownika", takie jak preferencje użytkownika, w tym jego lub jej identyfikator logowania (opcjonalnie bez hasła) i danych źródłowych on w najbardziej ostatnio pracowano.

Kreator aplikacji MFC obsługuje tworzenie aplikacji z nie polecenia menu Plik związanych z dokumentami. Wybierz **bazy danych w widoku bez obsługi plików** opcja **baza danych obsługuje** strony.

Interpretowanie polecenia menu Plik w specjalny sposób, konieczne jest przesłonięcie co najmniej jeden programy obsługi poleceń, przede wszystkim w Twojej `CWinApp`-klasy pochodnej. Na przykład, jeśli zastąpienie całkowicie `OnFileOpen` (który implementuje `ID_FILE_OPEN` polecenie) oznacza "otwartej bazy danych:"

- Nie wywołuj klasy bazowej wersję `OnFileOpen`, ponieważ całkowicie wymianie struktury Domyślna implementacja polecenia.

- Zamiast tego użyj programu obsługi, aby wyświetlić okno dialogowe, wyświetlanie listy źródeł danych. Można wyświetlić okna dialogowego, wywołując `CDatabase::OpenEx` lub `CDatabase::Open` z parametrem **NULL**. Zostanie otwarte okno dialogowe ODBC, który wyświetla wszystkie dostępne źródła danych na komputerze użytkownika.

- Ponieważ aplikacje baz danych zwykle nie zapisuj cały dokument, prawdopodobnie należy usunąć zapisywania i Zapisz jako implementacji, chyba że używasz Dokument zserializowany do przechowywania informacji o profilu. W przeciwnym razie może zaimplementować polecenia Zapisz jako, na przykład "commit transakcji." Zobacz [techniczne 22 Uwaga](../mfc/tn022-standard-commands-implementation.md) Aby uzyskać więcej informacji o zastępowanie tych poleceń.

## <a name="see-also"></a>Zobacz też

[Serializacja: serializacja a Dane wejściowe/wyjściowe bazy danych](../mfc/serialization-serialization-vs-database-input-output.md)

