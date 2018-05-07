---
title: Klasa CDaoQueryDef | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoQueryDef
- AFXDAO/CDaoQueryDef
- AFXDAO/CDaoQueryDef::CDaoQueryDef
- AFXDAO/CDaoQueryDef::Append
- AFXDAO/CDaoQueryDef::CanUpdate
- AFXDAO/CDaoQueryDef::Close
- AFXDAO/CDaoQueryDef::Create
- AFXDAO/CDaoQueryDef::Execute
- AFXDAO/CDaoQueryDef::GetConnect
- AFXDAO/CDaoQueryDef::GetDateCreated
- AFXDAO/CDaoQueryDef::GetDateLastUpdated
- AFXDAO/CDaoQueryDef::GetFieldCount
- AFXDAO/CDaoQueryDef::GetFieldInfo
- AFXDAO/CDaoQueryDef::GetName
- AFXDAO/CDaoQueryDef::GetODBCTimeout
- AFXDAO/CDaoQueryDef::GetParameterCount
- AFXDAO/CDaoQueryDef::GetParameterInfo
- AFXDAO/CDaoQueryDef::GetParamValue
- AFXDAO/CDaoQueryDef::GetRecordsAffected
- AFXDAO/CDaoQueryDef::GetReturnsRecords
- AFXDAO/CDaoQueryDef::GetSQL
- AFXDAO/CDaoQueryDef::GetType
- AFXDAO/CDaoQueryDef::IsOpen
- AFXDAO/CDaoQueryDef::Open
- AFXDAO/CDaoQueryDef::SetConnect
- AFXDAO/CDaoQueryDef::SetName
- AFXDAO/CDaoQueryDef::SetODBCTimeout
- AFXDAO/CDaoQueryDef::SetParamValue
- AFXDAO/CDaoQueryDef::SetReturnsRecords
- AFXDAO/CDaoQueryDef::SetSQL
- AFXDAO/CDaoQueryDef::m_pDAOQueryDef
- AFXDAO/CDaoQueryDef::m_pDatabase
dev_langs:
- C++
helpviewer_keywords:
- CDaoQueryDef [MFC], CDaoQueryDef
- CDaoQueryDef [MFC], Append
- CDaoQueryDef [MFC], CanUpdate
- CDaoQueryDef [MFC], Close
- CDaoQueryDef [MFC], Create
- CDaoQueryDef [MFC], Execute
- CDaoQueryDef [MFC], GetConnect
- CDaoQueryDef [MFC], GetDateCreated
- CDaoQueryDef [MFC], GetDateLastUpdated
- CDaoQueryDef [MFC], GetFieldCount
- CDaoQueryDef [MFC], GetFieldInfo
- CDaoQueryDef [MFC], GetName
- CDaoQueryDef [MFC], GetODBCTimeout
- CDaoQueryDef [MFC], GetParameterCount
- CDaoQueryDef [MFC], GetParameterInfo
- CDaoQueryDef [MFC], GetParamValue
- CDaoQueryDef [MFC], GetRecordsAffected
- CDaoQueryDef [MFC], GetReturnsRecords
- CDaoQueryDef [MFC], GetSQL
- CDaoQueryDef [MFC], GetType
- CDaoQueryDef [MFC], IsOpen
- CDaoQueryDef [MFC], Open
- CDaoQueryDef [MFC], SetConnect
- CDaoQueryDef [MFC], SetName
- CDaoQueryDef [MFC], SetODBCTimeout
- CDaoQueryDef [MFC], SetParamValue
- CDaoQueryDef [MFC], SetReturnsRecords
- CDaoQueryDef [MFC], SetSQL
- CDaoQueryDef [MFC], m_pDAOQueryDef
- CDaoQueryDef [MFC], m_pDatabase
ms.assetid: 9676a4a3-c712-44d4-8c5d-d1cc78288d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81e7d3b093da8127887878b2ac5f2af652f549c3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cdaoquerydef-class"></a>Klasa CDaoQueryDef
Reprezentuje definicji zapytania, lub "querydef" zazwyczaj jest to jeden zapisane w bazie danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDaoQueryDef : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|Konstruuje **CDaoQueryDef** obiektu. Następnie wywołaj **Otwórz** lub **Utwórz**, w zależności od potrzeb.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDaoQueryDef::Append](#append)|Dołącza querydef do bazy danych querydefs — kolekcja jako zapisaną kwerendę.|  
|[CDaoQueryDef::CanUpdate](#canupdate)|Zwraca wartość niezerową, jeśli zapytanie można zaktualizować bazy danych.|  
|[CDaoQueryDef::Close](#close)|Zamyka obiektu querydef. Po zakończeniu pracy z nim, należy zniszczyć obiektu C++.|  
|[CDaoQueryDef::Create](#create)|Tworzy obiekt querydef DAO. Użyj querydef jako tymczasowy kwerendy lub wywołanie **Append** go zapisać w bazie danych.|  
|[CDaoQueryDef::Execute](#execute)|Wykonuje zapytanie zdefiniowane przez obiekt querydef.|  
|[CDaoQueryDef::GetConnect](#getconnect)|Zwraca ciąg połączenia skojarzone z querydef. Parametry połączenia identyfikuje źródła danych. (Dla bazy danych SQL zapytań przekazujących tylko; w przeciwnym razie pusty ciąg.)|  
|[CDaoQueryDef::GetDateCreated](#getdatecreated)|Zwraca daty utworzenia zapisanego zapytania.|  
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|Zwraca datę ostatniej aktualizacji zapisanego zapytania.|  
|[CDaoQueryDef::GetFieldCount](#getfieldcount)|Zwraca liczbę pól zdefiniowanych przez querydef.|  
|[CDaoQueryDef::GetFieldInfo](#getfieldinfo)|Zwraca informacje dotyczące określonego pola zdefiniowanych w zapytaniu.|  
|[CDaoQueryDef::GetName](#getname)|Zwraca nazwę obiektu querydef.|  
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|Zwraca wartość limitu czasu używane przez ODBC (dla zapytania ODBC) po wykonaniu querydef. Jak długo określa zezwolić na ukończenie akcji kwerendy.|  
|[CDaoQueryDef::GetParameterCount](#getparametercount)|Zwraca liczbę parametrów określonych dla zapytania.|  
|[CDaoQueryDef::GetParameterInfo](#getparameterinfo)|Zwraca informacje na temat określonego parametru do zapytania.|  
|[CDaoQueryDef::GetParamValue](#getparamvalue)|Zwraca wartość określonego parametru do zapytania.|  
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|Zwraca liczbę rekordów dotyczy kwerenda.|  
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|Zwraca wartość niezerową, jeśli określone przez querydef kwerenda zwraca rekordy.|  
|[CDaoQueryDef::GetSQL](#getsql)|Zwraca ciąg SQL, który określa zapytania zdefiniowane przez querydef.|  
|[CDaoQueryDef::GetType](#gettype)|Zwraca typ zapytania: usuwanie, zaktualizować, Dołącz tworzącej tabelę i tak dalej.|  
|[CDaoQueryDef::IsOpen](#isopen)|Zwraca wartość niezerową, jeśli querydef jest otwarty i mogą być wykonywane.|  
|[CDaoQueryDef::Open](#open)|Otwiera istniejący querydef przechowywane w bazie danych querydefs — kolekcja.|  
|[CDaoQueryDef::SetConnect](#setconnect)|Ustawia parametry połączenia w przypadku kwerendy SQL dla źródła danych ODBC.|  
|[CDaoQueryDef::SetName](#setname)|Ustawia nazwę zapisanego zapytania, zastępując nazwę używany podczas tworzenia obiektu querydef.|  
|[CDaoQueryDef::SetODBCTimeout](#setodbctimeout)|Ustawia wartość limitu czasu używane przez ODBC (dla zapytania ODBC) po wykonaniu querydef.|  
|[CDaoQueryDef::SetParamValue](#setparamvalue)|Ustawia wartość określonego parametru do zapytania.|  
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|Określa, czy querydef rekordy. Ustawienie tego atrybutu na **TRUE** jest prawidłowy tylko dla zapytania przekazującego SQL.|  
|[CDaoQueryDef::SetSQL](#setsql)|Ustawia ciąg SQL, który określa zapytania zdefiniowane przez querydef.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDaoQueryDef::m_pDAOQueryDef](#m_pdaoquerydef)|Wskaźnik do interfejsu OLE dla obiekt querydef DAO.|  
|[CDaoQueryDef::m_pDatabase](#m_pdatabase)|Wskaźnik do `CDaoDatabase` obiektu, z którym jest skojarzona querydef. Querydef mogły zostać zapisane w bazie danych, czy nie.|  
  
## <a name="remarks"></a>Uwagi  
 Querydef jest obiektu dostępu do danych, który zawiera instrukcję SQL, która opisuje kwerendy i jego właściwości, takie jak "Data utworzenia" i "Limit czasu ODBC." Można również utworzyć obiekty tymczasowe querydef bez zapisywania ich, ale jest wygodne — i bardziej wydajnych — zapisać często ponownie zapytań w bazie danych. A [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiekt zachowuje kolekcję o nazwie querydefs — kolekcja zawierający jego zapisane querydefs —.  
  
> [!NOTE]
>  Klasy baz danych DAO różnią się od klasy baz danych MFC oparte na otwarte połączenie bazy danych (ODBC). Wszystkie nazwy klasy bazy danych DAO mają prefiks "CDao". Możesz nadal dostęp do źródła danych ODBC z klasy DAO. Ogólnie rzecz biorąc klas MFC DAO w oparciu mogą więcej niż klas MFC ODBC; w oparciu klasy oparte na DAO można uzyskać dostępu do danych, w tym za pomocą sterowników ODBC, za pomocą ich własnych aparatu bazy danych. Klasy oparte na DAO również obsługiwać operacji języka definicji danych (DDL), takich jak dodawanie tabel za pomocą klasy, bez konieczności wywoływanie obiektów DAO bezpośrednio.  
  
## <a name="usage"></a>Użycie  
 Za pomocą querydef obiektów albo do pracy z istniejącego zapisanego zapytania lub utworzyć nowy zapisany tymczasowego lub kwerendy:  
  
1.  We wszystkich przypadkach, należy najpierw utworzyć `CDaoQueryDef` obiektu, podając wskaźnik do [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiekt, do której należy zapytania.  
  
2.  Następnie wykonaj następujące czynności, w zależności od tego, co chcesz:  
  
    -   Aby korzystać z istniejącego zapisanego zapytania, wywołania obiektu querydef [Otwórz](#open) funkcji członkowskiej, podając nazwę zapisanego zapytania.  
  
    -   Aby utworzyć nowy zapisane zapytanie, należy wywołać obiekt querydef [Utwórz](#create) funkcji członkowskiej, podając nazwę zapytania. Następnie wywołaj [Append](#append) Aby zapisać kwerendę przez dołączenie go do bazy danych querydefs — kolekcja. **Utwórz** umieszcza querydef w stanie otwartym, tak po wywołaniu **Utwórz** Nie wywołuj **Otwórz**.  
  
    -   Aby utworzyć tymczasowy querydef, należy wywołać **Utwórz**. Przekazania pustego ciągu dla nazwy zapytania. Nie wywołuj **Append**.  
  
 Po zakończeniu przy użyciu obiektu querydef wywołać jej [Zamknij](#close) element członkowski funkcji; następnie zniszcz obiektu querydef.  
  
> [!TIP]
>  Najprostszym sposobem tworzenia zapisane kwerendy jest je utworzyć i zapisać je w bazie danych przy użyciu programu Microsoft Access. Następnie możesz otworzyć i używać ich w kodzie MFC.  
  
## <a name="purposes"></a>Do celów  
 Można użyć obiektu querydef dla żadnego z następujących celów:  
  
-   Aby utworzyć `CDaoRecordset` obiektu  
  
-   Aby wywołać obiektu **Execute** funkcji członkowskiej bezpośrednio wykonać zapytanie akcji lub przekazujący zapytanie SQL  
  
 Można użyć obiektu querydef dla dowolnego typu zapytania, łącznie z select, działania, krzyżowej, Usuń, aktualizacji, Dołącz tworzącej, definicje danych, przekazywanego SQL, Unii i zbiorcze zapytania. Typ zapytania jest określana przez instrukcji SQL, które można dostarczać zawartość. Informacje o typach zapytania, zobacz **Execute** i [GetType](#gettype) funkcji elementów członkowskich. Zestawy rekordów są często używane w celu zwrócenia wierszy wysyła zapytanie, zwykle te przy użyciu **wybierz... Z** słów kluczowych. **Wykonanie** jest najczęściej używane dla operacji zbiorczej. Aby uzyskać więcej informacji, zobacz [Execute](#execute) i [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md).  
  
## <a name="querydefs-and-recordsets"></a>Querydefs — i zestawy rekordów  
 Aby utworzyć za pomocą obiektu querydef `CDaoRecordset` obiektu, zwykle tworzenia lub otwierania querydef zgodnie z powyższym opisem. Następnie skonstruować obiektu zestawu rekordów, przekazanie wskaźnika do obiektu querydef podczas wywoływania [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open). Querydef, które przekazujesz musi być w stanie otwartym. Aby uzyskać więcej informacji, zobacz klasy [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md).  
  
 Nie można użyć querydef, aby utworzyć zestaw rekordów (najczęściej używane dla querydef), chyba że jest w stanie otwartym. Poddane querydef otwarte przez wywołanie albo **Otwórz** lub **Utwórz**.  
  
## <a name="external-databases"></a>Zewnętrznych baz danych  
 Obiekty QueryDef są preferowany sposób użycia natywnego dialekt SQL aparatu zewnętrznej bazy danych. Na przykład można utworzyć kwerendy Transact SQL (tak jak w programie Microsoft SQL Server) i zapisz go w obiekcie querydef. Należy użyć kwerendy SQL nie są oparte na aparacie bazy danych programu Microsoft Jet, musisz podać parametry połączenia, który wskazuje z zewnętrznym źródłem danych. Zapytania z ciągami prawidłowe połączenie obejścia aparatu bazy danych i przekazać zapytanie bezpośrednio na serwer zewnętrznej bazy danych w celu przetwarzania.  
  
> [!TIP]
>  Dołącz je do programu Microsoft Jet jest preferowany sposób pracy z tabel ODBC (. Baza danych MDB).  
  
 Aby uzyskać odpowiednie informacje zobacz tematy "QueryDef obiektu", "Querydefs — Kolekcja" i "CdbDatabase obiektu" w zestawie SDK DAO.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoQueryDef`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
##  <a name="append"></a>  CDaoQueryDef::Append  
 Wywołanie funkcji członkowskiej po wywołaniu metody [Utwórz](#create) można utworzyć nowego obiektu querydef.  
  
```  
virtual void Append();
```  
  
### <a name="remarks"></a>Uwagi  
 **Dołącz** querydef jest zapisywany w bazie danych przez dodanie obiektu do bazy danych querydefs — kolekcja. Można użyć obiektu querydef jako tymczasowy obiekt bez dołączenie jej, ale jeśli chcesz, aby utrwalić, należy wywołać **Append**.  
  
 Próba dołączenia obiektu querydef tymczasowego MFC zgłasza wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
##  <a name="canupdate"></a>  CDaoQueryDef::CanUpdate  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, czy można zmodyfikować obiektu querydef — takie jak zmiana jego nazwy lub parametrów SQL.  
  
```  
BOOL CanUpdate();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli jest to dozwolone, aby zmodyfikować querydef; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Można zmodyfikować obiektu querydef, jeśli:  
  
-   Nie jest oparta na bazie danych, która jest otwarta w trybie tylko do odczytu.  
  
-   Masz uprawnienia do aktualizacji bazy danych.  
  
     Zależy to od tego, czy zostały zaimplementowane funkcje zabezpieczeń. MFC nie zapewnia obsługi zabezpieczeń; musisz zaimplementować ją samodzielnie za wywoływanie obiektów DAO bezpośrednio lub za pomocą programu Microsoft Access. Zobacz temat "Właściwości uprawnień" w pomocy DAO.  
  
##  <a name="cdaoquerydef"></a>  CDaoQueryDef::CDaoQueryDef  
 Konstruuje **CDaoQueryDef** obiektu.  
  
```  
CDaoQueryDef(CDaoDatabase* pDatabase);
```  
  
### <a name="parameters"></a>Parametry  
 `pDatabase`  
 Wskaźnik do otwartego [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt może reprezentować querydef istniejących w bazy danych querydefs — kolekcja, nowe zapytanie, aby były przechowywane w kolekcji lub tymczasowe zapytania, aby nie były przechowywane. Następnym krokiem jest zależna od typu querydef:  
  
-   Jeśli obiekt reprezentuje istniejących querydef, wywołanie obiektu [Otwórz](#open) funkcji członkowskiej, aby go zainicjować.  
  
-   Jeśli obiekt reprezentuje nowe querydef można zapisać, wywołanie obiektu [Utwórz](#create) funkcję elementu członkowskiego. Spowoduje to dodanie obiektu do bazy danych querydefs — kolekcja. Następnie wywołaj `CDaoQueryDef` funkcji elementów członkowskich, które można ustawić atrybutów obiektu. Na koniec wywołania [Append](#append).  
  
-   Jeśli obiekt reprezentuje tymczasowe querydef (nie można zapisać w bazie danych), należy wywołać **Utwórz**, przekazywanie pusty ciąg nazwy zapytania. Po wywołaniu **Utwórz**, zainicjować querydef bezpośrednio ustawiając jego atrybuty. Nie wywołuj **Append**.  
  
 Aby ustawić atrybuty obiektu QueryDef, można użyć [SetName](#setname), [SetSQL](#setsql), [SetConnect](#setconnect), [SetODBCTimeout](#setodbctimeout)i [SetReturnsRecords](#setreturnsrecords) funkcji elementów członkowskich.  
  
 Po zakończeniu z obiektem querydef wywołać jej [Zamknij](#close) funkcję elementu członkowskiego. Jeśli masz wskaźnik do obiektu querydef użyj **usunąć** operator zniszczenie obiektu języka C++.  
  
##  <a name="close"></a>  CDaoQueryDef::Close  
 Wywołanie funkcji członkowskiej, po zakończeniu przy użyciu obiektu querydef.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Uwagi  
 Zamykanie querydef zwalnia obiekt DAO, ale nie niszczy zapisany obiekt querydef DAO lub języka C++ `CDaoQueryDef` obiektu. To nie jest taka sama jak [CDaoDatabase::DeleteQueryDef](../../mfc/reference/cdaodatabase-class.md#deletequerydef), które powoduje usunięcie querydef z bazy danych querydefs — kolekcja w DAO (Jeśli nie querydef tymczasowe).  
  
##  <a name="create"></a>  CDaoQueryDef::Create  
 Wywołanie tej funkcji Członkowskich do utworzenia nowej kwerendy zapisany lub nowe zapytanie tymczasowego.  
  
```  
virtual void Create(
    LPCTSTR lpszName = NULL,  
    LPCTSTR lpszSQL = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Unikatowa nazwa zapytania zapisane w bazie danych. Aby uzyskać więcej informacji o ciągu zobacz temat "CreateQueryDef Method" w pomocy DAO. Jeśli zaakceptuj wartość domyślną, ciągiem pustym querydef tymczasowy zostanie utworzony. Takie kwerendy nie jest zapisany w querydefs — kolekcja.  
  
 `lpszSQL`  
 Ciąg SQL, który definiuje zapytania. Jeśli zaakceptuj wartość domyślną **NULL**, później należy wywołać [SetSQL](#setsql) można ustawić ciąg. Do tego czasu zapytanie jest niezdefiniowany. Można jednak Użyj Niezdefiniowany zapytania, aby Otwórz zestaw rekordów; Aby uzyskać więcej informacji, zobacz uwagi. Instrukcja SQL muszą być zdefiniowane przed querydef można dołączyć do querydefs — kolekcja.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku przekazania nazwę w `lpszName`, można wywołać [Append](#append) do zapisania w bazie danych querydefs — kolekcja querydef. W przeciwnym razie obiekt jest tymczasowy querydef i nie został zapisany. W obu przypadkach querydef jest w stanie otwartym i możesz użyć jej do utworzenia [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) obiektu lub wywołać querydef [Execute](#execute) funkcję elementu członkowskiego.  
  
 Jeśli nie podasz instrukcję SQL w `lpszSQL`, nie można uruchomić zapytania z **Execute** , ale można go utworzyć zestaw rekordów. W takim przypadku MFC używa instrukcji SQL zestawu rekordów domyślne.  
  
##  <a name="execute"></a>  CDaoQueryDef::Execute  
 Wywołanie tej funkcji elementu członkowskiego, aby uruchomić zapytanie, zdefiniowane przez obiekt querydef.  
  
```  
virtual void Execute(int nOptions = dbFailOnError);
```  
  
### <a name="parameters"></a>Parametry  
 `nOptions`  
 Liczba całkowita, która określa właściwości zapytania. Powiązane informacje zobacz temat "Wykonywanie metody" w pomocy DAO. Można użyć operatora bitowego OR ( **&#124;**) do łączenia się z następujących stałych dla tego argumentu:  
  
- **dbDenyWrite** Odmów uprawnienie zapisu do innych użytkowników.  
  
- **dbInconsistent** niespójne aktualizacje.  
  
- **dbConsistent** spójne aktualizacji.  
  
- **dbSQLPassThrough** przekazywanego SQL. Powoduje, że instrukcji SQL, które mają być przekazane do bazy danych ODBC do przetwarzania.  
  
- **dbFailOnError** wartość domyślna. Wycofywanie aktualizacji, jeśli wystąpi błąd i raport błędu dla użytkownika.  
  
- **dbSeeChanges** generowanie błędów czasu wykonywania, jeśli inny użytkownik zmienia edytowania danych.  
  
> [!NOTE]
>  Aby uzyskać informacje o warunkach "niespójna" i "spójny,", zobacz temat "Wykonywanie metody" w pomocy DAO.  
  
### <a name="remarks"></a>Uwagi  
 Obiekty QueryDef używane do wykonania w ten sposób może reprezentować tylko jedną z następujących typów zapytania:  
  
-   Kwerendy akcji  
  
-   Przekazujący zapytania SQL  
  
 **Wykonanie** nie działa w przypadku zapytań zwracających rekordów, takich jak zapytania select. **Wykonanie** jest powszechnie używany do zbiorczego operację zapytania, takie jak **aktualizacji**, **Wstaw**, lub **SELECT INTO**, lub dla operacji (DDL) języka definicji danych.  
  
> [!TIP]
>  Preferowany sposób pracy z ODBC — źródła danych ma dołączyć tabel do programu Microsoft Jet (. Baza danych MDB). Aby uzyskać więcej informacji zobacz temat "Uzyskiwania dostępu do zewnętrznych baz danych z DAO" w pomocy DAO.  
  
 Wywołanie [GetRecordsAffected](#getrecordsaffected) funkcji członkowskiej klasy obiektem querydef, aby określić liczbę rekordów wpływ najnowszej **Execute** wywołania. Na przykład `GetRecordsAffected` zwraca informacje na temat liczby rekordów usunięty, zaktualizować lub wstawić podczas wykonywania zapytania akcji. Liczba zwrócił nie zreflektuje zmiany w tabelach pokrewnych, gdy w kaskadowego aktualizuje lub usuwa obowiązują.  
  
 Jeśli dołączysz zarówno **dbInconsistent** i **dbConsistent** lub jeśli nie, wynikiem jest wartość domyślna **dbInconsistent**.  
  
 **Wykonanie** nie zwraca zestawu rekordów. Przy użyciu **Execute** na zapytanie wybierające rekordy powoduje, że MFC do zgłoszenia wyjątku typu [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
##  <a name="getconnect"></a>  CDaoQueryDef::GetConnect  
 Wywołanie tej funkcji członkowskich można pobrać ciągu połączenia skojarzone ze źródłem danych querydef.  
  
```  
CString GetConnect();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) zawierający parametry połączenia dla obiektu querydef.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest używana tylko z źródła danych ODBC i niektórych sterowników ISAM. Nie jest używany z programu Microsoft Jet (. Baz danych MDB); w takim przypadku `GetConnect` zwraca pusty ciąg. Aby uzyskać więcej informacji, zobacz [SetConnect](#setconnect).  
  
> [!TIP]
>  Dołącz je do jest preferowany sposób pracy z tabel ODBC. MDB bazy danych. Aby uzyskać więcej informacji zobacz temat "Uzyskiwania dostępu do zewnętrznych baz danych z DAO" w pomocy DAO.  
  
 Informacji dotyczących parametrów połączenia Zobacz temat "Połącz Property" w pomocy DAO.  
  
##  <a name="getdatecreated"></a>  CDaoQueryDef::GetDateCreated  
 Wywołanie tej funkcji członkowskich można pobrać daty utworzenia obiektu querydef.  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiekt zawierający Data i godzina utworzenia obiektu querydef.  
  
### <a name="remarks"></a>Uwagi  
 Powiązane informacje zobacz temat "DateCreated właściwości LastUpdated" w pomocy DAO.  
  
##  <a name="getdatelastupdated"></a>  CDaoQueryDef::GetDateLastUpdated  
 Wywołanie funkcji członkowskiej można pobrać obiektu querydef datę ostatniej aktualizacji — gdy dowolne z jego właściwości zostały zmienione, takie jak jego nazwa, jego ciągu SQL lub parametrach połączenia.  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiekt zawierający Data i godzina ostatniej aktualizacji obiektu querydef.  
  
### <a name="remarks"></a>Uwagi  
 Powiązane informacje zobacz temat "DateCreated właściwości LastUpdated" w pomocy DAO.  
  
##  <a name="getfieldcount"></a>  CDaoQueryDef::GetFieldCount  
 Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę pól w zapytaniu.  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba pól zdefiniowanych w zapytaniu.  
  
### <a name="remarks"></a>Uwagi  
 `GetFieldCount` przydaje się do wszystkich pól w querydef w pętli. W tym celu użyj `GetFieldCount` w połączeniu z [GetFieldInfo](#getfieldinfo).  
  
##  <a name="getfieldinfo"></a>  CDaoQueryDef::GetFieldInfo  
 Wywołanie tej funkcji Członkowskich uzyskać różne rodzaje informacji na temat pola zdefiniowane w querydef.  
  
```  
void GetFieldInfo(
    int nIndex,  
    CDaoFieldInfo& fieldinfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

 
void GetFieldInfo(
    LPCTSTR lpszName,  
    CDaoFieldInfo& fieldinfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Liczony od zera indeks żądanego pola w kolekcji Fields querydef, wyszukiwanie według indeksu.  
  
 `fieldinfo`  
 Odwołanie do `CDaoFieldInfo` obiekt, który zwraca żądane informacje.  
  
 `dwInfoOptions`  
 Opcje, które określają, które informacje o polu do pobrania. Dostępne opcje są wyświetlane tutaj wraz z co spowodują one funkcja zwracająca:  
  
- `AFX_DAO_PRIMARY_INFO` (Ustawienie domyślne) Nazwa, typ, rozmiar, atrybuty  
  
- `AFX_DAO_SECONDARY_INFO` Informacje o podstawowym plus: porządkowym wymagane, Zezwalaj długości zerowej, pola źródła, obcego tabeli źródłowej, kolejność sortowania  
  
- `AFX_DAO_ALL_INFO` Głównych i dodatkowych informacji plus: domyślna wartość tekst sprawdzania poprawności reguły walidacji  
  
 `lpszName`  
 Ciąg zawierający nazwę żądanego pola wyszukiwania według nazwy. Można użyć [cstring —](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Uwagi  
 Opis informacje zwracane w `fieldinfo`, zobacz [cdaofieldinfo —](../../mfc/reference/cdaofieldinfo-structure.md) struktury. Ta struktura ma elementów członkowskich, które odpowiadają opisowe informacje w obszarze `dwInfoOptions` powyżej. Jeśli użytkownik żąda informacji o jeden poziom, możesz uzyskać wszystkie wcześniejsze poziomy również informacje.  
  
##  <a name="getname"></a>  CDaoQueryDef::GetName  
 Wywołaj tę funkcję elementu członkowskiego, aby pobrać nazwę kwerendy reprezentowany przez querydef.  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nazwa zapytania.  
  
### <a name="remarks"></a>Uwagi  
 QueryDef nazwy są unikatowe nazwy użytkownika. Aby uzyskać więcej informacji na temat nazw querydef zobacz temat "Właściwości Name" w pomocy DAO.  
  
##  <a name="getodbctimeout"></a>  CDaoQueryDef::GetODBCTimeout  
 Wywołanie tej funkcji członkowskich można pobrać bieżącego limitu czasu, zanim upłynie limit czasu zapytania do źródła danych ODBC.  
  
```  
short GetODBCTimeout();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba sekund przed zapytaniem upłynie limit czasu.  
  
### <a name="remarks"></a>Uwagi  
 Informacje dotyczące tego limitu czasu zobacz temat "ODBCTimeout Property" w pomocy DAO.  
  
> [!TIP]
>  Dołącz je do programu Microsoft Jet jest preferowany sposób pracy z tabel ODBC (. Baza danych MDB). Aby uzyskać więcej informacji zobacz temat "Uzyskiwania dostępu do zewnętrznych baz danych z DAO" w pomocy DAO.  
  
##  <a name="getparametercount"></a>  CDaoQueryDef::GetParameterCount  
 Wywołanie tej funkcji członkowskich można pobrać z liczbą parametrów w zapisanego zapytania.  
  
```  
short GetParameterCount();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba parametrów zdefiniowanych w zapytaniu.  
  
### <a name="remarks"></a>Uwagi  
 `GetParameterCount` jest przydatne w przypadku wszystkich parametrów w querydef w pętli. W tym celu użyj `GetParameterCount` w połączeniu z [GetParameterInfo](#getparameterinfo).  
  
 Aby uzyskać odpowiednie informacje zobacz tematy "Obiektu Parameter", "W kolekcji Parameters" i "parametry deklaracji (SQL)" w pomocy DAO.  
  
##  <a name="getparameterinfo"></a>  CDaoQueryDef::GetParameterInfo  
 Wywołanie tej funkcji Członkowskich, aby uzyskać informacje dotyczące parametru zdefiniowane w querydef.  
  
```  
void GetParameterInfo(
    int nIndex,  
    CDaoParameterInfo& paraminfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

 
void GetParameterInfo(
    LPCTSTR lpszName,  
    CDaoParameterInfo& paraminfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Liczony od zera indeks żądany parametr w kolekcji parametrów querydef, wyszukiwanie według indeksu.  
  
 `paraminfo`  
 Odwołanie do [cdaoparameterinfo —](../../mfc/reference/cdaoparameterinfo-structure.md) obiekt, który zwraca żądane informacje.  
  
 `dwInfoOptions`  
 Opcje, które określają, które informacje dotyczące parametru do pobrania. Opcja dostępna w tym miejscu znajduje oraz co go powoduje, że funkcja zwraca:  
  
- `AFX_DAO_PRIMARY_INFO` (Ustawienie domyślne) Nazwa, typ  
  
 `lpszName`  
 Ciąg zawierający nazwę parametru żądaną wyszukiwania według nazwy. Można użyć [cstring —](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Uwagi  
 Opis informacje zwracane w `paraminfo`, zobacz [cdaoparameterinfo —](../../mfc/reference/cdaoparameterinfo-structure.md) struktury. Ta struktura ma elementów członkowskich, które odpowiadają opisowe informacje w obszarze `dwInfoOptions` powyżej.  
  
 Powiązane informacje zobacz temat "parametry deklaracji (SQL)" w pomocy DAO.  
  
##  <a name="getparamvalue"></a>  CDaoQueryDef::GetParamValue  
 Wywołanie tej funkcji Członkowskich pobrać bieżącą wartość określony parametr przechowywanych w kolekcji parametrów querydef.  
  
```  
virtual COleVariant GetParamValue(LPCTSTR lpszName);  
virtual COleVariant GetParamValue(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Nazwa parametru, którego wartość należy do wyszukiwania według nazwy.  
  
 `nIndex`  
 Liczony od zera indeks parametru w kolekcji Parameters querydef, wyszukiwanie według indeksu. Możesz uzyskać tej wartości z wywołania [GetParameterCount](#getparametercount) i [GetParameterInfo](#getparameterinfo).  
  
### <a name="return-value"></a>Wartość zwracana  
 Obiekt klasy [COleVariant](../../mfc/reference/colevariant-class.md) zawierający wartości parametru.  
  
### <a name="remarks"></a>Uwagi  
 Według nazwy lub jej porządkowym w kolekcji można uzyskać dostępu do parametru.  
  
 Powiązane informacje zobacz temat "parametry deklaracji (SQL)" w pomocy DAO.  
  
##  <a name="getrecordsaffected"></a>  CDaoQueryDef::GetRecordsAffected  
 Wywołanie tej funkcji elementu członkowskiego, aby określić liczbę rekordów wpłynęła na ostatnim wywołaniu [Execute](#execute).  
  
```  
long GetRecordsAffected();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba zmodyfikowanych rekordów.  
  
### <a name="remarks"></a>Uwagi  
 Liczba zwrócił nie zreflektuje zmiany w tabelach pokrewnych, gdy w kaskadowego aktualizuje lub usuwa obowiązują.  
  
 Powiązane informacje zawiera temat "RecordsAffected Property" w pomocy DAO.  
  
##  <a name="getreturnsrecords"></a>  CDaoQueryDef::GetReturnsRecords  
 Wywołaj tę funkcję elementu członkowskiego, aby ustalić, czy querydef jest oparta na zapytanie zwracające rekordów.  
  
```  
BOOL GetReturnsRecords();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli querydef jest oparta na kwerendy zwracającą rekordów; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Funkcji członkowskiej jest używana tylko dla zapytania przekazującego SQL. Aby uzyskać więcej informacji na temat kwerend SQL, zobacz [Execute](#execute) funkcję elementu członkowskiego. Aby uzyskać więcej informacji na temat pracy z przekazujące zapytania SQL, zobacz [SetReturnsRecords](#setreturnsrecords) funkcję elementu członkowskiego.  
  
 Powiązane informacje zobacz temat "ReturnsRecords Property" w pomocy DAO.  
  
##  <a name="getsql"></a>  CDaoQueryDef::GetSQL  
 Wywołanie tej funkcji Członkowskich pobrać instrukcji SQL, który definiuje kwerendy, na której oparto querydef.  
  
```  
CString GetSQL();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Instrukcja SQL, która definiuje kwerendy, na której oparto querydef.  
  
### <a name="remarks"></a>Uwagi  
 Następnie będzie prawdopodobnie przeanalizować ciągu dla słów kluczowych, nazwy tabel i tak dalej.  
  
 Aby uzyskać odpowiednie informacje zobacz tematy "SQL Property", "Porównanie z bazy danych aparatu SQL i ANSI SQL programu Microsoft Jet" i "Zapytań bazy danych z programu SQL w kod" w pomocy DAO.  
  
##  <a name="gettype"></a>  CDaoQueryDef::GetType  
 Wywołanie tej funkcji członkowskich można określić typu zapytania querydef.  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Typ zdefiniowany przez querydef zapytania. Aby uzyskać wartości zobacz uwagi.  
  
### <a name="remarks"></a>Uwagi  
 Typ zapytania jest ustawiana przez wybrana w ciągu SQL querydef podczas tworzenia obiektu querydef lub wywołać istniejący querydef [SetSQL](#setsql) funkcję elementu członkowskiego. Zapytania zwrócone przez tę funkcję, może być jedną z następujących wartości:  
  
- **dbQSelect** wybierz  
  
- **dbQAction** akcji  
  
- **dbQCrosstab** krzyżowej  
  
- **dbQDelete** usunąć  
  
- **dbQUpdate** aktualizacji  
  
- **dbQAppend** dołączania  
  
- **dbQMakeTable** tworzące tabelę  
  
- **dbQDDL** definicji danych  
  
- **dbQSQLPassThrough** przekazywania  
  
- **dbQSetOperation** Unii  
  
- **dbQSPTBulk** używane z **dbQSQLPassThrough** do określenia kwerendę, która nie zwraca rekordów.  
  
> [!NOTE]
>  Aby utworzyć przekazujący zapytanie SQL, nie należy ustawiać **dbSQLPassThrough** stałej. To jest ustawiany automatycznie przez aparat bazy danych programu Microsoft Jet podczas tworzenia obiektu querydef i ustaw ciąg połączenia.  
  
 Informacje o ciągów SQL znajdują się w temacie [GetSQL](#getsql). Informacje o typach zapytania, zobacz [Execute](#execute).  
  
##  <a name="isopen"></a>  CDaoQueryDef::IsOpen  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, czy `CDaoQueryDef` obiekt jest obecnie otwarty.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli podano niezerowe `CDaoQueryDef` obiekt jest obecnie otwarty; w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Querydef musi być w stanie otwartym, aby użyć go do wywołania [Execute](#execute) lub utworzyć [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) obiektu. W celu uruchomienia querydef wywołanie otwarte albo [Utwórz](#create) (dla nowego querydef) lub [Otwórz](#open) (dla istniejących querydef).  
  
##  <a name="m_pdatabase"></a>  CDaoQueryDef::m_pDatabase  
 Zawiera wskaźnik do [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiekt skojarzony z obiektem querydef.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli potrzebujesz dostępu do bazy danych bezpośrednio za pomocą tego wskaźnika — na przykład uzyskać wskaźniki do innych querydef lub zestawu rekordów obiekty w kolekcjach bazy danych.  
  
##  <a name="m_pdaoquerydef"></a>  CDaoQueryDef::m_pDAOQueryDef  
 Zawiera wskaźnik do interfejsu OLE dla obiekt querydef DAO.  
  
### <a name="remarks"></a>Uwagi  
 This, wskaźnik zapewnia kompletność oraz spójność z innych klas. Jednak ponieważ raczej pełni hermetyzuje MFC DAO querydefs — jesteś prawdopodobnie nie będzie on potrzebny. Jeśli używasz, zrobić ostrożnie — w szczególności nie należy zmieniać wartości wskaźnika, jeśli nie masz pewności, co robią.  
  
##  <a name="open"></a>  CDaoQueryDef::Open  
 Wywołanie tej funkcji Członkowskich, aby otworzyć querydef wcześniej zapisanych w bazie danych querydefs — kolekcja.  
  
```  
virtual void Open(LPCTSTR lpszName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Ciąg zawierający nazwę zapisanego querydef, aby otworzyć. Można użyć [cstring —](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Uwagi  
 Po otwarciu querydef można wywołać jej [Execute](#execute) funkcji członkowskiej lub użyj querydef utworzyć [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) obiektu.  
  
##  <a name="setconnect"></a>  CDaoQueryDef::SetConnect  
 Wywołanie tej funkcji Członkowskich, aby ustawić parametry połączenia obiektu querydef.  
  
```  
void SetConnect(LPCTSTR lpszConnect);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszConnect`  
 Ciąg, który zawiera ciąg połączenia skojarzonych z nim [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ciąg połączenia jest używany do przekazania dodatkowych informacji do ODBC i sterownikami niektórych ISAM, zgodnie z potrzebami. Nie jest używany dla programu Microsoft Jet (. Bazy danych MDB).  
  
> [!TIP]
>  Dołącz je do jest preferowany sposób pracy z tabel ODBC. MDB bazy danych.  
  
 Przed wykonaniem querydef, który reprezentuje przekazujący zapytanie SQL do źródła danych ODBC, należy ustawić parametry połączenia z `SetConnect` i Wywołaj [SetReturnsRecords](#setreturnsrecords) do określenia, czy zapytanie zwraca rekordów.  
  
 Aby uzyskać więcej informacji na temat struktury i przykłady składników ciąg połączenia parametry połączenia Zobacz temat "Połącz Property" w pomocy DAO.  
  
##  <a name="setname"></a>  CDaoQueryDef::SetName  
 Wywołania funkcji członkowskiej, jeśli chcesz zmienić nazwę querydef, który nie jest tymczasowe.  
  
```  
void SetName(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Ciąg, który zawiera nową nazwę dla nontemporary zapytania w skojarzonym [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 QueryDef nazwy są unikatowe, zdefiniowane przez użytkownika nazwy. Możesz wywołać `SetName` przed querydef obiektu jest dołączany do querydefs — kolekcja.  
  
##  <a name="setodbctimeout"></a>  CDaoQueryDef::SetODBCTimeout  
 Wywołanie tej funkcji członkowskich można ustawić limitu czasu, zanim upłynie limit czasu zapytania do źródła danych ODBC.  
  
```  
void SetODBCTimeout(short nODBCTimeout);
```  
  
### <a name="parameters"></a>Parametry  
 *nODBCTimeout*  
 Liczba sekund przed zapytaniem upłynie limit czasu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska pozwala na zastępowanie domyślna liczba sekund przed kolejnych operacji na połączonego źródła danych "limit czasu." Operacja może przekroczono limit czasu ze względu na problemy z dostępem do sieci, czas przetwarzania zapytania nadmiernego i tak dalej. Wywołanie `SetODBCTimeout` przed wykonaniem kwerendy z tym querydef, jeśli chcesz zmienić wartość limitu czasu zapytania. (Zgodnie z ODBC ponownie używa połączenia, wartość limitu czasu jest takie samo dla wszystkich klientów w ramach tego samego połączenia.)  
  
 Wartością domyślną dla zapytania przekroczeń limitu czasu wynosi 60 sekund.  
  
##  <a name="setparamvalue"></a>  CDaoQueryDef::SetParamValue  
 Wywołanie tej funkcji członkowskich można ustawić wartości parametru w querydef w czasie wykonywania.  
  
```  
virtual void SetParamValue(
    LPCTSTR lpszName,  
    const COleVariant& varValue);

 
virtual void SetParamValue(
    int nIndex,  
    const COleVariant& varValue);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Nazwa parametru, którego chcesz ustawić wartość.  
  
 `varValue`  
 Wartość do ustawienia; Zobacz uwagi.  
  
 `nIndex`  
 {Numer porządkowy pozycja parametru w kolekcji Parameters querydef. Możesz uzyskać tej wartości z wywołania [GetParameterCount](#getparametercount) i [GetParameterInfo](#getparameterinfo).  
  
### <a name="remarks"></a>Uwagi  
 Parametr musi już zostały określone jako część ciągu SQL querydef. Według nazwy lub jej porządkowym w kolekcji można uzyskać dostępu do parametru.  
  
 Określ wartość do ustawienia jako `COleVariant` obiektu. Informacje o ustawianiu na żądaną wartość i wpisz Twojej `COleVariant` obiektów, zobacz klasę [COleVariant](../../mfc/reference/colevariant-class.md).  
  
##  <a name="setreturnsrecords"></a>  CDaoQueryDef::SetReturnsRecords  
 Wywołanie tej funkcji Członkowskich jako część procesu konfigurowania przekazujący zapytanie SQL do zewnętrznej bazy danych.  
  
```  
void SetReturnsRecords(BOOL bReturnsRecords);
```  
  
### <a name="parameters"></a>Parametry  
 *bReturnsRecords*  
 Przekaż **TRUE** Jeśli kwerenda w zewnętrznej bazy danych zwraca rekordy; w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 W takim przypadku należy utworzyć querydef i ustawienia swoich właściwości przy użyciu innych `CDaoQueryDef` funkcji elementów członkowskich. Aby uzyskać opis zewnętrznych baz danych, zobacz [SetConnect](#setconnect).  
  
##  <a name="setsql"></a>  CDaoQueryDef::SetSQL  
 Wywołanie tej funkcji członkowskich można ustawić instrukcji SQL, która wykonuje querydef.  
  
```  
void SetSQL(LPCTSTR lpszSQL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszSQL`  
 Ciąg zawierający pełną instrukcję SQL, odpowiedni w przypadku wykonywania. Składnia tego ciągu zależy od systemu DBMS który celów zapytania. Omówienie składni stosowanej w aparacie bazy danych programu Microsoft Jet zobacz temat "Building instrukcje w kodu SQL" w pomocy DAO.  
  
### <a name="remarks"></a>Uwagi  
 Typowy sposób użycia protokołu `SetSQL` jest skonfigurowanie obiektu querydef do użycia w przekazujący zapytanie SQL. (Składni zapytania przekazującego SQL, na docelowy system DBMS, zobacz dokumentację dla systemu DBMS).  
  
## <a name="see-also"></a>Zobacz też  
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cdaorecordset — klasa](../../mfc/reference/cdaorecordset-class.md)   
 [Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)   
 [Klasa CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)   
 [Klasa CDaoException](../../mfc/reference/cdaoexception-class.md)
