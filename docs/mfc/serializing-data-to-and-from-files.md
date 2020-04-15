---
title: Serializacja danych do plików i z plików
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], serialization
- documents [MFC], saving
- saving documents
- deserialization [MFC]
- serialization [MFC], role of document
- serialization [MFC], role of data
- data [MFC]
- data [MFC], serializing
- document data [MFC]
ms.assetid: b42a0c68-4bc4-4012-9938-5433a26d2c24
ms.openlocfilehash: 043ba019c6b5ad79db2cedb6314c9e65f14b14b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376933"
---
# <a name="serializing-data-to-and-from-files"></a>Serializacja danych do plików i z plików

Podstawową ideą trwałości jest to, że obiekt powinien być w stanie zapisać swój bieżący stan, wskazany przez wartości jego zmiennych członkowskich, do magazynu trwałego. Później obiekt może być ponownie utworzony przez odczyt lub "deserializing", stan obiektu z magazynu trwałego. Kluczowym punktem jest to, że sam obiekt jest odpowiedzialny za odczyt i zapis własnego stanu. W związku z tym dla klasy, aby być trwałe, należy zaimplementować podstawowe operacje serializacji.

Struktura zapewnia domyślną implementację zapisywania dokumentów do plików dyskowych w odpowiedzi na polecenia Zapisz i Zapisz jako w menu Plik oraz do ładowania dokumentów z plików dyskowych w odpowiedzi na polecenie Otwórz. Przy bardzo małej pracy można zaimplementować zdolność dokumentu do pisania i odczytywania jego danych do i z pliku. Najważniejsze, co należy zrobić, to zastąpić [funkcja element członkowski Serialize](../mfc/reference/cobject-class.md#serialize) w klasie dokumentu.

Kreator aplikacji MFC umieszcza szkieletowe zastąpienie funkcji `CDocument` `Serialize` elementu członkowskiego w klasie dokumentu, którą tworzy dla Ciebie. Po zaimplementowaniu zmiennych członkowskich aplikacji można wypełnić `Serialize` zastąpienie kodem, który wysyła dane do "obiektu archiwum" połączonego z plikiem. A [CArchive](../mfc/reference/carchive-class.md) obiekt jest podobny do **cin** i **cout** input/output obiektów z biblioteki iostream C++. Jednak `CArchive` pisze i odczytuje format binarny, a nie sformatowany tekst.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz wiedzieć więcej o

- [Serializacja](../mfc/serialization-in-mfc.md)

- [Rola dokumentu w serializacji](#_core_the_document.92.s_role_in_serialization)

- [Rola danych w serializacji](#_core_the_data.92.s_role_in_serialization)

- [Pomijanie mechanizmu serializacji](../mfc/bypassing-the-serialization-mechanism.md)

## <a name="the-documents-role-in-serialization"></a><a name="_core_the_document.92.s_role_in_serialization"></a>Rola dokumentu w serializacji

Struktura odpowiada automatycznie do menu Plik Otwórz, Zapisz i Zapisz jako polecenia, wywołując `Serialize` funkcję elementu członkowskiego dokumentu, jeśli jest zaimplementowana. Polecenie ID_FILE_OPEN, na przykład wywołuje funkcję obsługi w obiekcie aplikacji. Podczas tego procesu użytkownik widzi i odpowiada na okno dialogowe Otwieranie plików, a struktura uzyskuje nazwę pliku, który użytkownik wybierze. Struktura tworzy `CArchive` obiekt skonfigurowany do ładowania danych do dokumentu `Serialize`i przekazuje archiwum do programu . Struktura już otworzyła plik. Kod w funkcji `Serialize` członkowskiej dokumentu odczytuje dane za pośrednictwem archiwum, rekonstruując obiekty danych w razie potrzeby. Aby uzyskać więcej informacji na temat serializacji, zobacz artykuł [Serializacja](../mfc/serialization-in-mfc.md).

## <a name="the-datas-role-in-serialization"></a><a name="_core_the_data.92.s_role_in_serialization"></a>Rola danych w serializacji

Ogólnie rzecz biorąc dane typu klasy powinny być w stanie serializować się. Oznacza to, że po przedaniu obiektu do archiwum obiekt powinien wiedzieć, jak zapisać się do archiwum i jak czytać się z archiwum. MFC zapewnia obsługę tworzenia klas serializable w ten sposób. Jeśli projektujesz klasę w celu zdefiniowania typu danych i zamierzasz serializować dane tego typu, zaprojektuj serializację.

## <a name="see-also"></a>Zobacz też

[Używanie dokumentów](../mfc/using-documents.md)
