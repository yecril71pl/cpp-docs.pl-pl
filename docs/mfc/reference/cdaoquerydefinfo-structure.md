---
title: "Cdaoquerydefinfo — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CDaoQueryDefInfo
dev_langs: C++
helpviewer_keywords:
- DAO (Data Access Objects), QueryDefs collection
- CDaoQueryDefInfo structure [MFC]
ms.assetid: e20837dc-e78d-4171-a195-1b4075fb5d2a
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e476fd8e95b48b59bbb3bae41d9ad84829ca8fa9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
 `m_strName`  
 Unikatowej nazwy obiektu querydef. Aby uzyskać więcej informacji zobacz temat "Właściwości Name" w pomocy DAO. Wywołanie [CDaoQueryDef::GetName](../../mfc/reference/cdaoquerydef-class.md#getname) bezpośrednio pobrać tej właściwości.  
  
 `m_nType`  
 Wartość, która wskazuje operacyjne typu obiektu querydef. Wartość może być jedną z następujących czynności:  
  
- **dbQSelect** wybierz — kwerenda wybiera rekordy.  
  
- **dbQAction** akcji — zapytanie przenosi lub zmiany danych, ale nie zwraca rekordów.  
  
- **dbQCrosstab** krzyżowej — zwraca dane w formacie arkusza kalkulacyjnego podobne.  
  
- **dbQDelete** usunąć — zapytanie usuwa zestaw określonych wierszy.  
  
- **dbQUpdate** aktualizacji — zapytanie zmienia zestawu rekordów.  
  
- **dbQAppend** Dołącz — zapytanie dodaje nowe rekordy na końcu tabelę lub zapytanie.  
  
- **dbQMakeTable** tworzącej — zapytanie tworzy nową tabelę z zestawu rekordów.  
  
- **dbQDDL** definicji danych — struktury tabel lub ich części dotyczy zapytanie.  
  
- **dbQSQLPassThrough** przekazywanego — instrukcja SQL jest przekazywane bezpośrednio do wewnętrznej bazie danych, bez jej przetwarzania pośrednich.  
  
- **dbQSetOperation** Unii — zapytanie tworzy obiekt zestaw rekordów typu migawka, zawierający dane ze wszystkich określonych rekordów w dwóch lub większej liczby tabel z wszystkie zduplikowane rekordy usunięte. Aby uwzględnić duplikaty, Dodaj słowo kluczowe **wszystkich** w instrukcji SQL querydef.  
  
- **dbQSPTBulk** używane z **dbQSQLPassThrough** do określenia kwerendę, która nie zwraca rekordów.  
  
> [!NOTE]
>  Aby utworzyć przekazujący zapytanie SQL, nie należy ustawiać **dbQSQLPassThrough** stałej. To jest ustawiany automatycznie przez aparat bazy danych programu Microsoft Jet podczas tworzenia obiektu querydef i ustaw właściwość Connect.  
  
 Aby uzyskać więcej informacji zobacz temat "Właściwość Type" w pomocy DAO.  
  
 `m_dateCreated`  
 Data i godzina utworzenia obiektu querydef. Aby bezpośrednio pobrać datę utworzenia querydef, należy wywołać [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated) funkcji członkowskiej klasy `CDaoTableDef` obiekt skojarzony z tabelą. Aby uzyskać więcej informacji, zobacz uwagi poniżej. Również w temacie "DateCreated właściwości LastUpdated" w pomocy DAO.  
  
 `m_dateLastUpdated`  
 Data i godzina ostatniej zmiany wprowadzone do querydef. Aby bezpośrednio pobrać datę ostatniej aktualizacji tabeli, należy wywołać [GetDateLastUpdated](../../mfc/reference/cdaoquerydef-class.md#getdatelastupdated) funkcji członkowskiej klasy querydef. Aby uzyskać więcej informacji, zobacz uwagi poniżej. I zawiera temat "DateCreated właściwości LastUpdated" w pomocy DAO.  
  
 `m_bUpdatable`  
 Wskazuje, czy można zmodyfikować obiektu querydef. Jeśli ta właściwość jest **TRUE**querydef jest aktualizowalny; w przeciwnym razie, nie jest. Aktualizowalne oznacza, że można zmienić obiektu querydef definicji zapytania. Nadaje się do aktualizacji właściwości obiektu querydef ustawiono **TRUE** Jeśli definicja zapytania mogą być aktualizowane, nawet jeśli nie nadaje Wynikowy zestaw rekordów. Aby pobrać bezpośrednio, należy wywołać querydef [CanUpdate](../../mfc/reference/cdaoquerydef-class.md#canupdate) funkcję elementu członkowskiego. Aby uzyskać więcej informacji zobacz temat "Nadaje się do aktualizacji właściwości" w pomocy DAO.  
  
 *m_bReturnsRecords*  
 Wskazuje, czy przekazujący zapytanie SQL do zewnętrznej bazy danych zwraca rekordów. Jeśli ta właściwość jest **TRUE**, gdy kwerenda zwraca rekordów. Aby bezpośrednio pobrać tę właściwość, należy wywołać [CDaoQueryDef::GetReturnsRecords](../../mfc/reference/cdaoquerydef-class.md#getreturnsrecords). Nie wszystkie zapytania przekazującego SQL z zewnętrznymi bazami danych zwraca rekordów. Na przykład SQL **aktualizacji** Instrukcja aktualizuje rekordów bez powrotu rekordów podczas SQL **wybierz** instrukcja zwracać rekordów. Aby uzyskać więcej informacji zobacz temat "ReturnsRecords Property" w pomocy DAO.  
  
 *m_strSQL*  
 Instrukcja SQL, która definiuje zapytanie wykonywane przez obiektu querydef. Właściwość SQL zawiera instrukcję SQL, która określa, jak rekordy są wybrane, grupowanych i uporządkowanych podczas wykonywania zapytania. Zapytanie służy do wybierania rekordów do uwzględnienia w obiekcie zestaw rekordów typu dynamicznego lub migawek. Można również zdefiniować zbiorczego zapytania można zmodyfikować danych bez powrotu rekordów. Wartość tej właściwości można pobrać bezpośrednio, wywołując querydef [GetSQL](../../mfc/reference/cdaoquerydef-class.md#getsql) funkcję elementu członkowskiego.  
  
 `m_strConnect`  
 Zawiera informacje o źródle bazy danych używanych w zapytaniu przekazujące. Te informacje mają postać ciągu połączenia. Aby uzyskać więcej informacji o ciągów połączenia i informacje bezpośrednio do pobrania wartości tej właściwości, zobacz [CDaoDatabase::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) funkcję elementu członkowskiego.  
  
 *m_nODBCTimeout*  
 Liczba sekund oczekiwania przed błąd upływu limitu czasu aparatu bazy danych programu Microsoft Jet występuje podczas wykonywania kwerendy w bazie danych ODBC. Podczas korzystania z bazy danych ODBC, takich jak Microsoft SQL Server, mogą wystąpić opóźnienia z powodu używania ruchu lub ciężki sieci serwera ODBC. Zamiast oczekiwania przez czas nieograniczony, można określić, jak długo aparatu Microsoft Jet czeka przed generuje błąd. Domyślna wartość limitu czasu wynosi 60 sekund. Wartość tej właściwości można pobrać bezpośrednio, wywołując querydef [GetODBCTimeout](../../mfc/reference/cdaoquerydef-class.md#getodbctimeout) funkcję elementu członkowskiego. Aby uzyskać więcej informacji zobacz temat "ODBCTimeout Property" w pomocy DAO.  
  
## <a name="remarks"></a>Uwagi  
 Querydef jest obiektem klasy [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Odwołania do podstawowej, pomocniczej i wszystkie powyższe wskazują, jak informacje zwracane przez [GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) funkcji członkowskiej klasy `CDaoDatabase`.  
  
 Informacje o pobrane przez [CDaoDatabase::GetQueryDefInfo](../../mfc/reference/cdaodatabase-class.md#getquerydefinfo) funkcja członkowska jest przechowywany w `CDaoQueryDefInfo` struktury. Wywołanie `GetQueryDefInfo` dla obiektu bazy danych, w których querydefs — kolekcja jest obiekt querydef. `CDaoQueryDefInfo`definiuje również `Dump` kompilacje funkcji członkowskiej podczas debugowania. Można użyć `Dump` do zrzutu zawartość `CDaoQueryDefInfo` obiektu. Klasa `CDaoDatabase` dostarcza również funkcje Członkowskie uzyskać bezpośredni dostęp do wszystkich właściwości zwracane w `CDaoQueryDefInfo` obiektu, dzięki czemu prawdopodobnie rzadko trzeba wywołać `GetQueryDefInfo`.  
  
 Można dołączyć nowego pola lub parametr obiektu do kolekcji pól lub parametrów obiektu querydef podstawowej bazy danych nie obsługuje typ danych określony dla nowego obiektu jest zgłaszany wyjątek.  
  
 Ustawienia daty i godziny są uzyskiwane z komputera, na którym querydef utworzenia lub ostatniej aktualizacji. W środowisku wielodostępnym użytkowników należy uzyskać te ustawienia bezpośrednio z serwera plików przy użyciu **net czasu** polecenie, aby uniknąć niezgodności ustawień właściwości DateCreated i LastUpdated.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Klasa CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)   
 [Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)
