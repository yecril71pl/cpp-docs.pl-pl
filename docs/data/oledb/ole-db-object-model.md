---
title: Model obiektów OLE DB | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 65cb4ef7acad08d3065f8394d61a50441d5e597c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50056571"
---
# <a name="ole-db-object-model"></a>Model obiektów OLE DB

Model obiektów OLE DB składa się z następujących obiektów lub składniki. Pierwsze cztery obiekty lub składniki wymienione (źródła danych, sesje, polecenia i zestawy wierszy) umożliwiają łączenie ze źródłem danych i wyświetlanie go. Rest, począwszy od metod dostępu, odnoszą się do pracy z danymi, gdy jest on wyświetlany.

## <a name="data-sources"></a>Źródła danych

Obiekty źródła danych umożliwiają połączenie ze źródłem danych, np. plik lub DBMS. Obiekt źródła danych tworzy i zarządza połączenia i zawiera informacje o uprawnienia i uwierzytelnienia (takie jak nazwa logowania i hasło). Obiekt źródła danych można utworzyć co najmniej jednej sesji.

## <a name="sessions"></a>Kategoria Sessions

Sesja zarządza konkretnej interakcji ze źródłem danych w celu wykonywania zapytań i pobierania danych. Każda sesja jest pojedynczą transakcję. Transakcja jest jednostką pracy niepodzielne zdefiniowane przez ACID test. Aby uzyskać pełną definicję kwasu, zobacz [transakcji](#vcconoledbcomponents_transactions).

Sesje są ważne zadania, takie jak otwieranie zestawów wierszy i zwraca obiekt źródła danych, z której został utworzony. Sesje może również zwracać metadane oraz informacje o źródle danych (np. informacji o tabeli).

Sesji można utworzyć co najmniej jedno polecenie.

## <a name="commands"></a>Polecenia

Polecenia zostaną wykonane polecenia tekstu, np. instrukcji SQL. Jeśli polecenie tekst Określa zestaw wierszy, takich jak SQL **wybierz** instrukcję, polecenie spowoduje utworzenie zestawu wierszy.

Polecenie to po prostu kontener dla polecenia tekstu, czyli ciąg tekstowy (np. instrukcji SQL) przekazywane z konsumenta do obiektu źródła danych do wykonania w podstawowym magazynie danych dostawcy. Zazwyczaj polecenia tekst jest SQL **wybierz** — instrukcja (w tym przypadku, ponieważ SQL **wybierz** określa zestawu wierszy polecenia automatycznie tworzy zestawu wierszy).

## <a name="rowsets"></a>Zestawy wierszy

Zestawy wierszy Pokazywanie danych w formacie tabelarycznym. Indeks jest przypadkiem szczególnym zestawu wierszy. Możesz utworzyć zestawy wierszy z sesją lub polecenie.

### <a name="schema-rowsets"></a>Zestawy wierszy schematu

Schematy ma metadane (informacje o strukturalnych) dotyczące bazy danych. Zestawy wierszy schematu są zestawy wierszy, które mają informacji o schemacie. Niektórzy dostawcy OLE DB dla systemu DBMS obsługuje obiekty zestaw wierszy schematu. Aby uzyskać więcej informacji na temat zestawów wierszy schematu, zobacz [uzyskiwanie metadanych za pomocą zestawów wierszy schematu](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) i [klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).

### <a name="view-objects"></a>Wyświetl obiekty

Obiekt widoku definiuje podzbiór wierszy i kolumn w zestawie wierszy. Go nie ma danych własne. Obiekty widoku nie można połączyć dane z wielu zestawów wierszy.

## <a name="accessors"></a>Metod dostępu

Tylko OLE DB korzysta z koncepcji metod dostępu. Metoda dostępu opisano, jak dane są przechowywane w odbiorcy. Posiada zestawu powiązania (nazywane w mapie kolumny) między polami wierszy (kolumny) i elementy członkowskie danych możesz deklarować u odbiorcy.

##  <a name="vcconoledbcomponents_transactions"></a> Transakcje

Obiekty transakcji są używane, gdy przekazywanie lub przerywanie transakcji zagnieżdżonych w innych niż najniższego poziomu. Transakcja jest jednostką pracy niepodzielne zdefiniowane przez ACID test. ACID oznacza:

- Niepodzielność, nie można podzielić na mniejsze jednostki pracy

- Więcej niż jedna transakcja współbieżności, może wystąpić w czasie

- Izolacja, jedna transakcja ma ograniczoną wiedzę na temat zmian wprowadzonych przez inną

- Trwałość, transakcji sprawia, że trwałe zmiany

## <a name="enumerators"></a>Modułów wyliczających

Moduły wyliczające wyszukiwanie dostępnych źródeł danych i inne moduły wyliczające. Odbiorców, którzy nie są dostosowane do określonego źródła danych służy moduły wyliczające do wyszukiwania dla źródła danych do użycia.

Główny moduł wyliczający, dostarczane w programie Microsoft Data Access SDK przesyłane za pośrednictwem rejestru, szukanie źródeł danych i inne moduły wyliczające. Inne moduły wyliczające przechodzić rejestru lub wyszukiwania w sposób specyficzny dla dostawcy.

## <a name="errors"></a>błędy

Dowolny interfejs dla dowolnego obiektu OLE DB mogą generować błędy. Błędy mają dodatkowe informacje o błędzie, w tym obiekt opcjonalne błędu niestandardowego. Te informacje są przechowywane w wyniku HRESULT.

## <a name="notifications"></a>Powiadomienia

Powiadomienia są używane przez grupy konsumentów współpracujących Udostępnianie zestawu wierszy (gdzie udostępnianie oznacza przyjęto konsumentów działa w ramach tej samej transakcji). Powiadomienia umożliwiają współpracujących odbiorców udostępniania zestawu wierszy do uzyskania informacji o akcjach na wierszy, wykonywane przez jego elementów równorzędnych.

## <a name="see-also"></a>Zobacz też

[Programowanie OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Omówienie programowania OLE DB](../../data/oledb/ole-db-programming-overview.md)