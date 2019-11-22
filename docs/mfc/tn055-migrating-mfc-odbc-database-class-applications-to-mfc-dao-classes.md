---
title: 'TN055: migrowanie aplikacji klas baz danych MFC ODBC do klas MFC DAO'
ms.date: 09/17/2019
helpviewer_keywords:
- DAO [MFC], migration
- TN055
- migration [MFC], ODBC database applications
- ODBC classes [MFC], DAO classes
- migrating ODBC database applications [MFC]
- porting database applications to DAO
- ODBC [MFC], DAO
- porting ODBC database applications to DAO
- migrating database applications [MFC]
ms.assetid: 0f858bd1-e168-4e2e-bcd1-8debd82856e4
ms.openlocfilehash: 744e1c71476ccfbe6ea8f8359dcdb9a29efc995e
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305372"
---
# <a name="tn055-migrating-mfc-odbc-database-class-applications-to-mfc-dao-classes"></a>TN055: migrowanie aplikacji klas baz danych MFC ODBC do klas MFC DAO

> [!NOTE]
> Obiekty DAO są używane z bazami danych programu Access i są obsługiwane za pomocą pakietu Office 2013. Element DAO 3,6 jest wersją ostateczną i jest uznawany za przestarzały. Środowisko i C++ kreatory wizualne nie obsługują obiektów DAO (mimo że klasy DAO są dołączone i nadal można ich używać). Firma Microsoft zaleca korzystanie z [szablonów OLE DB](../data/oledb/ole-db-templates.md) lub [ODBC oraz MFC](../data/odbc/odbc-and-mfc.md) dla nowych projektów. Obiektów DAO należy używać tylko w przypadku zarządzania istniejącymi aplikacjami.

## <a name="overview"></a>Omówienie

W wielu sytuacjach może być pożądane Migrowanie aplikacji, które używają klas baz danych ODBC MFC do klas baz danych DAO MFC. Ta Uwaga techniczna zawiera szczegółowe informacje dotyczące większości różnic między klasami MFC ODBC i DAO. Mając na uwadze różnice, nie powinno być nadmiernie trudne do migrowania aplikacji z klas ODBC do klas MFC w razie potrzeby.

## <a name="why-migrate-from-odbc-to-dao"></a>Dlaczego należy przeprowadzić migrację z ODBC do DAO

Istnieje kilka powodów, dla których warto chcieć migrować aplikacje z klas baz danych ODBC do klas baz danych DAO, ale decyzja nie jest konieczna. Należy pamiętać, że aparat bazy danych Microsoft Jet używany przez DAO może odczytywać dowolne źródło danych ODBC, dla którego masz sterownik ODBC. Korzystanie z klas baz danych ODBC lub bezpośrednie wywoływanie ODBC może być bardziej wydajne, ale aparat bazy danych Microsoft Jet może odczytywać dane ODBC.

Niektóre proste przypadki, które ułatwiają podejmowanie decyzji ODBC/DAO. Na przykład jeśli potrzebujesz dostępu do danych w formacie, który aparat Microsoft Jet może odczytać bezpośrednio (format dostępu, format programu Excel itd.), oczywistym wyborem jest użycie klas bazy danych DAO.

Bardziej złożone przypadki powstają, gdy dane istnieją na serwerze lub na różnych różnych serwerach. W takim przypadku decyzja o korzystaniu z klas baz danych ODBC lub klas baz danych DAO jest trudna. Jeśli chcesz wykonywać takie operacje jak sprzężenia heterogeniczne (sprzęgać dane z serwerów w wielu formatach, takich jak SQL Server i Oracle), aparat bazy danych Microsoft Jet przeprowadzi sprzężenie dla Ciebie zamiast wymuszenia działania niezbędnego w przypadku korzystania z bazy danych ODBC Klasy lub bezpośrednio nazywane ODBC. Jeśli używasz sterownika ODBC, który obsługuje kursory sterowników, najlepszym wyborem może być Klasa bazy danych ODBC.

Wybór może być skomplikowany, dlatego warto napisać przykładowy kod w celu przetestowania wydajności różnych metod z uwzględnieniem specjalnych potrzeb. W tej uwadze technicznej przyjęto założenie, że podjęto decyzję o migracji z klas baz danych ODBC do klas baz danych DAO.

## <a name="similarities-between-odbc-database-classes-and-mfc-dao-database-classes"></a>Podobieństwa między klasami baz danych ODBC i klasami baz danych MFC DAO

Oryginalny projekt klas MFC ODBC był oparty na modelu obiektów DAO, który był używany w programie Microsoft Access i Microsoft Visual Basic. Oznacza to, że istnieje wiele typowych funkcji klas ODBC i DAO MFC, które nie zostaną wymienione w tej sekcji. Ogólnie rzecz biorąc modele programowania są takie same.

Aby wyróżnić kilka podobieństw:

- Zarówno klasy ODBC, jak i DAO mają obiekty bazy danych, którymi zarządza program przy użyciu podstawowego systemu zarządzania bazami danych (DBMS).

- Oba mają obiekty zestawu rekordów reprezentujące zestaw wyników zwróconych z tego systemu DBMS.

- Obiekty bazy danych i zestaw rekordów DAO mają elementy członkowskie niemal identyczne z klasami ODBC.

- W obu zestawach klas kod służący do pobierania danych jest identyczny z wyjątkiem niektórych zmian nazw obiektów i elementów członkowskich. Zmiany będą wymagane, ale zazwyczaj proces jest prostą zmianą nazwy podczas przełączania z klas ODBC do klas DAO.

Na przykład w obu modelach procedura pobierania danych polega na utworzeniu i otwarciu obiektu bazy danych, utworzeniu i otwarciu obiektu zestawu rekordów i przejściu (przeniesieniu), gdy dane wykonują kilka operacji.

## <a name="differences-between-odbc-and-dao-mfc-classes"></a>Różnice między klasami ODBC i DAO MFC

Klasy DAO obejmują więcej obiektów i bogatszy zestaw metod, ale w tej sekcji szczegółowo opisano różnice w podobnych klasach i funkcjach.

Prawdopodobnie najbardziej oczywiste różnice między klasami są zmianami nazw dla podobnych klas i funkcji globalnych. Na poniższej liście przedstawiono zmiany nazw obiektów, metod i funkcji globalnych skojarzonych z klasami baz danych:

|Klasa lub funkcja|Odpowiednik w klasach MFC DAO|
|-----------------------|-----------------------------------|
|`CDatabase`|`CDaoDatabase`|
|`CDatabase::ExecuteSQL`|`CDaoDatabase::Execute`|
|`CRecordset`|`CDaoRecordset`|
|`CRecordset::GetDefaultConnect`|`CDaoRecordset::GetDefaultDBName`|
|`CFieldExchange`|`CDaoFieldExchange`|
|`RFX_Bool`|`DFX_Bool`|
|`RFX_Byte`|`DFX_Byte`|
|`RFX_Int`|`DFX_Short`|
|`RFX_Long`|`DFX_Long`|
||`DFX_Currency`|
|`RFX_Single`|`DFX_Single`|
|`RFX_Double`|`DFX_Double`|
|`RFX_Date`<sup>1</sup>|`DFX_Date` (oparty na`COleDateTime`ach)|
|`RFX_Text`|`DFX_Text`|
|`RFX_Binary`|`DFX_Binary`|
|`RFX_LongBinary`|`DFX_LongBinary`|

<sup>1</sup> funkcja `RFX_Date` jest oparta na `CTime` i `TIMESTAMP_STRUCT`.

Poniżej przedstawiono istotne zmiany w funkcjonalności, które mogą mieć wpływ na aplikację i wymagają więcej niż proste zmiany nazw.

- Stałe i makra używane do określania elementów, takich jak typ otwartego zestawu rekordów i opcje otwierania zestawu rekordów, zostały zmienione.

   Za pomocą MFC klas ODBC wymaganych do definiowania tych opcji za pośrednictwem makr lub typów wyliczeniowych.

   Klasy DAO zawierają definicje tych opcji w pliku nagłówkowym (DBDAOINT. H). W ten sposób typem zestawu rekordów jest wyliczany element członkowski `CRecordset`, ale z obiektem DAO jest to stała. Na przykład można użyć **migawki** podczas określania typu `CRecordset` w ODBC, ale **DB_OPEN_SNAPSHOT** podczas określania typu `CDaoRecordset`.

- Domyślny typ zestawu rekordów dla `CRecordset` jest **migawką** , podczas gdy domyślny typ zestawu rekordów dla `CDaoRecordset` to **dynamiczny** (Zobacz uwagi poniżej, aby uzyskać dodatkowy problem dotyczący migawek klas ODBC).

- Klasa `CRecordset` ODBC ma opcję tworzenia zestawu rekordów tylko do przodu. W klasie `CDaoRecordset` tylko do przodu nie jest typem zestawu rekordów, ale zamiast właściwości (lub opcji) niektórych typów zestawów rekordów.

- Zestaw rekordów tylko do dołączenia podczas otwierania obiektu `CRecordset`, co oznacza, że dane zestawu rekordów mogą być odczytywane i dołączane. W przypadku `CDaoRecordset` obiektu opcja tylko do dołączania oznacza, że tylko dane zestawu rekordów mogą być dołączane (i nie odczytywane).

- Funkcje Członkowskie transakcji klas ODBC są członkami `CDatabase` i działają na poziomie bazy danych. W klasach DAO funkcje Członkowskie transakcji są członkami klasy wyższego poziomu (`CDaoWorkspace`), co może mieć wpływ na wiele obiektów `CDaoDatabase` współużytkujących ten sam obszar roboczy (przestrzeń transakcji).

- Klasa wyjątku została zmieniona. `CDBExceptions` są zgłaszane w klasach ODBC i `CDaoExceptions` w klasach DAO.

- `RFX_Date` używa `CTime` i `TIMESTAMP_STRUCT` obiektów, podczas gdy `DFX_Date` używa `COleDateTime`. `COleDateTime` jest niemal identyczny z `CTime`, ale jest oparty na 8-bajtowej **dacie** OLE zamiast 4-bajtowej **time_t** , dzięki czemu może on przechowywać znacznie większy zakres danych.

   > [!NOTE]
   > Migawki DAO (`CDaoRecordset`) są tylko do odczytu, a migawki ODBC (`CRecordset`) mogą być aktualizowalne w zależności od sterownika i używania biblioteki kursora ODBC. Jeśli używasz biblioteki kursorów, `CRecordset` migawki są aktualizowalne. Jeśli używasz dowolnego ze sterowników firmy Microsoft z pakietu sterowników pulpitu 3,0 bez biblioteki kursora ODBC, `CRecordset` migawki są tylko do odczytu. Jeśli używasz innego sterownika, zapoznaj się z dokumentacją sterownika, aby zobaczyć, czy migawki (`STATIC_CURSORS`) są tylko do odczytu.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
