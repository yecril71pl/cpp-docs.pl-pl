---
title: Menu Plik w aplikacji bazy danych MFC
ms.date: 11/04/2016
helpviewer_keywords:
- File menu
- database applications [MFC], File menu commands
ms.assetid: 92dafb75-c1b3-4860-80a0-87a83bfc36f2
ms.openlocfilehash: fbbb4382749278708e8e758f79a618d5cad0549e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615703"
---
# <a name="file-menu-in-an-mfc-database-application"></a>Menu Plik w aplikacji bazy danych MFC

W przypadku tworzenia aplikacji bazy danych MFC i nie używania serializacji, jak należy interpretować polecenia Otwórz, Zamknij, Zapisz i Zapisz jako w menu plik, gdy nie ma żadnych wytycznych dotyczących stylu dla tego pytania, poniżej przedstawiono kilka sugestii:

- Usuń całkowicie polecenie otwarcia menu plik.

- Interpretuj polecenie Otwórz jako "Otwórz bazę danych" i Pokaż użytkownikowi listę źródeł danych rozpoznawanych przez aplikację.

- Interpretuj polecenie Open jako, prawdopodobnie "Otwórz profil". Zachowaj otwarte, aby otworzyć serializowany plik, ale Użyj pliku do przechowywania zserializowanego dokumentu zawierającego informacje o profilu użytkownika, takie jak preferencje użytkownika, w tym jego identyfikator logowania (opcjonalnie z wyłączeniem hasła) i źródło danych, które ostatnio pracował.

Kreator aplikacji MFC obsługuje tworzenie aplikacji bez poleceń menu plik związanych z dokumentem. Wybierz opcję **Widok bazy danych bez obsługi plików** na stronie **Obsługa bazy danych** .

Aby interpretować polecenie menu plik w specjalny sposób, należy zastąpić jeden lub więcej programów obsługi poleceń, głównie w `CWinApp` klasie pochodnej. Jeśli na przykład całkowicie przesłonisz `OnFileOpen` (implementując `ID_FILE_OPEN` polecenie), oznacza to, że "Open Database:"

- Nie wywołuj wersji klasy bazowej `OnFileOpen` , ponieważ jest całkowicie zastępowana domyślna implementacja struktury polecenia.

- Użyj zamiast tego programu obsługi, aby wyświetlić okno dialogowe z listą źródeł danych. Możesz wyświetlić takie okno dialogowe, wywołując `CDatabase::OpenEx` lub `CDatabase::Open` z parametrem **null**. Spowoduje to otwarcie okna dialogowego ODBC, w którym są wyświetlane wszystkie dostępne źródła danych na komputerze użytkownika.

- Ponieważ aplikacje bazy danych zazwyczaj nie zapisują całego dokumentu, prawdopodobnie zechcesz usunąć implementacje Zapisz i Zapisz jako, chyba że używasz serializowanego dokumentu do przechowywania informacji o profilu. W przeciwnym razie można zaimplementować polecenie Zapisz jako, na przykład "Zatwierdź transakcję". Aby uzyskać więcej informacji na temat przesłaniania tych poleceń, zobacz [Uwaga techniczna 22](tn022-standard-commands-implementation.md) .

## <a name="see-also"></a>Zobacz też

[Serializacja: serializacja a dane wejściowe/wyjściowe bazy danych](serialization-serialization-vs-database-input-output.md)
