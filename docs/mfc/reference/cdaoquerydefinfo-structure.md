---
title: CDaoQueryDefInfo — Struktura
ms.date: 11/04/2016
f1_keywords:
- CDaoQueryDefInfo
helpviewer_keywords:
- DAO (Data Access Objects), QueryDefs collection
- CDaoQueryDefInfo structure [MFC]
ms.assetid: e20837dc-e78d-4171-a195-1b4075fb5d2a
ms.openlocfilehash: e2f0325237a30989637821464c63a4d8b8000b1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368938"
---
# <a name="cdaoquerydefinfo-structure"></a>CDaoQueryDefInfo — Struktura

Struktura `CDaoQueryDefInfo` zawiera informacje o obiektu querydef zdefiniowanym dla obiektów dostępu do danych (DAO).

## <a name="syntax"></a>Składnia

```
struct CDaoQueryDefInfo
{
    CString m_strName;               // Primary
    short m_nType;   // Primary
    COleDateTime m_dateCreated;      // Secondary
    COleDateTime m_dateLastUpdated;  // Secondary
    BOOL m_bUpdatable;               // Secondary
    BOOL m_bReturnsRecords;          // Secondary
    CString m_strSQL;                // All
    CString m_strConnect;            // All
    short m_nODBCTimeout;            // All
};
```

#### <a name="parameters"></a>Parametry

*m_strName*<br/>
Unikatowo nazywa obiekt querydef. Aby uzyskać więcej informacji, zobacz temat "Właściwość nazwy" w Pomocy DAO. Wywołanie [CDaoQueryDef::GetName,](../../mfc/reference/cdaoquerydef-class.md#getname) aby pobrać tę właściwość bezpośrednio.

*m_nType*<br/>
Wartość wskazująca typ operacyjny querydef obiektu. Może to być jedna z następujących wartości:

- `dbQSelect`Select — kwerenda wybiera rekordy.

- `dbQAction`Akcja — kwerenda przenosi lub zmienia dane, ale nie zwraca rekordów.

- `dbQCrosstab`Krzyżowa — kwerenda zwraca dane w formacie przypominającym arkusz kalkulacyjny.

- `dbQDelete`Usuń — kwerenda usuwa zestaw określonych wierszy.

- `dbQUpdate`Aktualizacja — kwerenda zmienia zestaw rekordów.

- `dbQAppend`Dołącz — kwerenda dodaje nowe rekordy na końcu tabeli lub kwerendy.

- `dbQMakeTable`Make-table — kwerenda tworzy nową tabelę z akcesu.

- `dbQDDL`Data-definition — kwerenda wpływa na strukturę tabel lub ich części.

- `dbQSQLPassThrough`Przekazywanie — instrukcja SQL jest przekazywana bezpośrednio do wewnętrznej bazy danych, bez przetwarzania pośredniego.

- `dbQSetOperation`Union — kwerenda tworzy obiekt zestaw rekordów typu migawki zawierający dane ze wszystkich określonych rekordów w dwóch lub więcej tabelach z usuniętymi rekordami. Aby uwzględnić duplikaty, dodaj słowo kluczowe **ALL** w instrukcji SQL querydef.

- `dbQSPTBulk`Używane `dbQSQLPassThrough` do określania kwerendy, która nie zwraca rekordów.

> [!NOTE]
> Aby utworzyć kwerendę przekazową SQL, nie `dbQSQLPassThrough` należy ustawiać stałej. Jest to ustawiane automatycznie przez aparat bazy danych Microsoft Jet podczas tworzenia obiektu querydef i ustawiania właściwości Connect.

Aby uzyskać więcej informacji, zobacz temat "Typ właściwości" w Pomocy DAO.

*m_dateCreated*<br/>
Data i godzina querydef został utworzony. Aby bezpośrednio pobrać datę querydef został utworzony, wywołać [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated) funkcji elementu członkowskiego `CDaoTableDef` obiektu skojarzonego z tabelą. Zobacz komentarze poniżej, aby uzyskać więcej informacji. Zobacz także temat "DateCreated, LastUpdated Properties" w Pomocy DAO.

*m_dateLastUpdated*<br/>
Data i godzina ostatniej zmiany wprowadzonej do querydef. Aby bezpośrednio pobrać datę ostatniej aktualizacji tabeli, należy wywołać funkcję elementu członkowskiego [GetDateLastUpdated](../../mfc/reference/cdaoquerydef-class.md#getdatelastupdated) querydef. Zobacz komentarze poniżej, aby uzyskać więcej informacji. I zobacz temat "DateCreated, LastUpdated Properties" w Pomocy DAO.

*m_bUpdatable*<br/>
Wskazuje, czy można ww. Jeśli ta właściwość jest TRUE, querydef jest aktualizowane; w przeciwnym razie tak nie jest. Aktualizacja oznacza, że definicja kwerendy obiektu querydef query może zostać zmieniona. Właściwość Updatable obiektu querydef jest ustawiona na WARTOŚĆ TRUE, jeśli można zaktualizować definicję kwerendy, nawet jeśli wynikowy zestaw rekordów nie jest aktualizowany. Aby pobrać tę właściwość bezpośrednio, wywołać querydef's [CanUpdate funkcji członkowskiej.](../../mfc/reference/cdaoquerydef-class.md#canupdate) Aby uzyskać więcej informacji, zobacz temat "Aktualizacja właściwości" w Pomocy DAO.

*m_bReturnsRecords*<br/>
Wskazuje, czy kwerenda przekazywania SQL do zewnętrznej bazy danych zwraca rekordy. Jeśli ta właściwość ma wartość PRAWDA, kwerenda zwraca rekordy. Aby bezpośrednio pobrać tę właściwość, wywołaj [CDaoQueryDef::GetReturnsRecords](../../mfc/reference/cdaoquerydef-class.md#getreturnsrecords). Nie wszystkie zapytania przekazywania SQL do zewnętrznych baz danych zwracają rekordy. Na przykład instrukcja SQL **UPDATE** aktualizuje rekordy bez zwracania rekordów, podczas gdy instrukcja SQL **SELECT** zwraca rekordy. Aby uzyskać więcej informacji, zobacz temat "Właściwość ReturnsRecords" w Pomocy DAO.

*m_strSQL*<br/>
Instrukcja SQL definiująca kwerendę wykonaną przez obiekt querydef. Właściwość SQL zawiera instrukcję SQL, która określa sposób wybierania, grupowania i porządkowania rekordów podczas wykonywania kwerendy. Za pomocą kwerendy można wybrać rekordy do uwzględnienia w obiekcie zestawu rekordów typu dynaset lub snapshot. Można również zdefiniować zapytania zbiorcze, aby zmodyfikować dane bez zwracania rekordów. Można pobrać wartość tej właściwości bezpośrednio wywołując querydef's [GetSQL](../../mfc/reference/cdaoquerydef-class.md#getsql) funkcji elementu członkowskiego.

*m_strConnect*<br/>
Zawiera informacje o źródle bazy danych używanej w kwerendzie przekazowej. Te informacje mają postać ciągu połączenia. Aby uzyskać więcej informacji na temat łączyć ciągów i informacji o pobieraniu wartości tej właściwości bezpośrednio, zobacz [CDaoDatabase::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) funkcji elementu członkowskiego.

*m_nODBCTimeout*<br/>
Liczba sekund, przez którą aparat bazy danych Microsoft Jet czeka, zanim wystąpi błąd limitu czasu, gdy kwerenda jest uruchamiana w bazie danych ODBC. Podczas korzystania z bazy danych ODBC, takich jak Microsoft SQL Server, mogą wystąpić opóźnienia z powodu ruchu sieciowego lub intensywnego korzystania z serwera ODBC. Zamiast czekać przez czas nieokreślony, można określić, jak długo aparat Microsoft Jet czeka, zanim wywoła błąd. Domyślna wartość limitu czasu wynosi 60 sekund. Można pobrać wartość tej właściwości bezpośrednio wywołując [querydef's GetODBCTimeout](../../mfc/reference/cdaoquerydef-class.md#getodbctimeout) funkcji elementu członkowskiego. Aby uzyskać więcej informacji, zobacz temat "ODBCTimeout Property" w Pomocy DAO.

## <a name="remarks"></a>Uwagi

Querydef jest obiektem klasy [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Odwołania do podstawowych, pomocniczych i wszystkie powyżej wskazują, jak informacje są zwracane `CDaoDatabase`przez funkcję elementu członkowskiego [GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) w klasie .

Informacje pobierane przez [CDaoDatabase::GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) funkcji elementu `CDaoQueryDefInfo` członkowskiego jest przechowywany w strukturze. Wywołanie `GetQueryDefInfo` obiektu bazy danych, w którego QueryDefs kolekcji querydef obiektu jest przechowywany. `CDaoQueryDefInfo`definiuje również `Dump` funkcję elementu członkowskiego w kompilacjach debugowania. Można użyć `Dump` do zrzutu `CDaoQueryDefInfo` zawartości obiektu. Klasa `CDaoDatabase` dostarcza również funkcje członkowskie do bezpośredniego dostępu do `CDaoQueryDefInfo` wszystkich właściwości zwróconych w obiekcie, więc prawdopodobnie rzadko trzeba wywołać `GetQueryDefInfo`.

Po dołączeniu nowego obiektu pola lub parametru do kolekcji Fields lub Parameters obiektu querydef zostanie zgłoszony wyjątek, jeśli podstawowa baza danych nie obsługuje typu danych określonego dla nowego obiektu.

Ustawienia daty i godziny pochodzą z komputera, na którym został utworzony lub ostatnio zaktualizowany querydef. W środowisku dla wielu użytkowników użytkownicy powinni uzyskać te ustawienia bezpośrednio z serwera plików za pomocą polecenia **czas netto,** aby uniknąć rozbieżności w ustawieniach właściwości DateCreated i LastUpdated.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Klasa CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)<br/>
[Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)
