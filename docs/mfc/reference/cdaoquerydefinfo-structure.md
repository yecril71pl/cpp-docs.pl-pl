---
title: CDaoQueryDefInfo — Struktura
ms.date: 11/04/2016
f1_keywords:
- CDaoQueryDefInfo
helpviewer_keywords:
- DAO (Data Access Objects), QueryDefs collection
- CDaoQueryDefInfo structure [MFC]
ms.assetid: e20837dc-e78d-4171-a195-1b4075fb5d2a
ms.openlocfilehash: d88d919bb87f614d140d710aee9df3fdf4fd10bc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399736"
---
# <a name="cdaoquerydefinfo-structure"></a>CDaoQueryDefInfo — Struktura

`CDaoQueryDefInfo` Struktura zawiera informacje dotyczące obiektu querydef zdefiniowany dla obiektów dostępu do danych (DAO).

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
Unikatowej nazwy obiektu querydef. Aby uzyskać więcej informacji zobacz temat "Nazwa właściwości" w Pomocy programu DAO. Wywołaj [CDaoQueryDef::GetName](../../mfc/reference/cdaoquerydef-class.md#getname) bezpośrednio pobrać tej właściwości.

*m_nType*<br/>
Wartość, która wskazuje operacyjnej typ obiektu querydef. Wartość może być jedną z następujących czynności:

- `dbQSelect` SELECT — zapytanie wybiera rekordy.

- `dbQAction` Akcja — zapytanie przenosi lub zmienia dane, ale nie zwraca rekordów.

- `dbQCrosstab` Krzyżowe — zwraca dane w formacie przypominającego arkusz kalkulacyjny.

- `dbQDelete` Usuń — zapytania usuwa zestaw określonych wierszy.

- `dbQUpdate` Aktualizacja — zapytania zmiany zestawu rekordów.

- `dbQAppend` Dołącz — zapytanie dodaje nowe rekordy na końcu tabelę lub zapytanie.

- `dbQMakeTable` Tworzące tabelę — zapytanie tworzy nową tabelę z zestawu rekordów.

- `dbQDDL` Definicja danych — struktura tabel lub ich części ma wpływ na zapytanie.

- `dbQSQLPassThrough` Przekazywanego — instrukcja SQL jest przekazywana bezpośrednio do bazy danych zaplecza, bez przetwarzania pośrednich.

- `dbQSetOperation` Union — zapytania tworzy obiekt zestawu rekordów typu migawka, zawierające dane z wszystkich określonych rekordów w dwóch lub większej liczby tabel z żadnych zduplikowanych rekordów usunięte. Aby dołączyć duplikaty, Dodaj słowo kluczowe **wszystkich** w instrukcji SQL querydef.

- `dbQSPTBulk` Używane z `dbQSQLPassThrough` do określenia kwerendę, która nie zwraca rekordy.

> [!NOTE]
>  Aby utworzyć zapytania przekazującego SQL, nie należy ustawiać `dbQSQLPassThrough` stałej. To jest ustawiana automatycznie przez aparat bazy danych Microsoft Jet podczas tworzenia obiektu querydef i ustaw właściwość Connect.

Aby uzyskać więcej informacji zobacz temat "Właściwość Type" w Pomocy programu DAO.

*m_dateCreated*<br/>
Data i godzina utworzenia querydef. Aby bezpośrednio pobrać datę utworzenia querydef, należy wywołać [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated) funkcji składowej typu `CDaoTableDef` obiekt skojarzony z tabeli. Aby uzyskać więcej informacji, zobacz uwagi poniżej. Również w temacie "DateCreated LastUpdated właściwości" w Pomocy programu DAO.

*m_dateLastUpdated*<br/>
Data i godzina ostatniej zmiany wprowadzone do obiektu querydef. Aby bezpośrednio pobrać daty ostatniej aktualizacji tabeli, należy wywołać [GetDateLastUpdated](../../mfc/reference/cdaoquerydef-class.md#getdatelastupdated) querydef funkcji elementu członkowskiego. Aby uzyskać więcej informacji, zobacz uwagi poniżej. I zobacz temat "DateCreated LastUpdated właściwości" w Pomocy programu DAO.

*m_bUpdatable*<br/>
Wskazuje, czy można zmodyfikować obiektu querydef. Jeśli ta właściwość ma wartość TRUE, querydef nadaje; w przeciwnym razie nie jest. Aktualizowalne oznacza, że można zmienić obiektu querydef definicji zapytania. Nadaje się do aktualizacji właściwości obiektu querydef ustawiono na wartość TRUE, jeśli definicja zapytania mogą być aktualizowane, nawet jeśli nie nadaje Wynikowy zestaw rekordów. Aby pobrać bezpośrednio, należy wywołać querydef [CanUpdate](../../mfc/reference/cdaoquerydef-class.md#canupdate) funkcja elementu członkowskiego. Aby uzyskać więcej informacji zobacz temat "Można zaktualizować właściwości" w Pomocy programu DAO.

*m_bReturnsRecords*<br/>
Wskazuje, czy zapytania przekazującego SQL do zewnętrznej bazy danych zwraca rekordy. Jeśli ta właściwość ma wartość TRUE, zapytanie zwraca rekordy. Aby bezpośrednio pobrać tę właściwość, należy wywołać [CDaoQueryDef::GetReturnsRecords](../../mfc/reference/cdaoquerydef-class.md#getreturnsrecords). Nie wszystkie zapytania przekazujące SQL z zewnętrznymi bazami danych zwraca rekordów. Na przykład SQL **aktualizacji** Instrukcja aktualizuje rekordy bez zwracania rekordów podczas SQL **wybierz** instrukcja zwraca rekordów. Aby uzyskać więcej informacji zobacz temat "ReturnsRecords Property" w Pomocy programu DAO.

*m_strSQL*<br/>
Instrukcja SQL, który definiuje zapytanie wykonana przez obiekt querydef. Właściwość SQL zawiera instrukcję SQL, która określa, jak rekordy są zaznaczone, pogrupowanych i uporządkowanych podczas wykonywania zapytania. Zapytanie służy do wybierania rekordów, które mają zostać objęte obiekty zestawów rekordów typu migawka lub dynamiczny. Można również definiować zapytania zbiorcze, aby modyfikować dane bez zwracania rekordów. Wartość tej właściwości można pobrać bezpośrednio, wywołując querydef [GetSQL](../../mfc/reference/cdaoquerydef-class.md#getsql) funkcja elementu członkowskiego.

*m_strConnect*<br/>
Zawiera informacje o źródle bazy danych używanej w zapytania przekazującego. Informacje te mają postać ciągu połączenia. Aby uzyskać więcej informacji o łączenie ciągów i uzyskać informacji o pobieraniu wartość tej właściwości bezpośrednio, zobacz [CDaoDatabase::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) funkcja elementu członkowskiego.

*m_nODBCTimeout*<br/>
Liczba sekund oczekiwania przez aparat bazy danych Microsoft Jet przed błąd upływu limitu czasu występuje, gdy zapytanie jest uruchamiany na bazy danych ODBC. Podczas korzystania z bazy danych ODBC, takich jak Microsoft SQL Server, ze względu na ruch lub duże wykorzystanie sieci serwera ODBC mogą wystąpić opóźnienia. Bez czekania na czas nieokreślony, można określić, jak długo aparatu Microsoft Jet czeka przed generuje błąd. Domyślna wartość limitu czasu wynosi 60 sekund. Wartość tej właściwości można pobrać bezpośrednio, wywołując querydef [GetODBCTimeout](../../mfc/reference/cdaoquerydef-class.md#getodbctimeout) funkcja elementu członkowskiego. Aby uzyskać więcej informacji zobacz temat "ODBCTimeout Property" w Pomocy programu DAO.

## <a name="remarks"></a>Uwagi

Querydef jest obiektem klasy [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Odwołania do podstawowego, pomocniczego i wszystkie powyższe wskazują, jak informacji jest zwróconych przez [GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) funkcja elementu członkowskiego w klasie `CDaoDatabase`.

Informacje o pobrane przez [CDaoDatabase::GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) funkcja członkowska jest przechowywany w `CDaoQueryDefInfo` struktury. Wywołaj `GetQueryDefInfo` dla obiektu bazy danych, w których querydefs — kolekcja jest przechowywany obiekt querydef. `CDaoQueryDefInfo` definiuje również `Dump` kompilacje funkcja elementu członkowskiego podczas debugowania. Możesz użyć `Dump` do porzucenia zawartość `CDaoQueryDefInfo` obiektu. Klasa `CDaoDatabase` również dostarcza funkcji elementów członkowskich, aby uzyskać bezpośredni dostęp do wszystkich właściwości zwracane w `CDaoQueryDefInfo` obiektu, dzięki czemu będzie prawdopodobnie rzadko należy wywołać `GetQueryDefInfo`.

Podczas dołączania nowe pola lub parametr obiektu w kolekcji parametrów lub pól obiektu querydef, wyjątek jest generowany, jeśli w źródłowej bazie danych nie obsługuje typu danych określonego dla nowego obiektu.

Ustawienia daty i godziny są uzyskiwane z komputera, na którym został utworzony lub ostatnia aktualizacja: querydef. W środowisku wielodostępnym użytkowników należy uzyskać te ustawienia bezpośrednio z serwera plików przy użyciu **net czasu** polecenie, aby uniknąć niezgodności w ustawieniach właściwości DateCreated i LastUpdated.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="see-also"></a>Zobacz także

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Klasa CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)<br/>
[Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)
