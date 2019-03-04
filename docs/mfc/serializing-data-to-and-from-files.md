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
ms.openlocfilehash: af3cde9445ae4b128e7e54a5f154db01b2eecd3b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279266"
---
# <a name="serializing-data-to-and-from-files"></a>Serializacja danych do plików i z plików

Podstawowa koncepcja trwałości jest, czy obiekt powinien móc zapisać jego bieżący stan wskazywanym przez wartości swoje zmienne elementu członkowskiego w magazynie trwałym. Później obiekt można ponownie utworzyć poprzez czytanie, lub "podczas deserializacji," stan obiektu z magazynu trwałego. Kluczowym punktem tutaj jest odpowiedzialna za odczytywanie i zapisywanie własną stan samego obiektu. W związku z tym dla klasy były trwałe, musi on implementować operacje podstawowe serializacji.

Struktura udostępnia domyślną implementację interfejsu do zapisywania dokumentów do plików dysku w odpowiedzi do zapisywania i Zapisz jako polecenia w menu Plik i ładowanie dokumentów z dysku w odpowiedzi na polecenie Otwórz. Dzięki bardzo małego wysiłku można zaimplementować dokumentu możliwość zapisu i odczytu jego danych do i z pliku. Główne rzeczą, należy wykonać, jest zastąpienie [Serialize](../mfc/reference/cobject-class.md#serialize) funkcja elementu członkowskiego w klasie dokumentów.

Kreator aplikacji MFC umieszcza szkieletowych zastępowania metody `CDocument` funkcja elementu członkowskiego `Serialize` w klasie dokumentów, tworzy dla Ciebie. Po udało Ci się wdrożyć zmienne Członkowskie swojej aplikacji, możesz wpisać w swojej `Serialize` zastąpienia z kodem, który wysyła dane do "obiektu archiwum" połączony z plikiem. A [CArchive](../mfc/reference/carchive-class.md) obiektu jest podobny do **cin** i **cout** wejścia/wyjścia obiektów z biblioteką iostream C++. Jednak `CArchive` zapisuje i odczytuje format binarny, nie jest sformatowany tekst.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Serializacja](../mfc/serialization-in-mfc.md)

- [Rola dokumentu w serializacji](#_core_the_document.92.s_role_in_serialization)

- [Rola danych serializacji](#_core_the_data.92.s_role_in_serialization)

- [Pomijanie mechanizmu serializacji](../mfc/bypassing-the-serialization-mechanism.md)

##  <a name="_core_the_document.92.s_role_in_serialization"></a> Rola dokumentu w serializacji

Struktura odpowiada automatycznie po otwarciu menu Plik Zapisz, a następnie Zapisz jako polecenia przez wywołanie metody dokumentu `Serialize` funkcja elementu członkowskiego, jeśli jest zaimplementowana. Id_file_open — polecenie, na przykład wywołuje funkcję obsługi w obiekcie aplikacji. W trakcie tego procesu użytkownik widzi i reaguje na okno dialogowe Otwieranie pliku i struktura uzyskuje nazwę pliku, który użytkownik wybierze. Szablon tworzy `CArchive` obiektu skonfigurowane pod kątem ładowania danych do dokumentu i przekazuje warstwy archiwum do `Serialize`. Struktura ma już otwarty plik. Kod w Twoim dokumencie `Serialize` funkcja elementu członkowskiego odczytuje dane w za pomocą archiwum Rekonstruowanie obiektów danych, zgodnie z potrzebami. Aby uzyskać więcej informacji na temat serializacji, zobacz artykuł [serializacji](../mfc/serialization-in-mfc.md).

##  <a name="_core_the_data.92.s_role_in_serialization"></a> Rola danych serializacji

Ogólnie rzecz biorąc dane typu klasy, powinno być możliwe do serializacji sam. Oznacza to jeśli obiekt do archiwum, obiekt powinien wiedzieć sposób zapisania się do archiwum i jak odczytać sam z archiwum. MFC obsługuje składania klas do serializacji w ten sposób. Jeśli zamierzasz serializowania danych tego typu zaprojektować klasy, aby zdefiniować typ danych, projektowanie dla serializacji.

## <a name="see-also"></a>Zobacz także

[Używanie dokumentów](../mfc/using-documents.md)
