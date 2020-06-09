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
ms.openlocfilehash: 344c444602555e2b5c145e58d237586199b9e1ed
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624821"
---
# <a name="containers-compound-files"></a>Kontenery: pliki złożone

W tym artykule wyjaśniono składniki i implementację plików złożonych oraz zalety i wady korzystania z plików złożonych w aplikacjach OLE.

Pliki złożone są integralną częścią OLE. Są one używane do ułatwienia transferu danych i magazynu dokumentów OLE. Pliki złożone są implementacją modelu aktywnego magazynu strukturalnego. Istnieją spójne interfejsy, które obsługują serializację do magazynu, strumienia lub obiektu pliku. Pliki złożone są obsługiwane w biblioteka MFC przez klasy `COleStreamFile` i `COleDocument` .

> [!NOTE]
> Użycie pliku złożonego nie oznacza, że informacje pochodzą z dokumentu OLE lub dokumentu złożonego. Pliki złożone są tylko jednym ze sposobów przechowywania dokumentów złożonych, dokumentów OLE i innych danych.

## <a name="components-of-a-compound-file"></a><a name="_core_components_of_a_compound_file"></a>Składniki pliku złożonego

Implementacja OLE plików złożonych używa trzech typów obiektów: Stream Objects, obiektów magazynu i `ILockBytes` obiektów. Te obiekty są podobne do składników standardowego systemu plików w następujący sposób:

- Obiekty strumieniowe, takie jak pliki, przechowują dane dowolnego typu.

- Obiekty magazynu, takie jak katalogi, mogą zawierać inne obiekty magazynu i strumienia.

- `LockBytes`obiekty reprezentują interfejs między obiektami magazynu a sprzętem fizycznym. Określają, jak rzeczywiste bajty są zapisywane do dowolnego urządzenia magazynującego `LockBytes` , do którego uzyskuje dostęp, takich jak dysk twardy lub obszar pamięci globalnej. Aby uzyskać więcej informacji o `LockBytes` obiektach i `ILockBytes` interfejsie, zobacz *informacje dotyczące programisty OLE*.

## <a name="advantages-and-disadvantages-of-compound-files"></a><a name="_core_advantages_and_disadvantages_of_compound_files"></a>Zalety i wady plików złożonych

Pliki złożone zapewniają korzyści niedostępne przy użyciu wcześniejszych metod magazynu plików. Obejmują one:

- Przyrostowy dostęp do pliku.

- Tryby dostępu do pliku.

- Normalizacja struktury plików.

Potencjalne wady plików złożonych — duże problemy dotyczące rozmiaru i wydajności związane z magazynem na dyskietkach — należy wziąć pod uwagę przy podejmowaniu decyzji o tym, czy mają być używane w aplikacji.

### <a name="incremental-access-to-files"></a><a name="_core_incremental_access_to_files"></a>Przyrostowy dostęp do plików

Przyrostowy dostęp do plików jest automatyczną zaletą korzystania z plików złożonych. Ponieważ plik złożony może być wyświetlany jako "system plików w pliku", można uzyskać dostęp do poszczególnych typów obiektów, takich jak Stream lub Storage, bez konieczności ładowania całego pliku. Może to znacząco skrócić czas, przez jaki aplikacja musi uzyskać dostęp do nowych obiektów do edycji przez użytkownika. Aktualizacja przyrostowa oparta na tym samym koncepcji oferuje podobne korzyści. Zamiast zapisywać cały plik tylko w celu zapisania zmian wprowadzonych w jednym obiekcie, OLE zapisuje tylko obiekt strumienia lub magazynu edytowany przez użytkownika.

### <a name="file-access-modes"></a><a name="_core_file_access_modes"></a>Tryby dostępu do plików

Możliwość określenia, kiedy zmiany obiektów w pliku złożonym są przekazane na dysk, jest kolejną zaletą korzystania z plików złożonych. Tryb, w którym są uzyskiwane dostęp do plików, transakcyjny lub bezpośredni, określa, kiedy zmiany są zatwierdzane.

- Tryb transakcyjny używa operacji zatwierdzania dwufazowego, aby wprowadzać zmiany w obiektach w pliku złożonym, co pozwala zachować zarówno starą, jak i nową kopię dokumentu do momentu, gdy użytkownik zdecyduje się na zapisanie lub cofnięcie zmian.

- Tryb bezpośredni obejmuje zmiany w dokumencie w miarę ich wprowadzania, bez możliwości późniejszego ich cofnięcia.

Aby uzyskać więcej informacji o trybach dostępu, zobacz *odwołanie OLE programista*.

### <a name="standardization"></a><a name="_core_standardization"></a>Standaryzacja

Znormalizowana struktura plików złożonych umożliwia różnym aplikacjom OLE przeglądanie plików złożonych utworzonych przez aplikację OLE bez znajomości aplikacji, która faktycznie utworzyła plik.

### <a name="size-and-performance-considerations"></a><a name="_core_size_and_performance_considerations"></a>Zagadnienia dotyczące rozmiaru i wydajności

Ze względu na złożoność struktury magazynu plików złożonych i możliwość przyrostowego zapisywania danych pliki korzystające z tego formatu mogą być większe niż inne pliki przy użyciu magazynu bez struktury lub "pliku prostego". Jeśli aplikacja często ładuje i zapisuje pliki, użycie plików złożonych może spowodować, że rozmiar pliku będzie znacznie szybszy niż pliki niezłożone. Ze względu na to, że pliki złożone mogą uzyskać duże rozmiary, czas dostępu dla plików przechowywanych na dysku i załadowany z dyskietek może być również dotknięty, co powoduje wolniejszy dostęp do plików.

Innym problemem wpływającym na wydajność jest fragmentacja pliku złożonego. Rozmiar pliku złożonego zależy od różnicy między pierwszym i ostatnim sektorem dysku używanym przez ten plik. Pofragmentowany plik może zawierać wiele obszarów wolnego miejsca, które nie zawierają danych, ale są zliczane podczas obliczania rozmiaru. W trakcie okresu istnienia pliku złożonego te obszary są tworzone przez wstawianie lub usuwanie obiektów magazynu.

## <a name="using-compound-files-format-for-your-data"></a><a name="_core_using_compound_files_format_for_your_data"></a>Używanie formatu plików złożonych dla danych

Po pomyślnym utworzeniu aplikacji, która ma klasę dokumentu pochodną od `COleDocument` , należy się upewnić, że Konstruktor dokumentu głównego wywołuje `EnableCompoundFile` . Gdy Kreator aplikacji tworzy aplikacje kontenera OLE, to wywołanie jest wstawiane.

W *odniesieniu do obiektu OLE programista*zobacz [IStream](/windows/win32/api/objidl/nn-objidl-istream), [Metoda IStorage](/windows/win32/api/objidl/nn-objidl-istorage)i [interfejsu ILockBytes](/windows/win32/api/objidl/nn-objidl-ilockbytes).

## <a name="see-also"></a>Zobacz też

[Containers](containers.md)<br/>
[Kontenery: kwestie dotyczące interfejsu użytkownika](containers-user-interface-issues.md)<br/>
[Klasa COleStreamFile](reference/colestreamfile-class.md)<br/>
[Klasa COleDocument](reference/coledocument-class.md)
