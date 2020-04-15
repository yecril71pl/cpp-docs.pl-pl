---
title: Model obiektów OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
ms.openlocfilehash: b37205eb91317c602010a4b568057845b2345ef0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369799"
---
# <a name="ole-db-object-model"></a>Model obiektów OLE DB

Model obiektów OLE DB składa się z następujących obiektów lub komponentów. Pierwsze cztery wymienione obiekty lub składniki (źródła danych, sesje, polecenia i zestawy wierszy) umożliwiają łączenie się ze źródłem danych i wyświetlanie go. Reszta, począwszy od akcesorów, odnoszą się do pracy z danymi, gdy są wyświetlane.

## <a name="data-sources"></a>Źródła danych

Obiekty źródła danych umożliwiają łączenie się ze źródłem danych, takim jak plik lub system DBMS. Obiekt źródła danych tworzy połączenie i zarządza nim oraz zawiera informacje o uprawnieniach i uwierzytelnianiu (takie jak nazwa logowania i hasło). Obiekt źródła danych może utworzyć jedną lub więcej sesji.

## <a name="sessions"></a>Sesje

Sesja zarządza określoną interakcją ze źródłem danych w celu wykonywania zapytań i pobierania danych. Każda sesja jest pojedynczą transakcją. Transakcja jest niepodzielną jednostką roboczą zdefiniowaną przez test ACID. Aby uzyskać definicję ACID, zobacz [Transakcje](#vcconoledbcomponents_transactions).

Sesje wykonują ważne zadania, takie jak otwieranie zestawów wierszy i zwracanie obiektu źródła danych, który go utworzył. Sesje mogą również zwracać metadane lub informacje o samym źródle danych (takie jak informacje o tabeli).

Sesja może utworzyć jedno lub więcej poleceń.

## <a name="commands"></a>Polecenia

Polecenia wykonują polecenie tekstowe, takie jak instrukcja SQL. Jeśli polecenie tekstowe określa zestaw wierszy, taki jak instrukcja SQL **SELECT,** polecenie tworzy zestaw wierszy.

Polecenie jest po prostu kontenerem dla polecenia tekstowego, który jest ciągiem (na przykład instrukcją SQL) przekazywanym z konsumenta do obiektu źródła danych do wykonania przez podstawowy magazyn danych dostawcy. Zazwyczaj polecenie tekstowe jest instrukcją SQL **SELECT** (w takim przypadku, ponieważ SQL **SELECT** określa zestaw wierszy, polecenie automatycznie tworzy zestaw wierszy).

## <a name="rowsets"></a>Zestawów wierszy

Zestawy wierszy pokazują dane w formacie tabelarycznym. Indeks jest szczególnym przypadkiem zestawu wierszy. Zestawy wierszy można tworzyć z sesji lub polecenia.

### <a name="schema-rowsets"></a>Zestawy wierszy schematu

Schematy mają metadane (informacje strukturalne) o bazie danych. Zestawy wierszy schematu są zestawami wierszy, które mają informacje o schemacie. Niektórzy dostawcy ole db dla dbms obsługi obiektów zestawu wierszy schematu. Aby uzyskać więcej informacji na temat zestawów wierszy schematu, zobacz [Uzyskiwanie metadanych za pomocą zestawów wierszy schematu](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) i [klas zestawów wierszy schematu i klas Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).

### <a name="view-objects"></a>Wyświetlanie obiektów

Obiekt widoku definiuje podzbiór wierszy i kolumn z zestawu wierszy. Nie posiada własnych danych. Widok obiektów nie może łączyć danych z wielu zestawów wierszy.

## <a name="accessors"></a>Akcesorów

Tylko OLE DB używa pojęcia akcesorów. Akcesor opisuje, jak dane są przechowywane w konsumenta. Ma zestaw powiązań (nazywany mapą kolumn) między polami zestawu wierszy (kolumnami) i elementami członkowskich danych, które deklarujesz w konsumenta.

## <a name="transactions"></a><a name="vcconoledbcomponents_transactions"></a>Transakcji

Obiekty transakcji są używane podczas zatwierdzania lub przerywania zagnieżdżonych transakcji na poziomie innym niż najniższy. Transakcja jest niepodzielną jednostką roboczą zdefiniowaną przez test ACID. Acid oznacza:

- Niepodzielność, nie można podzielić na mniejsze jednostki robocze

- Współbieżność, więcej niż jedna transakcja może wystąpić w czasie

- Izolacja, jedna transakcja ma ograniczoną wiedzę na temat zmian wprowadzonych przez inną

- Trwałość, transakcja wprowadza trwałe zmiany

## <a name="enumerators"></a>Modułów wyliczających

Wyliczacze wyszukują dostępne źródła danych i inne wyliczenia. Konsumenci, którzy nie są dostosowane do określonego źródła danych użyć inicjatorów do wyszukiwania źródła danych do użycia.

Wyliczenie główne, dostarczane w microsoft data access SDK, przechodzi przez rejestr w poszukiwaniu źródeł danych i innych wyliczaczy. Inne wyliczenia przechodzą przez rejestr lub wyszukiwania w sposób specyficzny dla dostawcy.

## <a name="errors"></a>Errors

Każdy interfejs na dowolnym obiekcie OLE DB może generować błędy. Błędy mają dodatkowe informacje o błędzie, w tym opcjonalny niestandardowy obiekt błędu. Informacje te są przechowywane w hresult.

## <a name="notifications"></a>Powiadomienia

Powiadomienia są używane przez grupy współpracujących konsumentów, którzy mają zestaw wierszy (gdzie udostępnianie oznacza, że zakłada się, że konsumenci pracują w ramach tej samej transakcji). Powiadomienia umożliwiają współpracującym konsumentom udostępniającym zestaw wierszy, aby byli informowani o działaniach w zestawie wierszy wykonywanych przez ich partnerów.

## <a name="see-also"></a>Zobacz też

[Programowanie OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Omówienie programowania OLE DB](../../data/oledb/ole-db-programming-overview.md)
