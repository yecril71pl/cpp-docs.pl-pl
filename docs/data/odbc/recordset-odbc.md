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
ms.openlocfilehash: b7a55621f4875b24cc33a0fd49a5b8b4c88b34cb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368635"
---
# <a name="recordset-odbc"></a>Zestaw rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.

Obiekt [CRecordset](../../mfc/reference/crecordset-class.md) reprezentuje zestaw rekordów wybranych ze źródła danych. Rekordy mogą pochodzić z:

- Tabela.

- Kwerenda.

- Procedura składowana, która uzyskuje dostęp do jednej lub więcej tabel.

Przykładem zestaw rekordów na podstawie tabeli jest "wszyscy klienci", który uzyskuje dostęp do tabeli Klienta. Przykładem kwerendy jest "wszystkie faktury dla Joe Smitha". Przykładem zestawie rekordów na podstawie procedury składowanej (czasami nazywanej wstępnie zdefiniowaną kwerendą) jest "wszystkie konta zaległości", która wywołuje procedurę składowaną w bazie danych zaplecza. Zestaw rekordów może dołączyć do dwóch lub więcej tabel z tego samego źródła danych, ale nie tabel z różnych źródeł danych.

> [!NOTE]
> Niektóre sterowniki ODBC obsługują widoki bazy danych. Widok w tym sensie jest kwerendą pierwotnie `CREATE VIEW` utworzoną za pomocą instrukcji SQL.

## <a name="recordset-capabilities"></a><a name="_core_recordset_capabilities"></a>Możliwości nastawy rekordów

Wszystkie obiekty wstawki rekordów mają następujące możliwości:

- Jeśli źródło danych nie jest tylko do odczytu, można określić, że zestaw rekordów może być [aktualizowany,](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md) [dołączany](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)lub tylko do odczytu. Jeśli zestaw rekordów można zaktualizować, można wybrać pesymistyczne lub optymistyczne metody [blokowania,](../../data/odbc/recordset-locking-records-odbc.md) pod warunkiem, że sterownik zapewnia odpowiednią obsługę blokowania. Jeśli źródło danych jest tylko do odczytu, zestaw rekordów będzie tylko do odczytu.

- Można wywołać funkcje członkowskie, aby [przewijać](../../data/odbc/recordset-scrolling-odbc.md) wybrane rekordy.

- Można [filtrować](../../data/odbc/recordset-filtering-records-odbc.md) rekordy, aby ograniczyć, które rekordy są wybierane z dostępnych.

- Rekordy można [sortować](../../data/odbc/recordset-sorting-records-odbc.md) w kolejności rosnącej lub malejącej na podstawie jednej lub więcej kolumn.

- Można [sparametryzować](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) tablicę rekordów, aby zakwalifikować wybór tablicy rekordów w czasie wykonywania.

## <a name="snapshots-and-dynasets"></a><a name="_core_snapshots_and_dynasets"></a>Migawki i dynasety

Istnieją dwa główne typy zestawów rekordów: [migawki](../../data/odbc/snapshot.md) i [zestawy dynasetów.](../../data/odbc/dynaset.md) Oba są obsługiwane `CRecordset`przez klasę . Każdy z nich ma wspólne cechy wszystkich rekordów, ale każdy rozszerza również wspólne funkcje na swój własny specjalistyczny sposób. Migawki zapewniają statyczny widok danych i są przydatne w raportach i innych sytuacjach, w których chcesz widok danych, jak istniały w określonym czasie. Zestawy dynasets są przydatne, gdy chcesz, aby aktualizacje wprowadzone przez innych użytkowników były widoczne w zestawie rekordów bez konieczności ponownego podzespołu lub odświeżenia zestawu rekordów. Migawki i zestawy dynasetów można aktualizować lub tylko do odczytu. Aby odzwierciedlić rekordy dodane lub usunięte przez innych użytkowników, zadzwoń do [CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery).

`CRecordset`pozwala również na dwa inne typy rekordów: dynamiczne zestawy rekordów i zestawy rekordów tylko do przodu. Dynamiczne zestawy rekordów są podobne do zestawów dynamicznych; jednak dynamiczne zestawy rekordów odzwierciedlają wszelkie `CRecordset::Requery`rekordy dodane lub usunięte bez wywoływania . Z tego powodu dynamiczne zestawy rekordów są na ogół drogie w odniesieniu do czasu przetwarzania w systemie dbms, a wiele sterowników ODBC nie obsługuje ich. Z kolei zestawy rekordów tylko do przodu zapewniają najbardziej efektywną metodę dostępu do danych dla zestawów rekordów, które nie wymagają aktualizacji ani przewijania wstecznego. Na przykład można użyć zestaw rekordów tylko do przodu do migracji danych z jednego źródła danych do innego, gdzie wystarczy poruszać się między danymi w kierunku do przodu. Aby użyć do przodu tylko do przodu, należy wykonać obie czynności:

- Przekaż tę `CRecordset::forwardOnly` opcję jako parametr *nOpenType* funkcji [Otwórz](../../mfc/reference/crecordset-class.md#open) element członkowski.

- Określ `CRecordset::readOnly` w parametrze *dwOptions* . `Open`

    > [!NOTE]
    >  Aby uzyskać informacje na temat wymagań sterowników ODBC dla obsługi dynaset, zobacz [ODBC](../../data/odbc/odbc-basics.md). Aby uzyskać listę sterowników ODBC zawartych w tej wersji programu Visual C++ oraz informacje na temat uzyskiwania dodatkowych sterowników, zobacz [Lista sterowników ODBC](../../data/odbc/odbc-driver-list.md).

## <a name="your-recordsets"></a><a name="_core_your_recordsets"></a>Twoje zestawy rekordów

Dla każdej odrębnej tabeli, widoku lub procedury składowanej, do której `CRecordset`chcesz uzyskać dostęp, zazwyczaj definiuje się klasę pochodną . (Wyjątkiem jest sprzężenie bazy danych, w którym jeden rekord reprezentuje kolumny z dwóch lub więcej tabel).) Podczas wyprowadzania klasy zestawów rekordów należy włączyć mechanizm wymiany pól rekordów (RFX) lub mechanizm zbiorczej wymiany pól rekordów (Bulk RFX), który jest podobny do mechanizmu wymiany danych dialogowych (DDX). RFX i Bulk RFX upraszczają przesyłanie danych ze źródła danych do zbioru rekordów; RFX dodatkowo przesyła dane z zestawu rekordów do źródła danych. Aby uzyskać więcej informacji, zobacz [Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md) i [Recordset: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Obiekt zestawu rekordów zapewnia dostęp do wszystkich wybranych rekordów. Przewijaj wiele wybranych `CRecordset` rekordów za `MoveNext` `MovePrev`pomocą funkcji członkowskich, takich jak i . W tym samym czasie obiekt forum rekordów reprezentuje tylko jeden z wybranych rekordów, bieżący rekord. Pola bieżącego rekordu można sprawdzić, deklarując zmienne członkowskie klasy zestawów rekordów, które odpowiadają kolumnom tabeli lub rekordom wynikającym z kwerendy bazy danych. Aby uzyskać informacje o członkach danych zestawów rekordów, zobacz [Zestaw rekordów: Architektura (ODBC)](../../data/odbc/recordset-architecture-odbc.md).

W poniższych tematach opisano szczegóły korzystania z obiektów pliku recordset. Tematy są wymienione w kategoriach funkcjonalnych i naturalnej kolejności przeglądania, aby umożliwić czytanie sekwencyjne.

### <a name="topics-about-the-mechanics-of-opening-reading-and-closing-recordsets"></a>Tematy dotyczące mechaniki otwierania, czytania i zamykania recordsets

- [Recordset: Architektura (ODBC)](../../data/odbc/recordset-architecture-odbc.md)

- [Zestaw rekordów: deklarowanie klasy dla tabeli (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)

- [Zestaw rekordów: tworzenie i zamykanie zestawów rekordów (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

- [Zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)

- [Zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

- [Zestaw rekordów: filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)

- [Zestaw rekordów: sortowanie rekordów (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)

- [Zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

### <a name="topics-about-the-mechanics-of-modifying-recordsets"></a>Tematy dotyczące mechaniki modyfikowania rekordów

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

### <a name="topics-about-how-recordsets-work"></a>Tematy dotyczące działania rekordów

- [Zestaw rekordów: jak zestawy rekordów pobierają rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)

- [Zestaw rekordów: jak zestawy rekordów aktualizują rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

## <a name="see-also"></a>Zobacz też

[Łączność z otwartą bazą danych (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[MFC ODBC zużywają](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Transakcja (ODBC)](../../data/odbc/transaction-odbc.md)
