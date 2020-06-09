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
ms.openlocfilehash: f47cac34f6cdbdae01af98ec28be5af17edf0e25
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620963"
---
# <a name="bypassing-the-serialization-mechanism"></a>Pomijanie mechanizmu serializacji

Jak widać, struktura zapewnia domyślny sposób odczytywania i zapisywania danych w plikach i. Serializacja przy użyciu obiektu archiwum odpowiada potrzebom dużej liczby aplikacji. Taka aplikacja odczytuje plik w całości do pamięci, pozwala użytkownikowi aktualizować plik, a następnie ponownie zapisuje zaktualizowaną wersję na dysku.

Jednak niektóre aplikacje działają na danych bardzo inaczej i w przypadku serializacji aplikacji za poorednictwem archiwum nie są odpowiednie. Przykłady obejmują programy baz danych, programy, które edytują tylko części dużych plików, programy, które zapisują pliki tekstowe i programy, które współużytkują pliki danych.

W takich przypadkach można zastąpić funkcję [serializacji](reference/cobject-class.md#serialize) w inny sposób, aby skorygować działania plików za pośrednictwem obiektu [CFile](reference/cfile-class.md) , a nie obiektu [CArchive](reference/carchive-class.md) .

Możesz użyć `Open` `Read` funkcji,, `Write` , `Close` i `Seek` elementu członkowskiego klasy, `CFile` Aby otworzyć plik, przenieść wskaźnik pliku (Seek) do określonego punktu w pliku, odczytać rekord (określoną liczbę bajtów) w tym momencie, pozwolić użytkownikowi na aktualizację rekordu, a następnie ponownie przejść do tego samego punktu i zapisać rekord z powrotem do pliku. Struktura otworzy plik i można użyć `GetFile` funkcji składowej klasy, `CArchive` Aby uzyskać wskaźnik do `CFile` obiektu. Aby uzyskać bardziej zaawansowane i elastyczne użycie, można przesłonić funkcje elementów członkowskich [OnOpenDocument](reference/cdocument-class.md#onopendocument) i [OnSaveDocument](reference/cdocument-class.md#onsavedocument) klasy `CWinApp` . Aby uzyskać więcej informacji, zobacz Klasa [CFile](reference/cfile-class.md) w *dokumentacji MFC*.

W tym scenariuszu `Serialize` przesłonięcie nie wykonuje żadnych operacji, chyba że na przykład chcesz odczytywać i zapisywać nagłówek pliku, aby zachować jego aktualność podczas zamykania dokumentu.

## <a name="see-also"></a>Zobacz też

[Używanie dokumentów](using-documents.md)
