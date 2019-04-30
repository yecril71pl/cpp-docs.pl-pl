---
title: Pomijanie mechanizmu serializacji
ms.date: 11/04/2016
helpviewer_keywords:
- archive objects [MFC]
- bypassing serialization
- archives [MFC], serialization
- serialization [MFC], bypassing
- archives [MFC]
- serialization [MFC], role of framework
- serialization [MFC], overriding
ms.assetid: 48d4a279-b51c-4ba5-81cd-ed043312b582
ms.openlocfilehash: 1937098de30884be327c67a698dbb0023be248bb
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345199"
---
# <a name="bypassing-the-serialization-mechanism"></a>Pomijanie mechanizmu serializacji

Jak wiesz już, struktura umożliwia domyślne do odczytu i zapisu danych do i z plików. Serializacja przez obiekt, który archiwum odpowiadających potrzebom bardzo wiele aplikacji. Taką aplikację odczytuje plik całkowicie do pamięci, zezwala użytkownikowi na aktualizowanie pliku, a następnie zapisuje zaktualizowanej wersji na dysku, ponownie.

Jednak niektóre aplikacje działają na danych bardzo różny sposób, a dla tych aplikacji serializacji za pomocą archiwum nie nadaje się. Przykłady obejmują bazy danych programu, programy, które edytować tylko części dużych plików, programy, które zapisać pliki tekstowe i programy, które współużytkują plików danych.

W takich przypadkach można zastąpić [Serialize](../mfc/reference/cobject-class.md#serialize) funkcji w inny sposób, aby zapewnić obsługę akcje plików za pośrednictwem [CFile](../mfc/reference/cfile-class.md) obiektu zamiast [CArchive](../mfc/reference/carchive-class.md) obiektu.

Możesz użyć `Open`, `Read`, `Write`, `Close`, i `Seek` funkcji elementów członkowskich klasy `CFile` próbę otwarcia pliku, przesuń wskaźnik pliku (wyszukiwanie) do określonego punktu w pliku odczytać rekordu (określoną liczbę bajtów ) w tym momencie umożliwiają użytkownikowi zaktualizować rekord, a następnie ponownie dążyć do tego samego punktu i zapisania rekordu z powrotem do pliku. Struktura otworzy plik dla Ciebie i możesz użyć `GetFile` funkcji składowej klasy typu `CArchive` uzyskać wskaźnik do `CFile` obiektu. Na korzystanie z jeszcze bardziej zaawansowane i elastyczne, można zastąpić [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) i [OnSaveDocument](../mfc/reference/cdocument-class.md#onsavedocument) funkcji elementów członkowskich klasy `CWinApp`. Aby uzyskać więcej informacji, zobacz klasy [CFile](../mfc/reference/cfile-class.md) w *odwołanie MFC*.

W tym scenariuszu usługi `Serialize` zastąpienie nie wykonuje żadnych działań, chyba że na przykład chcesz go odczytywać i zapisywać w nagłówku pliku, aby utrzymać ją na bieżąco po zamknięciu dokumentu.

## <a name="see-also"></a>Zobacz także

[Używanie dokumentów](../mfc/using-documents.md)
