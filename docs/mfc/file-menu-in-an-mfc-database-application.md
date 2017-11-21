---
title: Menu Plik w aplikacji bazy danych MFC | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- File menu
- database applications [MFC], File menu commands
ms.assetid: 92dafb75-c1b3-4860-80a0-87a83bfc36f2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c9e75a88eb4093387317a3cdb84be4b0b73f4201
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="file-menu-in-an-mfc-database-application"></a>Menu Plik w aplikacji bazy danych MFC
Jeśli tworzenie aplikacji bazy danych MFC i nie używaj serializacji, jak należy interpretować otwarte, Zamknij, Zapisz i Zapisz jako polecenia w menu Plik w czasie nie wytyczne dla tego pytania poniżej przedstawiono kilka sugestii:  
  
-   Całkowicie wyeliminować polecenia Otwórz menu Plik.  
  
-   Interpretacji polecenia Otwórz jako "otwartej bazy danych" i wyświetlane użytkownikowi listy źródeł danych, które rozpoznaje aplikacji.  
  
-   Interpretować polecenia Otwórz jako przykład, "otworzyć profilu." Zachować Otwórz Otwieranie pliku serializacji, ale użyj pliku do przechowywania serializacji dokument zawierający informacje "profil użytkownika", takie jak preferencje użytkownika, w tym jego lub jej Identyfikatora logowania (opcjonalnie bez hasła) i danych źródłowych on w najbardziej ostatnio doświadczenie z.  
  
 Kreator aplikacji MFC obsługuje tworzenie aplikacji z żadnych poleceń menu powiązanych z dokumentem pliku. Wybierz **bazy danych widoku bez obsługi plików** opcja **baza danych obsługuje** strony.  
  
 Interpretować polecenia menu Plik w specjalny sposób, konieczne jest przesłonięcie co najmniej jeden programy obsługi poleceń, przede wszystkim w Twojej `CWinApp`-klasy. Na przykład, jeśli całkowicie zastąpić `OnFileOpen` (które implementuje `ID_FILE_OPEN` polecenie) oznacza "otwartej bazy danych:"  
  
-   Nie wywołuj wersja klasy podstawowej `OnFileOpen`, ponieważ jest całkowicie zamieniany framework Domyślna implementacja polecenia.  
  
-   W zamian użyj programu obsługi, aby wyświetlić okno dialogowe Wyświetlanie listy źródeł danych. Można wyświetlić okna dialogowego, wywołując `CDatabase::OpenEx` lub `CDatabase::Open` z parametrem **NULL**. Zostanie otwarte okno dialogowe ODBC, która wyświetla wszystkie dostępne źródła danych na komputerze użytkownika.  
  
-   Ponieważ aplikacje baz danych zwykle nie zapisuj całego dokumentu, prawdopodobnie należy do usunięcia zapisywania i Zapisz jako implementacji, chyba że serializacji dokumentu jest używany do przechowywania informacji o profilu. W przeciwnym razie może zastosować polecenia Zapisz jako, na przykład "zatwierdzić transakcji." Zobacz [22 Uwaga techniczna](../mfc/tn022-standard-commands-implementation.md) Aby uzyskać więcej informacji na temat tych poleceń zastępowanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Serializacja: Serializacja vs. Bazy danych we/wy](../mfc/serialization-serialization-vs-database-input-output.md)

