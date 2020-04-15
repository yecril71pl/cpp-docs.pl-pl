---
title: Serializacja w MFC
ms.date: 11/04/2016
helpviewer_keywords:
- collection classes [MFC], serialization
- bypassing serialization [MFC]
- MFC, serialization
- serialization [MFC], MFC
- serialization [MFC], bypassing
ms.assetid: fb596a18-4522-47e0-96e0-192732d24c12
ms.openlocfilehash: eca4d0357977bc7ef21063718c738ae5bd8e7431
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372750"
---
# <a name="serialization-in-mfc"></a>Serializacja w MFC

W tym artykule opisano mechanizm serializacji przewidziany w bibliotece klas Programu Microsoft Foundation (MFC), aby umożliwić zachowywanie się obiektów między przebiegami programu.

Serializacja to proces zapisywania lub odczytywania obiektu na trwałym nośniku pamięci, takim jak plik dysku. Serializacja jest idealna dla sytuacji, w których jest pożądane, aby zachować stan danych strukturalnych (takich jak klasy c++ lub struktur) podczas lub po wykonaniu programu. Za pomocą obiektów serializacji dostarczonych przez MFC umożliwia to występuje w sposób standardowy i spójny, zwalniając użytkownika z konieczności wykonywania operacji plików ręcznie.

MFC dostarcza wbudowaną obsługę serializacji w `CObject`klasie . W związku z tym `CObject` wszystkie klasy `CObject`uzyskane z można skorzystać z protokołu serializacji .S

Podstawową ideą serializacji jest to, że obiekt powinien być w stanie zapisać swój bieżący stan, zwykle wskazywany przez wartość jego zmiennych członkowskich, do magazynu trwałego. Później obiekt może być ponownie utworzony przez odczyt lub deserializacji, stan obiektu z magazynu. Serializacja obsługuje wszystkie szczegóły wskaźników obiektów i odwołań cyklicznych do obiektów, które są używane podczas serializacji obiektu. Kluczowym punktem jest to, że sam obiekt jest odpowiedzialny za odczyt i zapis własnego stanu. W związku z tym dla klasy, które mają być serializable, należy zaimplementować podstawowe operacje serializacji. Jak pokazano w grupie serializacji artykułów, łatwo jest dodać tę funkcję do klasy.

MFC używa obiektu `CArchive` klasy jako pośrednika między obiektem, który ma być serializowany, a nośnikiem magazynu. Ten obiekt jest zawsze `CFile` skojarzony z obiektem, z którego uzyskuje informacje niezbędne do serializacji, w tym nazwę pliku i czy żądana operacja jest odczytem lub zapisem. Obiekt, który wykonuje operację serializacji `CArchive` można użyć obiektu bez względu na charakter nośnika magazynu.

Obiekt `CArchive` używa przeciążonych operatorów**<** wstawiania ( ) i ekstrakcji (**>>**) do wykonywania operacji zapisu i odczytu. Aby uzyskać więcej informacji, zobacz [Przechowywanie i ładowanie CObjects za pośrednictwem archiwum](../mfc/storing-and-loading-cobjects-via-an-archive.md) w artykule Serializacja: Serializacji obiektu.

> [!NOTE]
> Nie należy mylić `CArchive` klasy z klasami iostream ogólnego przeznaczenia, które są tylko dla sformatowanego tekstu. Klasa `CArchive` jest dla obiektów serializowanych w formacie binarnym.

Jeśli chcesz, można pominąć serializacji MFC, aby utworzyć własny mechanizm trwałego magazynu danych. Należy zastąpić funkcje członkowskie klasy, które inicjują serializacji za pomocą polecenia użytkownika. Zobacz dyskusję w [notatce technicznej 22](../mfc/tn022-standard-commands-implementation.md) ID_FILE_OPEN, ID_FILE_SAVE i ID_FILE_SAVE_AS standardowych poleceń.

Następujące artykuły obejmują dwa główne zadania wymagane do serializacji:

- [Serializacja: ustawianie klasy jako możliwej do serializacji](../mfc/serialization-making-a-serializable-class.md)

- [Serializacja: serializacja obiektu](../mfc/serialization-serializing-an-object.md)

Artykuł [Serializacja: Serializacja vs wejście/wyjście bazy danych](../mfc/serialization-serialization-vs-database-input-output.md) opisuje, kiedy serializacja jest odpowiednią techniką wejścia/wyjścia w aplikacjach bazy danych.

## <a name="see-also"></a>Zobacz też

[Pojęcia](../mfc/mfc-concepts.md)<br/>
[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)<br/>
[Klasa CArchive](../mfc/reference/carchive-class.md)<br/>
[Klasa CObject](../mfc/reference/cobject-class.md)<br/>
[Klasa CDocument](../mfc/reference/cdocument-class.md)<br/>
[Klasa CFile](../mfc/reference/cfile-class.md)
