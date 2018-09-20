---
title: Nowy projekt z istniejącego kodu — pliki źródłowe (Visual C++) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: e2d33f4dbe852b7f9a64f59b44af9fbb4f8eb12c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403919"
---
# <a name="specify-project-location-and-source-files-create-new-project-from-existing-code-files-wizard"></a>Określ lokalizację projektu i plików źródłowych, Kreator Utwórz nowy projekt z istniejących plików z kodem

Użyj tej strony kreator Utwórz nowy projekt z istniejących plików kodu, aby określić:

- Ścieżka katalogu nowego projektu

- Katalogi do wyszukiwania dla istniejących plików źródłowych

- Rodzaje plików kreatora zostaną zaimportowane do nowego projektu

## <a name="task-list"></a>Lista zadań

[Instrukcje: tworzenie projektu C++ z istniejącego kodu](../ide/how-to-create-a-cpp-project-from-existing-code.md)

## <a name="uielement-list"></a>Lista elementów UI

- **Lokalizacja pliku projektu**

   Określa ścieżkę katalogu nowy projekt. Ta lokalizacja jest, w której Kreator będzie złożenia, wszystkie pliki (i podkatalogi) nowego projektu.

- **Przeglądaj**

   Wyświetla **lokalizacja pliku projektu** okno dialogowe, które pomaga określić katalog, który będzie zawierać nowy projekt. Ten formant umożliwia przejdź do żądanego folderu.

- **Nazwa projektu**

   Określa nazwę nowego projektu. Pliki projektu, które mają rozszerzenia pliku, takie jak vcxproj przyjmie tej nazwy. Istniejących plików kodu zostanie zachowana, aby ich oryginalną nazwę.

- **Dodaj pliki do projektu z tych folderów**

   Po zaznaczeniu tej opcji, ustawia pracę kreatora Aby skopiować istniejących plików kodu z ich oryginalnego katalogów, (które są określone w polu listy poniżej tego formantu) do nowego projektu.

- **Dodaj podfoldery**

   Określa, aby skopiować pliki kodu z wszystkie podkatalogi katalogu wymienione **folderu** kolumny do nowego projektu.

- **Folder**

   Określa ścieżkę do katalogu, który zawiera istniejących plików kodu, aby skopiować do nowego projektu. Ta kolumna zawiera listę wszystkich katalogów, które kreator umożliwia wyszukiwanie istniejących plików kodu.

- **Add**

   Wyświetla **Dodaj pliki do projektu z tego folderu** okno dialogowe, które ułatwi Ci katalogi Określ, które kreator umożliwia wyszukiwanie istniejących plików kodu.

- **Usuń**

   Usuwa ścieżkę katalogu wybranego na liście pole po lewej stronie tej kontrolki.

- **Typy plików do dodania do projektu**

   Określa typy plików, które kreator doda do nowego projektu na podstawie rozszerzeń danego pliku. Rozszerzenia plików są poprzedzone znakiem symbol wieloznaczny gwiazdka i są rozdzielane na liście rozszerzeń plików średnikiem.

- **Pokaż wszystkie pliki w Eksploratorze rozwiązań**

   Określa, że wszystkie pliki w nowym projekcie jako widoczny i wyświetlane w oknie Eksploratora rozwiązań. Ta opcja jest domyślnie włączona.