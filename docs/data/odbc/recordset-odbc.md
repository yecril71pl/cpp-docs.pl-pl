---
title: Zestaw rekordów (ODBC)
ms.date: 05/09/2019
helpviewer_keywords:
- recordsets, snapshots
- recordsets, creating
- dynamic recordsets
- forward-only recordsets
- recordsets, dynasets
- ODBC recordsets, CRecordset objects
- ODBC recordsets
- recordsets, about recordsets
- snapshots, ODBC recordsets
- dynasets
ms.assetid: 333337c5-575e-4d26-b5f6-47166ad7874d
ms.openlocfilehash: b043b08e13611b87bbffbe9dfb3255d5520e3359
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707832"
---
# <a name="recordset-odbc"></a>Zestaw rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.

A [CRecordset](../../mfc/reference/crecordset-class.md) obiekt reprezentuje zestaw rekordów wybranych ze źródła danych. Rekordy mogą pochodzić z:

- Tabela.

- Zapytanie.

- Procedura składowana, która uzyskuje dostęp do co najmniej jedna tabela.

Przykład zestawu rekordów na podstawie tabeli jest "wszyscy klienci", który uzyskuje dostęp do tabeli klientów. Przykład zapytania to "wszystkie faktury dla Jan Kowalski". Przykład zestawu rekordów, oparte na procedury składowanej (nazywane również wstępnie zdefiniowanego zapytania) jest "wszystkie konta bardzo" który wywołuje procedurę składowaną w bazie danych zaplecza. Zestaw rekordów, mogą dołączyć do co najmniej dwóch tabel, z tego samego źródła danych, ale nie tabel pochodzących z różnych źródeł danych.

> [!NOTE]
>  Niektóre sterowniki ODBC obsługi widoków bazy danych. Widok, w tym sensie to zapytania utworzone za pomocą języka SQL `CREATE VIEW` instrukcji.

##  <a name="_core_recordset_capabilities"></a> Funkcje zestawu rekordów

Wszystkie obiekty w zestawie rekordów mają następujące możliwości:

- Jeśli źródło danych nie jest tylko do odczytu, możesz określić, że rekordów być [aktualizowalnych](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), [appendable](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), lub tylko do odczytu. Jeśli zestaw rekordów jest można aktualizować, możesz wybrać optymistycznego lub pesymistycznego [blokowania](../../data/odbc/recordset-locking-records-odbc.md) metod, pod warunkiem sterownik dostarcza odpowiednią obsługę blokowania. Jeśli źródło danych jest tylko do odczytu, zestaw rekordów będzie tylko do odczytu.

- Element członkowski można wywołać funkcji [przewijania](../../data/odbc/recordset-scrolling-odbc.md) wybrane rekordy.

- Możesz [filtru](../../data/odbc/recordset-filtering-records-odbc.md) rekordy, które mają ograniczenia, które rekordy są wybierane spośród dostępnych.

- Możesz [sortowania](../../data/odbc/recordset-sorting-records-odbc.md) rekordy w kolejności rosnącej lub malejącej, oparte na co najmniej jedną kolumnę.

- Możesz [parametryzacja](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) rekordów do kwalifikowania rekordów zaznaczenie w czasie wykonywania.

##  <a name="_core_snapshots_and_dynasets"></a> Migawki i zestawów dynamicznych

Istnieją dwa typy jednostki zestawów rekordów: [migawek](../../data/odbc/snapshot.md) i [zestawów dynamicznych](../../data/odbc/dynaset.md). Oba są obsługiwane przez klasę `CRecordset`. Każdy udostępnia typowe cechy wszystkich zestawów rekordów, ale każdy rozszerzają typowych funkcji w jego własnej wyspecjalizowane sposób. Migawki zapewniają widok statyczny danych i są przydatne w przypadku raportów i innych sytuacjach, w których mają wgląd w dane znajdowały się w określonym czasie. Zestawy dynamiczne są przydatne, jeśli chcesz, aby aktualizacje wprowadzone przez innych użytkowników były widoczne w zestawie rekordów bez konieczności Requery — ani nie odświeżaj zestawu rekordów. Migawki i zestawów dynamicznych, może być można aktualizować lub tylko do odczytu. Do odzwierciedlenia rekordów dodanych lub usunięty przez innych użytkowników, wywołaj [CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery).

`CRecordset` Umożliwia również dwa inne rodzaje zestawów rekordów: dynamiczne zestawy rekordów i zestawów rekordów tylko do przodu. Dynamiczne zestawy rekordów są podobne do zestawów dynamicznych; jednak dynamiczne zestawy rekordów odzwierciedla wszelkie rekordy dodawane lub usuwane bez wywoływania `CRecordset::Requery`. Z tego powodu dynamiczne zestawy rekordów są zwykle kosztowne względem czasu przetwarzania w systemu DBMS, a wiele sterowników ODBC nie obsługiwać takiej osoby. Z kolei zestawy rekordów tylko do przodu, podaj najbardziej efektywny sposób dostępu do danych dla zestawów rekordów, które nie wymagają aktualizacji lub przewijanie do tyłu. Może na przykład użyć rekordów, aby przeprowadzić migrację danych z jednego źródła danych do innego, gdzie należy tylko przenieść dane znajdujące się w kierunku do przodu. Aby korzystać z rekordów, należy wykonać obie z następujących czynności:

- Przekaż opcję `CRecordset::forwardOnly` jako *nOpenType* parametru [Otwórz](../../mfc/reference/crecordset-class.md#open) funkcja elementu członkowskiego.

- Określ `CRecordset::readOnly` w *dwOptions* parametru `Open`.

    > [!NOTE]
    >  Aby uzyskać informacji na temat obsługi dynamiczny, wymagania dotyczące sterownika ODBC, zobacz [ODBC](../../data/odbc/odbc-basics.md). Lista sterowników ODBC zawarte w tej wersji programu Visual C++ i informacji na temat uzyskiwania dodatkowych sterowników, zobacz [lista sterowników ODBC](../../data/odbc/odbc-driver-list.md).

##  <a name="_core_your_recordsets"></a> Zestawach rekordów

Dla każdego distinct tabeli, widoku lub procedury składowanej, który chcesz uzyskać dostęp do zazwyczaj zdefiniować klasę pochodną `CRecordset`. (Wyjątek stanowi połączenie bazy danych, w którym jeden zestaw rekordów reprezentuje kolumn z co najmniej dwóch tabel). Gdy klasa wyprowadzona z zestawu rekordów, możesz włączyć mechanizm wymiany (RFX) pola rekordów lub mechanizm wymiany (zbiorcze RFX) pola rekordów zbiorczego, które są podobne do mechanizm wymiany (DDX) danych w oknie dialogowym. RFX i zbiorcze RFX upraszczają transfer danych ze źródła danych do rekordów; RFX dodatkowo przesyła dane z rekordów w źródle danych. Aby uzyskać więcej informacji, zobacz [wymiany pól rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md) i [zestaw rekordów: Pobieranie rekordów (ODBC) zbiorcze](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Obiekty zestawów rekordów daje dostęp do wszystkich wybranych rekordów. Przewiń do wielu rekordów przy użyciu `CRecordset` funkcjach Członkowskich, takich jak `MoveNext` i `MovePrev`. W tym samym czasie obiektem rekordem reprezentuje tylko jeden z wybranych rekordów bieżącego rekordu. Pola bieżącego rekordu można sprawdzić przez zadeklarowanie rekordów zmienne składowe klasy, które odnoszą się do kolumn w tabeli lub rekordy, które są wynikiem zapytań bazy danych. Aby uzyskać informacji na temat elementów członkowskich danych zestawu rekordów, zobacz [zestaw rekordów: Architektura (ODBC)](../../data/odbc/recordset-architecture-odbc.md).

W poniższych tematach opisano szczegóły przy użyciu obiektów zestawu rekordów. Tematy są wymienione w kategorie funkcjonalne i kolejność naturalnych przeglądania dozwolonej sekwencyjnego odczytu.

### <a name="topics-about-the-mechanics-of-opening-reading-and-closing-recordsets"></a>Tematy dotyczące sposobu otwierania, odczytywania i zamykanie zestawów rekordów

- [Zestaw rekordów: architektura (ODBC)](../../data/odbc/recordset-architecture-odbc.md)

- [Zestaw rekordów: deklarowanie klasy dla tabeli (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)

- [Zestaw rekordów: tworzenie i zamykanie zestawów rekordów (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

- [Zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)

- [Zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

- [Zestaw rekordów: filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)

- [Zestaw rekordów: sortowanie rekordów (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)

- [Zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

### <a name="topics-about-the-mechanics-of-modifying-recordsets"></a>Tematy dotyczące sposobu modyfikowania zestawów rekordów

- [Zestaw rekordów: dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)

- [Zestaw rekordów: blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)

- [Zestaw rekordów: ponowne wysyłanie zapytania do zestawu rekordów (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)

### <a name="topics-about-somewhat-more-advanced-techniques"></a>Tematy dotyczące nieco bardziej zaawansowane techniki

- [Zestaw rekordów: wykonywanie sprzężenia (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)

- [Zestaw rekordów: deklarowanie klasy dla wstępnie zdefiniowanego zapytania (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)

- [Zestaw rekordów: dynamiczne powiązanie kolumn danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)

- [Zestaw rekordów: zbiorcze pobieranie rekordów (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

- [Zestaw rekordów: praca z dużymi elementami danych (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)

- [Zestaw rekordów: uzyskiwanie sum i innych wyników agregacji (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)

### <a name="topics-about-how-recordsets-work"></a>Tematy dotyczące informacji na temat działania zestawów rekordów

- [Zestaw rekordów: jak zestawy rekordów wybierają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)

- [Zestaw rekordów: jak zestawy rekordów aktualizują rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

## <a name="see-also"></a>Zobacz także

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Klient MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Transakcja (ODBC)](../../data/odbc/transaction-odbc.md)