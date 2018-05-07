---
title: 'Kontenery: Pliki złożone | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8983fd8cb51a9f305ef4b0fad4d546fc8091f5a5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="containers-compound-files"></a>Kontenery: pliki złożone
W tym artykule opisano składniki i implementacja pliki złożone i zalety i wady używania pliki złożone w aplikacji OLE.  
  
 Pliki złożone są integralną częścią OLE. Są one używane do ułatwienia transferu danych i przechowywanie dokumentów OLE. Pliki złożone są implementację modelu magazynu o strukturze aktywnej. Interfejsy zgodne istnieje tej serializacji pomocy technicznej do magazynu, strumienia lub obiektu pliku. Pliki złożone są obsługiwane w programie Microsoft Foundation Class Library przez klasy `COleStreamFile` i `COleDocument`.  
  
> [!NOTE]
>  Przy użyciu pliku złożonego nie oznacza, czy informacje pochodzą z dokumentu OLE lub złożonych. Pliki złożone są tylko jedną z metod do przechowywania dokumentów złożonych, dokumenty OLE i innych danych.  
  
##  <a name="_core_components_of_a_compound_file"></a> Składniki plik złożony  
 Implementacja OLE pliki złożone używa trzech typów obiektów: obiekty strumienia, obiektów magazynu oraz `ILockBytes` obiektów. Te obiekty są podobne do składników systemu standardowego pliku w następujący sposób:  
  
-   Obiekty strumienia, takich jak pliki, przechowywać dane dowolnego typu.  
  
-   Magazyn obiekty, takie jak katalogi, może zawierać inne obiekty magazynu i strumienia.  
  
-   **LockBytes** reprezentować interfejs między obiektami pamięci masowej i sprzętem fizycznym. Określają one, jak rzeczywista liczba bajtów zapisywanych w niezależnie od urządzenia magazynującego **LockBytes** obiekt uzyskuje dostęp do takich jak dysk twardy lub obszar pamięci globalnej. Aby uzyskać więcej informacji na temat **LockBytes** obiektów i `ILockBytes` interfejsu, zobacz *OLE Podręcznik programisty*.  
  
##  <a name="_core_advantages_and_disadvantages_of_compound_files"></a> Zalety i wady pliki złożone  
 Pliki złożone zapewniają korzyści, które nie są dostępne z wcześniejszych metod magazynu plików. Obejmują one:  
  
-   Uzyskiwanie dostępu do pliku przyrostowe.  
  
-   Plik tryby dostępu.  
  
-   Standaryzacja struktury plików.  
  
 Potencjalne wady pliki złożone — duże problemy rozmiaru i wydajności dotyczących pamięci masowej na dyskietki — powinien być uważane po wybraniu podjęcie decyzji o użyciu je w aplikacji.  
  
###  <a name="_core_incremental_access_to_files"></a> Przyrostowe dostęp do plików  
 Przyrostowe dostęp do plików jest automatyczne zaletą używania pliki złożone. Ponieważ plik złożony można wyświetlić jako "system plików w pliku", są dostępne typów poszczególnych obiektów, takich jak strumienia lub magazynu, bez konieczności załadować całego pliku. Może to znacznie skrócić czas aplikacji wymaga dostępu do nowych obiektów do edycji przez użytkownika. Przyrostowe aktualizowanie na podstawie tego samego pojęcia korzyści podobnych oferty. Zamiast zapisywania całego pliku tak, aby zapisać zmiany wprowadzone do jednego obiektu OLE zapisuje tylko strumienia lub magazynu obiekt edytowane przez użytkownika.  
  
###  <a name="_core_file_access_modes"></a> Tryby dostępu do pliku  
 Możliwość określenia, gdy dysku są zmiany do obiektów w pliku złożonego jest inną zaletą używania pliki złożone. Tryb, w którym pliki są dostępne, transakcyjne lub bezpośrednio, określa, kiedy są zatwierdzone zmiany.  
  
-   Tryb transakcyjne używa operacji dwufazowe wprowadzać zmiany do obiektów w pliku złożonego, co utrzymywanie zarówno stary, jak i nowych kopii dokumentu dostępne, dopóki użytkownik wybierze opcję albo zapisać lub cofnąć zmiany.  
  
-   W trybie bezpośrednim zawiera zmiany w dokumencie, jak zostały wprowadzone, bez możliwości ich później cofnąć.  
  
 Aby uzyskać więcej informacji na temat trybów dostępu, zobacz *OLE Podręcznik programisty*.  
  
###  <a name="_core_standardization"></a> Standaryzacja  
 Struktura standardowych pliki złożone umożliwia różnych aplikacji OLE przeglądać pliki złożone utworzone przez aplikację OLE z nie wie, aplikacji, która faktycznie utworzony plik.  
  
###  <a name="_core_size_and_performance_considerations"></a> Rozmiar i zagadnienia dotyczące wydajności  
 Ze względu na złożoność struktury magazynu plików złożone i możliwość zapisania danych przyrostowo plików za pomocą tego formatu zazwyczaj będzie większy niż inne pliki przy użyciu bez struktury lub magazynu "płaskim plik". Jeśli aplikacja często załadowanie i zapisanie plików, przy użyciu pliki złożone może spowodować znacznie szybciej niż pliki noncompound zwiększyć rozmiar pliku. Ponieważ pliki złożone można uzyskać duży, czas dostępu dla plików przechowywanych na i załadowane z dyskietek można również będzie zmienione, spowodować wolniejszy dostęp do plików.  
  
 Inny problem, który wpływa na wydajność jest złożone pliku fragmentacji. Rozmiar pliku złożonego jest określany przez różnicę między sektorów dysku imię i nazwisko, używane przez plik. Pofragmentowany plik może zawierać wiele obszarów wolnego miejsca, które nie zawierają danych, ale są uwzględniane podczas obliczania rozmiaru. Okres istnienia pliku złożonego tych obszarów są tworzone przez wstawiania lub usuwania obiektów magazynu.  
  
##  <a name="_core_using_compound_files_format_for_your_data"></a> Dla danych przy użyciu formatu pliki złożone  
 Po pomyślnie tworzenie aplikacji zawierającej pochodzi od klasy dokumentu `COleDocument`, upewnij się, że Twoje Konstruktor głównego dokumentu wywołuje `EnableCompoundFile`. Gdy Kreator aplikacji tworzy aplikacje kontenera OLE, to wywołanie jest wprowadzana automatycznie.  
  
 W *OLE Podręcznik programisty*, zobacz [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034), [IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015), i [typ ILockBytes](http://msdn.microsoft.com/library/windows/desktop/aa379238).  
  
## <a name="see-also"></a>Zobacz też  
 [Kontenery](../mfc/containers.md)   
 [Kontenery: Problemy z interfejsem użytkownika](../mfc/containers-user-interface-issues.md)   
 [Klasa COleStreamFile](../mfc/reference/colestreamfile-class.md)   
 [Klasa COleDocument](../mfc/reference/coledocument-class.md)
