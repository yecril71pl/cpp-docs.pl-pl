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
ms.openlocfilehash: 011191b99170b8a8338b5ca1a440a32404c4d793
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212826"
---
# <a name="recordset-odbc"></a>Zestaw rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.

Obiekt [CRecordset](../../mfc/reference/crecordset-class.md) reprezentuje zestaw rekordów wybranych ze źródła danych. Rekordy mogą pochodzić z:

- Tabelę.

- Zapytanie.

- Procedura składowana, która uzyskuje dostęp do co najmniej jednej tabeli.

Przykładem zestawu rekordów na podstawie tabeli jest "Wszyscy klienci", który uzyskuje dostęp do tabeli klienta. Przykładem zapytania jest "wszystkie faktury dla Jan Kowalski". Przykładem zestawu rekordów na podstawie procedury składowanej (czasami nazywanego wstępnie zdefiniowanym zapytaniem) jest "wszystkie konta naruszenia", które wywołuje procedurę przechowywaną w bazie danych zaplecza. Zestaw rekordów może sprzęgać dwie lub więcej tabel z tego samego źródła danych, ale nie tabel z różnych źródeł danych.

> [!NOTE]
>  Niektóre sterowniki ODBC obsługują widoki bazy danych. Widok w tym sensie to zapytanie utworzone pierwotnie przy użyciu instrukcji SQL `CREATE VIEW`.

##  <a name="recordset-capabilities"></a><a name="_core_recordset_capabilities"></a>Możliwości zestawu rekordów

Wszystkie obiekty zestawu rekordów współdzielą następujące możliwości:

- Jeśli źródło danych nie jest tylko do odczytu, możesz określić, że zestaw rekordów ma być [aktualizowalny](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), [dołączany](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)lub tylko do odczytu. Jeśli zestaw rekordów jest aktualizowalny, można wybrać metody pesymistyczne lub optymistyczne, pod warunkiem, że sterownik dostarcza odpowiednie wsparcie [do blokowania.](../../data/odbc/recordset-locking-records-odbc.md) Jeśli źródło danych jest tylko do odczytu, zestaw rekordów będzie tylko do odczytu.

- Można wywołać funkcje członkowskie, aby [przewijać](../../data/odbc/recordset-scrolling-odbc.md) wybrane rekordy.

- Można [filtrować](../../data/odbc/recordset-filtering-records-odbc.md) rekordy, aby ograniczyć, które rekordy są wybrane z tych dostępnych.

- Rekordy można [sortować](../../data/odbc/recordset-sorting-records-odbc.md) w kolejności rosnącej lub malejącej na podstawie jednej lub większej liczby kolumn.

- Można [Sparametryzuj](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) zestaw rekordów, aby kwalifikować wybór zestawu rekordów w czasie wykonywania.

##  <a name="snapshots-and-dynasets"></a><a name="_core_snapshots_and_dynasets"></a>Migawki i zestawy dynamiczne

Istnieją dwa główne typy zestawów rekordów: [migawki](../../data/odbc/snapshot.md) i [zestawy dynamiczne](../../data/odbc/dynaset.md). Oba są obsługiwane przez `CRecordset`klas. Każda z nich ma wspólne cechy wszystkich zestawów rekordów, ale każdy z nich również rozszerza typowe funkcje we własnym, wyspecjalizowanym sposobie. Migawki zapewniają statyczny widok danych i są przydatne w raportach i w innych sytuacjach, w których widok danych powinien znajdować się w określonym czasie. Zestawy dynamiczne są przydatne, gdy chcesz, aby aktualizacje dokonane przez innych użytkowników były widoczne w zestawie rekordów bez konieczności ponawiania kwerendy lub odświeżania zestawu rekordów. Migawki i zestawy dynamiczne mogą być aktualizowalne lub tylko do odczytu. Aby odzwierciedlić rekordy dodane lub usunięte przez innych użytkowników, wywołaj [CRecordset:: Requery](../../mfc/reference/crecordset-class.md#requery).

`CRecordset` również zezwala na dwa inne typy zestawów rekordów: dynamiczne zestawy rekordów i zestawy rekordów do przodu. Dynamiczne zestawy rekordów są podobne do zestawów dynamicznych; jednak dynamiczne zestawy rekordów odzwierciedlają wszystkie rekordy dodane lub usunięte bez wywoływania `CRecordset::Requery`. Z tego powodu dynamiczne zestawy rekordów są generalnie kosztowne w odniesieniu do czasu przetwarzania w systemie DBMS i wiele sterowników ODBC ich nie obsługuje. Z kolei zestawy rekordów tylko do przodu zapewniają najbardziej wydajną metodę dostępu do danych dla zestawów rekordów, które nie wymagają aktualizacji lub przewijania do tyłu. Na przykład można użyć zestawu rekordów tylko do przesyłania dalej do migrowania danych z jednego źródła danych do innego, gdy wystarczy przenieść dane w kierunku do przodu. Aby użyć zestawu rekordów tylko do przesyłania dalej, należy wykonać obie następujące czynności:

- Przekaż `CRecordset::forwardOnly` opcji jako parametr *nOpenType* funkcji [Open](../../mfc/reference/crecordset-class.md#open) member.

- Określ `CRecordset::readOnly` w parametrze *dwOptions* `Open`.

    > [!NOTE]
    >  Aby uzyskać informacje o wymaganiach dotyczących sterownika ODBC dla obsługi dynamicznego, zobacz [ODBC](../../data/odbc/odbc-basics.md). Aby uzyskać listę sterowników ODBC uwzględnionych w tej wersji programu Visual C++ i uzyskać informacje o uzyskiwaniu dodatkowych sterowników, zobacz [Lista sterowników ODBC](../../data/odbc/odbc-driver-list.md).

##  <a name="your-recordsets"></a><a name="_core_your_recordsets"></a>Zestawy rekordów

Dla każdej oddzielnej tabeli, widoku lub procedury składowanej, do której chcesz uzyskać dostęp, zazwyczaj zdefiniujesz klasę pochodną `CRecordset`. (Wyjątek jest przyłączaniem do bazy danych, w którym jeden zestaw rekordów reprezentuje kolumny z dwóch lub więcej tabel). W przypadku wyprowadzania klasy zestawu rekordów należy włączyć mechanizm wymiany pól rekordów (RFX) lub mechanizmu wymiany zbiorczych pól rekordów (bulk RFX), który jest podobny do mechanizmu wymiany danych (DDX) okna dialogowego. RFX i bulk RFX upraszczają transfer danych ze źródła danych do zestawu rekordów; RFX dodatkowo transferuje dane z zestawu rekordów do źródła danych. Aby uzyskać więcej informacji, zobacz [Rejestrowanie pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md) i [zestaw rekordów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Obiekt zestawu rekordów umożliwia dostęp do wszystkich wybranych rekordów. Przewinięcie wielu wybranych rekordów przy użyciu `CRecordset` funkcji Członkowskich, takich jak `MoveNext` i `MovePrev`. W tym samym czasie obiekt zestawu rekordów reprezentuje tylko jeden z wybranych rekordów, bieżącego rekordu. Można zbadać pola bieżącego rekordu, deklarując zmienne składowe klasy zestawu rekordów, które odpowiadają kolumnom tabeli lub rekordów, które wynikają z kwerendy bazy danych. Aby uzyskać informacje o elementach członkowskich danych zestawu rekordów, zobacz [zestaw rekordów: architektura (ODBC)](../../data/odbc/recordset-architecture-odbc.md).

W poniższych tematach opisano szczegóły dotyczące korzystania z obiektów zestawu rekordów. Tematy są wymienione w kategorii funkcjonalnej i naturalnej kolejności przeglądania w celu zezwolenia na Odczyt sekwencyjny.

### <a name="topics-about-the-mechanics-of-opening-reading-and-closing-recordsets"></a>Tematy dotyczące Mechanics otwieranie, odczytywanie i zamykanie zestawów rekordów

- [Zestaw rekordów: architektura (ODBC)](../../data/odbc/recordset-architecture-odbc.md)

- [Zestaw rekordów: deklarowanie klasy dla tabeli (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)

- [Zestaw rekordów: tworzenie i zamykanie zestawów rekordów (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

- [Zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)

- [Zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

- [Zestaw rekordów: filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)

- [Zestaw rekordów: sortowanie rekordów (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)

- [Zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

### <a name="topics-about-the-mechanics-of-modifying-recordsets"></a>Tematy dotyczące Mechanics modyfikowania zestawów rekordów

- [Zestaw rekordów: dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)

- [Zestaw rekordów: blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)

- [Zestaw rekordów: ponowne wysyłanie zapytania do zestawu rekordów (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)

### <a name="topics-about-somewhat-more-advanced-techniques"></a>Tematy dotyczące nieco bardziej zaawansowanych technik

- [Zestaw rekordów: wykonywanie sprzężenia (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)

- [Zestaw rekordów: deklarowanie klasy dla wstępnie zdefiniowanego zapytania (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)

- [Zestaw rekordów: dynamiczne powiązanie kolumn danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)

- [Zestaw rekordów: zbiorcze pobieranie rekordów (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

- [Zestaw rekordów: praca z dużymi elementami danych (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)

- [Zestaw rekordów: uzyskiwanie sum i innych wyników agregacji (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)

### <a name="topics-about-how-recordsets-work"></a>Tematy dotyczące sposobu działania zestawów rekordów

- [Zestaw rekordów: jak zestawy rekordów pobierają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)

- [Zestaw rekordów: jak zestawy rekordów aktualizują rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

## <a name="see-also"></a>Zobacz też

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Korzystanie z MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Transakcja (ODBC)](../../data/odbc/transaction-odbc.md)
