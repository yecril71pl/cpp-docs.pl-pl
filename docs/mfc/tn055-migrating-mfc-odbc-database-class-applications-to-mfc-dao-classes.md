---
title: 'TN055: Migrowanie aplikacji klas baz danych MFC ODBC do klas MFC DAO'
ms.date: 06/20/2018
f1_keywords:
- vc.mfc.odbc
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
ms.openlocfilehash: f8e0d8e50f05e86c35e0f8b7f324533bffea6f25
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399671"
---
# <a name="tn055-migrating-mfc-odbc-database-class-applications-to-mfc-dao-classes"></a>TN055: Migrowanie aplikacji klas baz danych MFC ODBC do klas MFC DAO

> [!NOTE]
> Środowiska Visual C++ i kreatory nie obsługują DAO (mimo że uwzględniono klas DAO i nadal można użyć). Firma Microsoft zaleca się, że używasz [szablony OLE DB](../data/oledb/ole-db-templates.md) lub [ODBC i MFC](../data/odbc/odbc-and-mfc.md) dla nowych projektów. DAO należy używać tylko w zachowaniu istniejących aplikacji.

## <a name="overview"></a>Omówienie

W wielu sytuacjach może być pożądane, aby przeprowadzić migrację aplikacji używających klasy bazy danych programu MFC ODBC do klas baz danych DAO MFC. Ta uwaga techniczna dotyczył większość różnic między klas MFC ODBC i DAO. Z różnicami należy pamiętać, nie powinna być zbyt trudne do migracji aplikacji z klasy ODBC do klas MFC, w razie potrzeby.

## <a name="why-migrate-from-odbc-to-dao"></a>Dlaczego warto przeprowadzić migrację z ODBC do DAO

Istnieje kilka powodów dlaczego warto dokonać migracji aplikacji z klas baz danych ODBC do klas baz danych DAO, ale decyzja nie musi być proste lub oczywiste. Warto pamiętać, to czy aparat bazy danych Microsoft Jet, który jest używany przez DAO przeczytasz dowolnego źródła danych ODBC, do której masz sterownika ODBC. Może być bardziej efektywne, aby użyć klasy bazy danych ODBC lub wywołania ODBC bezpośrednio samodzielnie, ale aparat bazy danych Microsoft Jet można odczytać danych ODBC.

Czasami prosty, wchodzące w ODBC/DAO decyzji łatwo. Na przykład gdy wystarczy tylko dostęp do danych w formacie, który może być odczytany aparatu Microsoft Jet bezpośrednio (format programu Access, formatu programu Excel i tak dalej) jest użycie klas baz danych DAO oczywistym wyborem.

Bardziej złożonych przypadkach wystąpić, gdy dane istnieje na serwerze lub na wielu różnych serwerach. W tym przypadku decyzji o użyciu klas baz danych ODBC i klasy baz danych DAO jest trudne. Jeśli chcesz zrobić elementy, takie jak heterogenicznych sprzężenia (łączenie danych z serwerów w wielu formatach, takich jak SQL Server i Oracle), a następnie aparatu bazy danych Microsoft Jet będzie wykonać ich sprzężenie należy zamiast co zmuszało do wykonują pracę niezbędne, jeśli używana baza danych ODBC Klasy lub bezpośrednio wywołana ODBC. Jeśli używasz sterownika ODBC obsługującego kursory sterownika, najlepszym rozwiązaniem może być klas baz danych ODBC.

Wybór może być skomplikowane, dzięki czemu możesz chcieć napisać przykładowy kod do testowania wydajności różnych metod, biorąc pod uwagę swoje specjalnymi potrzebami. Ta uwaga techniczna przyjęto założenie, wprowadzono decyzja o migracji z klas baz danych ODBC do klas baz danych DAO.

## <a name="similarities-between-odbc-database-classes-and-mfc-dao-database-classes"></a>Podobieństwa między usługami klas baz danych ODBC i klasy baz danych MFC DAO

Oryginalny projekt klasach MFC ODBC zostało oparte na modelu obiektów DAO, które było używane w programie Microsoft Access i Microsoft Visual Basic. Oznacza to, że jest wiele typowych funkcji klasy ODBC i DAO MFC, które nie wszystkie wyświetlane jest w tej sekcji. Ogólnie rzecz biorąc modele programowania są takie same.

Aby zaznaczyć kilka podobieństwa:

- Klasy ODBC i DAO mają obiektów bazy danych o zarządzanych za pomocą podstawowego system zarządzania bazami danych (DBMS).

- Mają obiektów rekordów reprezentujących zestaw wyników zwrócony z tego systemu DBMS.

- Obiekty bazy danych i zestaw rekordów DAO członkowie prawie identyczna klasy ODBC.

- Za pomocą obu zestawów klasy identyczne, z wyjątkiem niektórych zmiany nazw obiektów i elementów członkowskich jest kod, aby pobrać dane. Zmiany będzie wymagana, ale zwykle proces to zmiana nazwy proste, w przypadku przechodzenia z klasy ODBC do klas DAO.

Na przykład w obu modelach procedury do pobierania danych jest utworzyć i otworzyć obiektu bazy danych, utworzyć i otworzyć obiekt zestawu rekordów i poruszać (przenoszenie) danych, wykonywania pewnych operacji.

## <a name="differences-between-odbc-and-dao-mfc-classes"></a>Różnice między klasy DAO MFC i ODBC

Klasy DAO zawierają więcej obiektów i metod z bogatszego zestawu, ale w tej sekcji dotyczył tylko różnice w podobnych klasy i funkcje.

Prawdopodobnie najbardziej oczywiste różnice między klasami są zmiany nazwy dla podobnych klasy i funkcje globalne. Na poniższej liście przedstawiono zmiany nazw obiektów, metody i funkcje globalne skojarzone z klas baz danych:

|Klasa lub funkcja|Odpowiedniej wartości wyrażonej w klas MFC DAO|
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
|`RFX_Date`<sup>1</sup>|`DFX_Date` (`COleDateTime`— na podstawie)|
|`RFX_Text`|`DFX_Text`|
|`RFX_Binary`|`DFX_Binary`|
|`RFX_LongBinary`|`DFX_LongBinary`|

<sup>1</sup> `RFX_Date` funkcja opiera się na `CTime` i `TIMESTAMP_STRUCT`.

Poniżej przedstawiono najważniejszych zmian funkcji, które mogą wpływać na aplikację i wymagają więcej niż prosta nazwa zmian.

- Stałe i makra używane do określenia elementów, takich jak zestaw rekordów otwórz typ i zestaw rekordów, Otwórz opcje zostały zmienione.

   Klasy ODBC MFC niezbędnej do zdefiniowania tych opcji za pomocą makra lub wyliczany typów.

   Przy użyciu klas DAO DAO znajduje się definicja tych opcji w pliku nagłówkowym (DBDAOINT. GODZ.). Zatem typ zbioru rekordów jest wyliczany elementem członkowskim `CRecordset`, ale za pomocą DAO jest stałą, zamiast tego. Na przykład można użyć **migawki** podczas określania typu `CRecordset` w ODBC, ale **DB_OPEN_SNAPSHOT** podczas określania typu `CDaoRecordset`.

- Domyślny typ zestawu rekordów dla `CRecordset` jest **migawki** podczas domyślnego zestawu rekordów typu `CDaoRecordset` jest **dynamiczny** (patrz uwaga poniżej dla dodatkowego problemu dotyczących migawek klasy ODBC).

- ODBC `CRecordset` klasa ma możliwość utworzenia typu rekordów. W `CDaoRecordset` klasy, tylko do przodu nie jest typu zestawu rekordów, ale raczej właściwości (lub opcja) niektórych typów zestawów rekordów.

- Zestaw rekordów tylko do dołączania podczas otwierania `CRecordset` obiektu przeznaczona czy w zestawie rekordów danych może odczytać i dołączany. Za pomocą `CDaoRecordset` obiektu tylko do dołączania opcji oznacza, że dosłownie w zestawie rekordów danych może składać dołączany (a nie do odczytu).

- Funkcje Członkowskie transakcji do klas ODBC są elementami członkowskimi `CDatabase` i działają na poziomie bazy danych. Do klas DAO transakcji funkcji elementów członkowskich są elementami członkowskimi wyższy poziom klasy (`CDaoWorkspace`) i w związku z tym może mieć wpływ na wiele `CDaoDatabase` obiektów udostępnianie tego samego obszaru roboczego (miejsca transakcji).

- Klasy wyjątków został zmieniony. `CDBExceptions` są zgłaszane w klasach ODBC i `CDaoExceptions` klas DAO.

- `RFX_Date` używa `CTime` i `TIMESTAMP_STRUCT` obiektów podczas `DFX_Date` używa `COleDateTime`. `COleDateTime` Jest prawie identyczna `CTime`, ale opiera się na OLE 8-bajtowych **data** zamiast 4-bajtowych **time_t** , może on przechowywać znacznie większy zakres danych.

   > [!NOTE]
   > DAO (`CDaoRecordset`) migawki są tylko do odczytu podczas ODBC (`CRecordset`) migawki mogą być można aktualizować w zależności od tego, czy sterownik i korzystanie z biblioteki kursorów ODBC. Jeśli korzystasz z biblioteki kursorów `CRecordset` migawki są aktualizowalne. Jeśli używasz dowolnego sterowniki firmy Microsoft 3.0 pakiet sterownika pulpitu bez z biblioteki kursorów ODBC `CRecordset` migawki są przeznaczone tylko do odczytu. Jeśli używasz innego sterownika w dokumentacji sterownika czy migawek (`STATIC_CURSORS`) są przeznaczone tylko do odczytu.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
