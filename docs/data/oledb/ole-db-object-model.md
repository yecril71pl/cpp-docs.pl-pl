---
title: Model obiektów OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
ms.openlocfilehash: 192195d02b034546e50b1cb860b1f11c47dc2b65
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210122"
---
# <a name="ole-db-object-model"></a>Model obiektów OLE DB

OLE DB model obiektów składa się z następujących obiektów lub składników. Pierwsze cztery obiekty lub składniki wymienione na liście (źródła danych, sesje, polecenia i zestawy wierszy) umożliwiają nawiązywanie połączenia ze źródłem danych i ich wyświetlanie. Pozostała część, rozpoczynająca się od metod dostępu, odnosi się do pracy z danymi wyświetlanymi.

## <a name="data-sources"></a>Źródła danych

Obiekty źródła danych umożliwiają łączenie się ze źródłem danych, takim jak plik lub system DBMS. Obiekt źródła danych tworzy połączenie i zarządza nim oraz zawiera uprawnienia i informacje dotyczące uwierzytelniania (takie jak nazwa logowania i hasło). Obiekt źródła danych może utworzyć co najmniej jedną sesję.

## <a name="sessions"></a>Sesje

Sesja zarządza określoną interakcją ze źródłem danych w celu wykonywania zapytań i pobierania danych. Każda sesja jest pojedynczą transakcją. Transakcja to niepodzielna jednostka robocza zdefiniowana przez test kwasu. Aby zapoznać się z definicją kwasu, zobacz [Transactions](#vcconoledbcomponents_transactions).

Sesje są ważnymi zadaniami, takimi jak otwieranie zestawów wierszy i zwracanie obiektu źródła danych, który go utworzył. Sesje mogą również zwracać metadane lub informacje o samym źródle danych (takie jak informacje tabeli).

Sesja może utworzyć jedno lub więcej poleceń.

## <a name="commands"></a>Polecenia

Polecenia wykonują polecenie tekstowe, takie jak instrukcja SQL. Jeśli polecenie tekstowe określa zestaw wierszy, taki jak instrukcja SQL **SELECT** , polecenie tworzy zestaw wierszy.

Polecenie jest po prostu kontenerem polecenia tekstowego, które jest ciągiem (na przykład instrukcją SQL) przekazaną przez odbiorcę do obiektu źródła danych w celu wykonania przez podstawowy magazyn danych dostawcy. Zazwyczaj polecenie Text jest instrukcją **SELECT** języka SQL (w tym przypadku, ponieważ SQL **SELECT** określa zestaw wierszy, polecenie automatycznie tworzy zestaw wierszy).

## <a name="rowsets"></a>Zestawy wierszy

Zestawy wierszy pokazują dane w formacie tabelarycznym. Indeks jest specjalnym przypadkiem zestawu wierszy. Zestawy wierszy można tworzyć z sesji lub polecenia.

### <a name="schema-rowsets"></a>Zestawy wierszy schematu

Schematy mają metadane (informacje strukturalne) o bazie danych. Zestawy wierszy schematu są zestawami wierszy, które mają informacje o schemacie. Niektórzy dostawcy OLE DB dla systemu DBMS obsługują obiekty zestawu wierszy schematu. Aby uzyskać więcej informacji na temat zestawów wierszy schematu, zobacz [Uzyskiwanie metadanych za pomocą zestawów wierszy](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) schematu i klas [zestawów wierszy schematu oraz klas typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).

### <a name="view-objects"></a>Wyświetl obiekty

Obiekt widoku definiuje podzestaw wierszy i kolumn z zestawu wierszy. Nie ma własnych danych. Obiekty widoku nie mogą łączyć danych z wielu zestawów wierszy.

## <a name="accessors"></a>Metod dostępu

Tylko OLE DB używa koncepcji metod dostępu. Metoda dostępu opisuje, jak dane są przechowywane w odbiorcy. Zawiera zestaw powiązań (nazywany mapowaniem kolumn) między polami zestawu wierszy (kolumnami) i elementami członkowskimi danych, które zostały zadeklarowane w odbiorcy.

##  <a name="transactions"></a><a name="vcconoledbcomponents_transactions"></a>Akcja

Obiekty transakcji są używane podczas zatwierdzania lub przerywania transakcji zagnieżdżonych na poziomie innym niż najniższy. Transakcja to niepodzielna jednostka robocza zdefiniowana przez test kwasu. Oznacza KWASem:

- Niepodzielność, nie można podzielić na mniejsze jednostki robocze

- Współbieżność, jednocześnie może wystąpić więcej niż jedna transakcja

- Izolacja, jedna transakcja ma ograniczoną wiedzę o zmianach wprowadzonych przez inną

- Trwałość, transakcja powoduje trwałe zmiany

## <a name="enumerators"></a>Modułów wyliczających

Moduł wyliczający wyszukuje dostępne źródła danych i inne moduły wyliczające. Konsumenci niedostosowani do określonego źródła danych używają modułów wyliczających do wyszukiwania źródła danych do użycia.

Główny moduł wyliczający dostarczany w zestawie SDK dostępu do danych firmy Microsoft przechodzi rejestr szukający źródeł danych i innych modułów wyliczających. Inne moduły wyliczające przechodzą rejestr lub przeszukiwać w sposób specyficzny dla dostawcy.

## <a name="errors"></a>Błędy

Każdy interfejs dowolnego OLE DB obiektu może generować błędy. Błędy zawierają dodatkowe informacje o błędzie, w tym opcjonalny obiekt błędu niestandardowego. Te informacje są przechowywane w wyniku HRESULT.

## <a name="notifications"></a>Powiadomienia

Powiadomienia są używane przez grupy współpracujących klientów, którzy współpracują z zestawem wierszy (gdzie udostępnianie oznacza, że odbiorcy będą pracować w ramach tej samej transakcji). Powiadomienia umożliwiają współpracownikom współpracującym udostępnianie zestawu wierszy w celu uzyskania informacji o działaniach w zestawie wierszy wykonywanym przez ich elementy równorzędne.

## <a name="see-also"></a>Zobacz też

[Programowanie OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Omówienie programowania OLE DB](../../data/oledb/ole-db-programming-overview.md)
