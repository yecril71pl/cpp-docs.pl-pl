---
title: 'Kontenery: Pliki złożone'
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
ms.openlocfilehash: 8ae701af3dbf45a1b48ef223f421d17f6abee213
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326629"
---
# <a name="containers-compound-files"></a>Kontenery: Pliki złożone

W tym artykule opisano składniki i implementacja pliki złożone i zalety i wady używania pliki złożone w aplikacji OLE.

Pliki złożone są integralną częścią OLE. Są one używane do ułatwienia transferu danych i przechowywania dokumentów OLE. Pliki złożone są implementacja modelu Active strukturalny magazyn. Spójne interfejsy istnieć tej serializacji pomocy technicznej do magazynu, strumienia lub obiektu pliku. Pliki złożone są obsługiwane w bibliotece klas Microsoft Foundation przez klasy `COleStreamFile` i `COleDocument`.

> [!NOTE]
>  Przy użyciu pliku złożonym nie oznacza, czy informacje pochodzą z dokumentu OLE lub złożone. Pliki złożone są co najmniej jeden sposoby przechowywania dokumentów złożonych, dokumenty OLE i innych danych.

##  <a name="_core_components_of_a_compound_file"></a> Składniki pliku złożonym

Implementacja plików złożonych OLE używa trzech typów obiektów: obiekty strumienia, obiektów magazynu oraz `ILockBytes` obiektów. Te obiekty są podobne do składników systemu standardowy plik w następujący sposób:

- Stream obiektów, takich jak pliki, przechowuj dane dowolnego typu.

- Magazyn obiektów, takich jak katalogi, mogą zawierać inne obiekty magazynu i strumieni.

- `LockBytes` obiekty reprezentują interfejs między obiektami magazynu i sprzętu fizycznego. Określają, jak rzeczywista liczba bajtów zapisywanych niezależnie od urządzenia magazynującego `LockBytes` obiekt uzyskuje dostęp do takich jak dysk twardy lub obszar pamięci globalnej. Aby uzyskać więcej informacji na temat `LockBytes` obiektów i `ILockBytes` interfejsu, zobacz *OLE Podręcznik programisty*.

##  <a name="_core_advantages_and_disadvantages_of_compound_files"></a> Zalety i wady pliki złożone

Pliki złożone zapewniają korzyści, które nie są dostępne za pomocą wcześniejszych metod magazynu plików. Obejmują one:

- Uzyskiwanie dostępu do pliku przyrostowe.

- Plik tryby dostępu.

- Standaryzacja struktury plików.

Potencjalne wady pliki złożone — duży rozmiar problemów z wydajnością związane z magazynem na dyskietki — powinny być uważane gdy podjęcie decyzji o użyciu je w aplikacji.

###  <a name="_core_incremental_access_to_files"></a> Przyrostowe dostęp do plików

Przyrostowe dostęp do plików jest automatyczne zaletą używania plików złożonych. Ponieważ plik złożony mogą być wyświetlane jako "systemu plików w pliku", typów poszczególnych obiektów, takich jak stream lub magazynu, są dostępne bez konieczności wczytać całego pliku. To jest znacznie zmniejszyć czas, aplikacja musi uzyskać dostęp do nowych obiektów do edycji przez użytkownika. Przyrostowe aktualizowanie na podstawie tego samego pojęcia oferuje podobne korzyści. Zamiast zapisywać cały plik tak, aby zapisać zmiany wprowadzone do jednego obiektu, OLE są zapisywane tylko strumienia lub magazynu obiekt edytowane przez użytkownika.

###  <a name="_core_file_access_modes"></a> Tryby dostępu do pliku

Jest możliwe ustalenie, kiedy zmiany obiektów w pliku złożonym zobowiązujemy się do dysku jest kolejną korzyścią wynikającą z korzystania z plików złożone. Tryb, w której pliki są dostępne, transakcyjne lub bezpośrednich, określa, kiedy zmiany zostaną zatwierdzone.

- Tryb transakcyjne używa operacji dwufazowego, aby wprowadzić zmiany do obiektów w pliku złożonym, w tym samym sprowadzając zarówno stare i nowe kopie dokumentu, które są dostępne, dopóki użytkownik wybierze albo zapisać albo cofnąć zmiany.

- W trybie bezpośrednim zawiera zmiany w dokumencie, jak zostały wprowadzone, bez możliwości ich później wycofać.

Aby uzyskać więcej informacji na temat trybów dostępu, zobacz *OLE Podręcznik programisty*.

###  <a name="_core_standardization"></a> Standaryzacja

Standardowej struktury plików złożonych umożliwia różnym aplikacjom OLE, przejrzyj pliki złożone tworzone przez testowaną aplikację OLE nie znajomości aplikacji, która faktycznie utworzyła plik.

###  <a name="_core_size_and_performance_considerations"></a> Rozmiar i zagadnienia dotyczące wydajności

Ze względu na złożoność i możliwość zapisania danych przyrostowe struktury magazynu złożony plik, pliki, używając następującego formatu zwykle będzie większy niż inne pliki przy użyciu bez określonej struktury lub magazynu "prostego pliku". Jeśli aplikacja często załadowanie i zapisanie plików, przy użyciu plików złożonych może spowodować rozmiar pliku zwiększyć się znacznie szybciej niż pliki noncompound. Ponieważ pobieranie dużych plików złożonych, czas dostępu dla plików przechowywanych w i ładowane z stacje dyskietek może mieć wpływ, co spowoduje wolniejszy dostęp do plików.

Inny problem, który wpływa na wydajność jest fragmentację pliku złożone. Rozmiar pliku złożonym wynika różnica między sektory dysku imię i nazwisko, używane przez plik. Pofragmentowany plik może zawierać wiele obszarów wolnego miejsca na dysku, które nie zawierają danych, ale są uwzględniane podczas obliczania rozmiaru. W okresie istnienia pliku złożonym te obszary są tworzone przez wstawiania lub usuwania obiektów magazynu.

##  <a name="_core_using_compound_files_format_for_your_data"></a> Przy użyciu formatu plików złożonych danych

Po pomyślnym tworzenia aplikacji, która pochodzi od klasy dokumentów `COleDocument`, upewnij się, że wywołuje konstruktora dokumentu głównego `EnableCompoundFile`. Gdy Kreator aplikacji tworzy się aplikacje kontenera OLE, to wywołanie jest wstawiany za Ciebie.

W *OLE Podręcznik programisty*, zobacz [IStream](/windows/desktop/api/objidl/nn-objidl-istream), [IStorage](/windows/desktop/api/objidl/nn-objidl-istorage), i [interfejsu ILockBytes](/windows/desktop/api/objidl/nn-objidl-ilockbytes).

## <a name="see-also"></a>Zobacz także

[Kontenery](../mfc/containers.md)<br/>
[Kontenery: Problemy z interfejsem użytkownika](../mfc/containers-user-interface-issues.md)<br/>
[Klasa COleStreamFile](../mfc/reference/colestreamfile-class.md)<br/>
[Klasa COleDocument](../mfc/reference/coledocument-class.md)
