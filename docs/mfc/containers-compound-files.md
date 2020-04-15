---
title: 'Kontenery: pliki złożone'
ms.date: 11/04/2016
helpviewer_keywords:
- compound files [MFC]
- compound documents
- containers [MFC], compound files
- OLE documents [MFC], compound files
- performance [MFC], compound files
- files [MFC], compound
- standardized file structure compound files
- documents [MFC], compound
- documents [MFC], OLE
- OLE containers [MFC], compound files
- access modes for files [MFC]
ms.assetid: 8b83cb3e-76c8-4bbe-ba16-737092b36f49
ms.openlocfilehash: 98166a355fd267ecbec0a7f0cc1d18fd0b2e7cd0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353586"
---
# <a name="containers-compound-files"></a>Kontenery: pliki złożone

W tym artykule opisano składniki i implementacji plików złożonych i zalety i wady korzystania z plików złożonych w aplikacjach OLE.

Pliki złożone są integralną częścią OLE. Są one używane w celu ułatwienia transferu danych i przechowywania dokumentów OLE. Pliki złożone są implementacją modelu aktywnego przechowywania strukturalnego. Istnieją spójne interfejsy, które obsługują serializacji do magazynu, strumienia lub obiektu pliku. Pliki złożone są obsługiwane w bibliotece klas `COleStreamFile` `COleDocument`Programu Microsoft Foundation przez klasy i .

> [!NOTE]
> Użycie pliku złożonego nie oznacza, że informacje pochodzą z dokumentu OLE lub dokumentu złożonego. Pliki złożone to tylko jeden ze sposobów przechowywania złożonych dokumentów, dokumentów OLE i innych danych.

## <a name="components-of-a-compound-file"></a><a name="_core_components_of_a_compound_file"></a>Składniki pliku złożonego

Implementacja OLE plików złożonych używa trzech typów obiektów: `ILockBytes` strumieniowe obiekty, obiekty magazynu i obiekty. Obiekty te są podobne do składników standardowego systemu plików w następujący sposób:

- Przesyłaj strumieniowo obiekty, takie jak pliki, przechowuje dane dowolnego typu.

- Obiekty magazynu, takie jak katalogi, mogą zawierać inne obiekty magazynu i strumienia.

- `LockBytes`obiekty reprezentują interfejs między obiektami magazynu a sprzętem fizycznym. Określają one, jak rzeczywiste bajty są zapisywane na dowolnym urządzeniu magazynującym, do które `LockBytes` obiekt uzyskuje dostęp, na przykład na dysku twardym lub obszarze pamięci globalnej. Aby uzyskać `LockBytes` więcej informacji `ILockBytes` o obiektach i interfejsie, zobacz *odwołanie programisty OLE*.

## <a name="advantages-and-disadvantages-of-compound-files"></a><a name="_core_advantages_and_disadvantages_of_compound_files"></a>Zalety i wady plików złożonych

Pliki złożone zapewniają korzyści nie są dostępne we wcześniejszych metodach przechowywania plików. Obejmują one następujące raporty:

- Przyrostowy dostęp do plików.

- Tryby dostępu do plików.

- Standaryzacja struktury plików.

Przy podejmowaniu decyzji, czy używać ich w aplikacji, należy wziąć pod uwagę potencjalne wady plików złożonych — duże rozmiary i problemy z wydajnością związane z przechowywaniem dyskietek.

### <a name="incremental-access-to-files"></a><a name="_core_incremental_access_to_files"></a>Przyrostowy dostęp do plików

Przyrostowy dostęp do plików jest automatyczną korzyścią z używania plików złożonych. Ponieważ plik złożony może być postrzegany jako "system plików w pliku", poszczególne typy obiektów, takie jak strumień lub magazyn, są dostępne bez konieczności ładowania całego pliku. Może to znacznie zmniejszyć czas aplikacji musi uzyskać dostęp do nowych obiektów do edycji przez użytkownika. Aktualizacja przyrostowa, oparta na tej samej koncepcji, oferuje podobne korzyści. Zamiast zapisywać cały plik tylko po to, aby zapisać zmiany wprowadzone w jednym obiekcie, OLE zapisuje tylko strumień lub obiekt magazynu edytowany przez użytkownika.

### <a name="file-access-modes"></a><a name="_core_file_access_modes"></a>Tryby dostępu do plików

Możliwość określenia, kiedy zmiany obiektów w pliku złożonym są zobowiązane do dysku jest kolejną zaletą przy użyciu plików złożonych. Tryb, w którym pliki są dostępne, transacted lub bezpośrednie, określa, kiedy zmiany są zatwierdzane.

- Tryb transacted używa operacji zatwierdzania dwufazowego do wprowadzania zmian w obiektach w pliku złożonym, dzięki tym samym zachowując dostęp zarówno starych, jak i nowych kopii dokumentu, dopóki użytkownik nie zdecyduje się zapisać lub cofnąć zmiany.

- Tryb bezpośredni zawiera zmiany w dokumencie w miarę ich wprowadzania, bez możliwości ich późniejszego cofnięcia.

Aby uzyskać więcej informacji na temat trybów dostępu, zobacz *odwołanie programisty OLE*.

### <a name="standardization"></a><a name="_core_standardization"></a>Standaryzacji

Znormalizowana struktura plików złożonych pozwala różnym aplikacjom OLE przeglądać złożone pliki utworzone przez aplikację OLE bez znajomości aplikacji, która faktycznie utworzyła plik.

### <a name="size-and-performance-considerations"></a><a name="_core_size_and_performance_considerations"></a>Zagadnienia dotyczące rozmiaru i wydajności

Ze względu na złożoność struktury magazynu plików złożonych i możliwość zapisywania danych przyrostowo, pliki przy użyciu tego formatu wydają się być większe niż inne pliki przy użyciu magazynu bez struktury lub "płaskiego pliku". Jeśli aplikacja często ładuje i zapisuje pliki, użycie plików złożonych może spowodować, że rozmiar pliku wzrośnie znacznie szybciej niż pliki niezwiązane ze skomponowaniem. Ponieważ pliki złożone mogą uzyskać duże, może to mieć wpływ na czas dostępu do plików przechowywanych na dyskietkach i załadowanych z dyskietek, co powoduje wolniejszy dostęp do plików.

Innym problemem, który wpływa na wydajność jest fragmentacja pliku złożonego. Rozmiar pliku złożonego zależy od różnicy między pierwszym i ostatnim sektorem dysku używanym przez plik. Pofragmentowany plik może zawierać wiele obszarów wolnego miejsca, które nie zawierają danych, ale są liczone podczas obliczania rozmiaru. W okresie istnienia pliku złożonego obszary te są tworzone przez wstawianie lub usuwanie obiektów magazynu.

## <a name="using-compound-files-format-for-your-data"></a><a name="_core_using_compound_files_format_for_your_data"></a>Korzystanie z formatu plików złożonych dla danych

Po pomyślnym utworzeniu aplikacji, która ma `COleDocument`klasę dokumentu pochodną , `EnableCompoundFile`upewnij się, że główny konstruktor dokumentu wywołuje . Gdy kreator aplikacji tworzy aplikacje kontenera OLE, to wywołanie jest wstawiany dla Ciebie.

W programie *Ole Programmer's Reference*, zobacz [IStream](/windows/win32/api/objidl/nn-objidl-istream), [IStorage](/windows/win32/api/objidl/nn-objidl-istorage)i [ILockBytes](/windows/win32/api/objidl/nn-objidl-ilockbytes).

## <a name="see-also"></a>Zobacz też

[Containers](../mfc/containers.md)<br/>
[Kontenery: kwestie dotyczące interfejsu użytkownika](../mfc/containers-user-interface-issues.md)<br/>
[Klasa COleStreamFile](../mfc/reference/colestreamfile-class.md)<br/>
[Klasa COleDocument](../mfc/reference/coledocument-class.md)
