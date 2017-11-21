---
title: 'TN055: Migrowanie aplikacji klas baz danych MFC ODBC do klas MFC DAO | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.odbc
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bb9b4041f9c288b40a6efb1ef7978d323bad2fb4
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="tn055-migrating-mfc-odbc-database-class-applications-to-mfc-dao-classes"></a>TN055: migrowanie aplikacji klas baz danych MFC ODBC do klas MFC DAO
> [!NOTE]
>  Środowiska Visual C++ i kreatorów nie obsługują DAO (mimo że uwzględniono klasy DAO i nadal można ich używać). Firma Microsoft zaleca użycie [szablony OLE DB](../data/oledb/ole-db-templates.md) lub [ODBC i MFC](../data/odbc/odbc-and-mfc.md) dla nowych projektów. Obiekty DAO należy używać tylko w zachowaniu istniejących aplikacji.  
  
 **Omówienie**  
  
 W wielu sytuacjach może być pożądane, aby przeprowadzić migrację aplikacji używających klasy bazy danych MFC ODBC do klas baz danych DAO MFC. Ta uwaga techniczna szczegółowe większość różnice między klas MFC ODBC i DAO. Różnice, pamiętając nie należy zbyt trudne do migracji aplikacji z klasy ODBC do klas MFC w razie potrzeby.  
  
 **Dlaczego migracji z ODBC do DAO**  
  
 Istnieje wiele powodów dlaczego warto aplikacje można migrować z klasami baz danych ODBC do klas baz danych DAO, ale decyzja nie jest zawsze proste lub oczywiste. Jedyną operacją, należy wziąć pod uwagę jest czy aparat bazy danych programu Microsoft Jet, który jest używany przez obiekty DAO mogą odczytywać wszystkie źródła danych ODBC, dla którego masz sterownik ODBC. Może być bardziej efektywne korzystanie z klasami baz danych ODBC lub wywołania ODBC bezpośrednio samodzielnie, ale aparat bazy danych programu Microsoft Jet można odczytać danych ODBC.  
  
 Czasami proste, które łatwo decyzji ODBC/DAO. Na przykład, gdy wystarczy tylko dostęp do danych w formacie, który może być odczytany aparatu Microsoft Jet bezpośrednio (format programu Access, format programu Excel i tak dalej) oczywistym wyborze jest użycie klasy baz danych DAO.  
  
 Bardziej złożonych przypadkach wystąpić, gdy danych istnieje na serwerze lub na wielu różnych serwerach. W takim przypadku decyzji o użyciu klas baz danych ODBC i klasy baz danych DAO jest trudne. Aby wykonać czynności, takich jak sprzężenia heterogenicznych (łączenie danych z serwerów w wielu formatach, takich jak SQL Server i Oracle), a następnie aparat bazy danych programu Microsoft Jet wykona sprzężenie należy zamiast wymuszania wykonywania pracy niezbędne, jeśli używasz bazy danych ODBC Klasy lub bezpośrednio wywoływane ODBC. Jeśli używasz obsługującego kursory sterownik sterownika ODBC, najlepszym rozwiązaniem może być klasy baz danych ODBC.  
  
 Wybór może być skomplikowane, dlatego warto zapisać niektórych przykładowy kod do testowania wydajności różnych metod podanych potrzeb specjalne. Ta uwaga techniczna zakłada wprowadzone decyzja o migracji z klasami baz danych ODBC do klas baz danych DAO.  
  
 **Podobieństwa między usługami klasy baz danych ODBC i klasy baz danych MFC DAO**  
  
 Oryginalny projekt klasy MFC ODBC została oparta na modelu obiektów DAO, które było używane w programie Microsoft Access i Microsoft Visual Basic. Oznacza to, że ma wiele cech wspólnych klasy ODBC i DAO MFC, które nie wszystkie znajdzie się w tej sekcji. Ogólnie rzecz biorąc modele programowania są takie same.  
  
 Aby zaznaczyć kilka podobieństwa:  
  
-   Klasy ODBC i DAO mają obiektów bazy danych o zarządzanych za pomocą podstawowej system zarządzania bazami (danych DBMS).  
  
-   Mają obiektów zestawu rekordów, reprezentujący zestaw wyników zwrócony z tego systemu DBMS.  
  
-   Obiekty bazy danych i zestaw rekordów DAO mieć elementy członkowskie niemal identyczna z klasy ODBC.  
  
-   Z obu zestawach klasy kod służący do pobierania danych jest identyczny z wyjątkiem zmiany nazwy niektórych obiektów i element członkowski. Zmiany będzie wymagane, ale proces jest zazwyczaj zmianę nazwy proste podczas przełączania z klasy ODBC do DAO — klasy.  
  
 Na przykład w obu modeli procedury do pobierania danych jest do tworzenia i otworzyć obiektu bazy danych, tworzenie i otworzyć obiektu zestawu rekordów i poruszać (przenoszenia) danych wykonywania pewnych operacji.  
  
 **Różnice między klasy DAO MFC i ODBC**  
  
 Klasy DAO zawiera więcej obiektów i bogaty zestaw metod, ale ta sekcja zawiera tylko szczegółowe różnic podobne klas i funkcji.  
  
 Najbardziej oczywisty różnice między klasami są prawdopodobnie zmiany nazwy podobne klasy i funkcje globalne. Na poniższej liście przedstawiono zmiany nazw obiektów, metod i funkcje globalne skojarzone z klasami baz danych:  
  
|Klasa lub funkcja|Odpowiednik w klas MFC DAO|  
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
|**Rfx_date —\***|**DFX_Date** (`COleDateTime`— na podstawie)|  
|`RFX_Text`|`DFX_Text`|  
|`RFX_Binary`|`DFX_Binary`|  
|`RFX_LongBinary`|`DFX_LongBinary`|  
  
 \*`RFX_Date` Funkcja jest oparta na `CTime` i **TIMESTAMP_STRUCT**.  
  
 Poniżej przedstawiono najważniejszych zmian funkcji, które mogą mieć wpływ na aplikację i wymagać więcej niż prosta nazwa zmian.  
  
-   Stałe i makra używana do określania typu Otwórz np. zestaw rekordów i rekordów Otwórz opcje zostały zmienione.  
  
     Klasy ODBC MFC wymagane do zdefiniowania tych opcji za pomocą makra lub wyliczyć typów.  
  
     Klasy DAO DAO znajduje się definicja tych opcji w pliku nagłówka (DBDAOINT. H). W związku z tym typ zbioru rekordów jest elementem wyliczenia `CRecordset`, ale z DAO jest stałą, zamiast tego. Na przykład można użyć **migawki** podczas określania typu `CRecordset` w ODBC, ale **DB_OPEN_SNAPSHOT** podczas określania typu `CDaoRecordset`.  
  
-   Domyślny typ rekordów dla `CRecordset` jest **migawki** podczas domyślnego zestawu rekordów typu `CDaoRecordset` jest **dynamiczny** (zobacz uwaga poniżej dodatkowe problemu dotyczących migawek klasy ODBC).  
  
-   ODBC `CRecordset` klasa ma możliwość utworzenia typu rekordów. W `CDaoRecordset` klasa, tylko do przodu nie jest typu zestawu rekordów, ale raczej właściwości (lub opcji) niektórych typów zestawów rekordów.  
  
-   Dołącz rekordów podczas otwierania `CRecordset` obiektu oznaczało, że zestawu rekordów danych można odczytać, a dołączone. Z `CDaoRecordset` obiektu, opcja tylko Dołącz dosłownie oznacza, że zestawu rekordów danych może być tylko dołączona (i nie do odczytu).  
  
-   Funkcje Członkowskie klas ODBC transakcji są elementami członkowskimi `CDatabase` i działa na poziomie bazy danych. W klasach DAO funkcji Członkowskich transakcji są elementami członkowskimi wyższym poziomie klasy (`CDaoWorkspace`) i w związku z tym może mieć wpływ na wiele `CDaoDatabase` obiektów udostępnianie tego samego obszaru roboczego (transakcji miejsca).  
  
-   Klasa wyjątku został zmieniony. **CDBExceptions** są zgłaszane w klasach ODBC i **CDaoExceptions** w klasach DAO.  
  
-   `RFX_Date`używa `CTime` i **TIMESTAMP_STRUCT** obiekty podczas **DFX_Date** używa `COleDateTime`. `COleDateTime` Jest niemal identyczna z `CTime`, ale jest oparta na OLE 8-bajtowych **data** zamiast 4-bajtowych `time_t` , może przechowywać znacznie większego zakresu danych.  
  
    > [!NOTE]
    >  Obiekty DAO (`CDaoRecordset`) migawki są tylko do odczytu podczas ODBC (`CRecordset`) migawki mogą być aktualizowalne w zależności od sterownika i korzystanie z biblioteki kursorów ODBC. Jeśli korzystasz z biblioteki kursorów `CRecordset` migawki są aktualizowalne. Jeśli używasz dowolnej sterowniki firmy Microsoft 3.0 pakiet sterownika pulpitu bez z biblioteki kursorów ODBC `CRecordset` migawki są tylko do odczytu. Jeśli używasz innym sterownikiem w dokumentacji sterownika czy migawek (**STATIC_CURSORS**) są tylko do odczytu.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

