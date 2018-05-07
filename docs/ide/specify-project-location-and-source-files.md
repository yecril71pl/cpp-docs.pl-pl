---
title: Nowy projekt z istniejących źródeł - pliki źródłowe (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.importwiz.location
dev_langs:
- C++
ms.assetid: 29ddffb9-5918-4d72-8c7a-a365f9de96dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d85a7b85996ed307596865a31d55cf4b119e5bd5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="specify-project-location-and-source-files-create-new-project-from-existing-code-files-wizard"></a>Określ lokalizację projektu i plików źródłowych, Kreator Utwórz nowy projekt z istniejących plików z kodem
Umożliwia określenie tej strony kreator Utwórz nowy projekt z istniejących plików kodu:  
  
-   Ścieżka katalogu nowego projektu  
  
-   Katalogi wyszukiwania istniejących plików źródłowych  
  
-   Typy plików kreatora zostaną zaimportowane do nowego projektu  
  
## <a name="task-list"></a>Lista zadań  
 [Instrukcje: tworzenie projektu C++ z istniejącego kodu](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Lokalizacja pliku projektu**  
 Określa ścieżkę katalogu nowego projektu. Ta lokalizacja jest, gdzie Kreator będzie złożenia wszystkich plików (i jego podkatalogach) nowy projekt.  
  
 **Przeglądaj**  
 Wyświetla **lokalizacja pliku projektu** okno dialogowe, które pomaga określić katalog, który będzie zawierać nowy projekt. Ten formant umożliwia przejdź do żądanego folderu.  
  
 **Nazwa projektu**  
 Określa nazwę nowego projektu. Pliki projektu, które mają rozszerzenia plików, takich jak .vcxproj przyjmie tej nazwy. Istniejących plików kodu będzie przechowywać ich oryginalną nazwę.  
  
 **Dodaj pliki do projektu z tych folderów**  
 Po zaznaczeniu tej opcji, ustawia kreatora, aby skopiować istniejących plików kodu z ich oryginalnego katalogów (które są określone na liście poniżej tego formantu) do nowego projektu.  
  
 **Dodaj podfoldery**  
 Określa, aby skopiować pliki kodu z wszystkie podkatalogi katalogu wymienione **folderu** kolumny do nowego projektu.  
  
 **Folder**  
 Określa ścieżkę do katalogu zawierającego istniejących plików kodu ma zostać skopiowany do nowego projektu. Ta kolumna zawiera wszystkie katalogi, które kreator umożliwia wyszukiwanie istniejących plików kodu.  
  
 **Dodaj**  
 Wyświetla **Dodaj pliki do projektu z tego folderu** okno dialogowe, które pomaga katalogi Określ, które kreator umożliwia wyszukiwanie istniejących plików kodu.  
  
 **Usuń**  
 Usuwa ścieżki katalogu, który wybrano w lewo pole listy tego formantu.  
  
 **Typy plików do dodania do projektu**  
 Określa typy plików, które kreator doda do nowego projektu na podstawie rozszerzeń danego pliku. Rozszerzenia plików są poprzedzone znaku wieloznacznego gwiazdki i są rozdzielane na liście rozszerzeń nazw plików średnikiem.  
  
 **Pokaż wszystkie pliki w Eksploratorze rozwiązań**  
 Określa, że wszystkie pliki w nowym projekcie być widoczne i wyświetlane w oknie Eksploratora rozwiązań. Ta opcja jest domyślnie włączona.