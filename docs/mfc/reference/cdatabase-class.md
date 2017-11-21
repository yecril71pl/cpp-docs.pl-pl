---
title: "Cdatabase — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDatabase
- AFXDB/CDatabase
- AFXDB/CDatabase::CDatabase
- AFXDB/CDatabase::BeginTrans
- AFXDB/CDatabase::BindParameters
- AFXDB/CDatabase::Cancel
- AFXDB/CDatabase::CanTransact
- AFXDB/CDatabase::CanUpdate
- AFXDB/CDatabase::Close
- AFXDB/CDatabase::CommitTrans
- AFXDB/CDatabase::ExecuteSQL
- AFXDB/CDatabase::GetBookmarkPersistence
- AFXDB/CDatabase::GetConnect
- AFXDB/CDatabase::GetCursorCommitBehavior
- AFXDB/CDatabase::GetCursorRollbackBehavior
- AFXDB/CDatabase::GetDatabaseName
- AFXDB/CDatabase::IsOpen
- AFXDB/CDatabase::OnSetOptions
- AFXDB/CDatabase::Open
- AFXDB/CDatabase::OpenEx
- AFXDB/CDatabase::Rollback
- AFXDB/CDatabase::SetLoginTimeout
- AFXDB/CDatabase::SetQueryTimeout
- AFXDB/CDatabase::m_hdbc
dev_langs: C++
helpviewer_keywords:
- CDatabase [MFC], CDatabase
- CDatabase [MFC], BeginTrans
- CDatabase [MFC], BindParameters
- CDatabase [MFC], Cancel
- CDatabase [MFC], CanTransact
- CDatabase [MFC], CanUpdate
- CDatabase [MFC], Close
- CDatabase [MFC], CommitTrans
- CDatabase [MFC], ExecuteSQL
- CDatabase [MFC], GetBookmarkPersistence
- CDatabase [MFC], GetConnect
- CDatabase [MFC], GetCursorCommitBehavior
- CDatabase [MFC], GetCursorRollbackBehavior
- CDatabase [MFC], GetDatabaseName
- CDatabase [MFC], IsOpen
- CDatabase [MFC], OnSetOptions
- CDatabase [MFC], Open
- CDatabase [MFC], OpenEx
- CDatabase [MFC], Rollback
- CDatabase [MFC], SetLoginTimeout
- CDatabase [MFC], SetQueryTimeout
- CDatabase [MFC], m_hdbc
ms.assetid: bd0de70a-e3c3-4441-bcaa-bbf434426ca8
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: efeb16478d78648bb813d0e25a53380ec305d5ac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdatabase-class"></a>Cdatabase — klasa
Reprezentuje połączenie ze źródłem danych, za pomocą których można korzystać w źródle danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDatabase : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDatabase::CDatabase](#cdatabase)|Konstruuje `CDatabase` obiektu. Należy zainicjować obiektu przez wywołanie metody `OpenEx` lub **Otwórz**.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDatabase::BeginTrans](#begintrans)|Uruchamia "transakcji" — szereg odwracalnego wywołań `AddNew`, **Edytuj**, **usunąć**, i **aktualizacji** funkcji elementów członkowskich klasy `CRecordset` — na połączonego źródła danych. Źródło danych musi obsługiwać transakcji dla **BeginTrans** mają wpływu.|  
|[CDatabase::BindParameters](#bindparameters)|Umożliwia tworzenie powiązań parametrów przed wywołaniem `CDatabase::ExecuteSQL`.|  
|[CDatabase::Cancel](#cancel)|Anuluje operację asynchroniczną lub procesu z drugiego wątku.|  
|[CDatabase::CanTransact](#cantransact)|Zwraca wartość niezerową, jeśli źródło danych obsługuje transakcji.|  
|[CDatabase::CanUpdate](#canupdate)|Zwraca różną od zera, jeśli `CDatabase` nadaje obiektu (nie tylko do odczytu).|  
|[CDatabase::Close](#close)|Zamyka połączenie ze źródłem danych.|  
|[CDatabase::CommitTrans](#committrans)|Kończy rozpoczynania transakcji przez **BeginTrans**. Polecenia w transakcji, które alter źródła danych są wykonywane.|  
|[CDatabase::ExecuteSQL](#executesql)|Wykonuje instrukcję SQL. Nie zwrócono żadnych rekordów danych.|  
|[CDatabase::GetBookmarkPersistence](#getbookmarkpersistence)|Identyfikuje operacje za pomocą których zakładki utrwalania obiektów zestawu rekordów.|  
|[CDatabase::GetConnect](#getconnect)|Zwraca ciąg połączenia ODBC, które są używane do łączenia z `CDatabase` obiektu ze źródłem danych.|  
|[CDatabase::GetCursorCommitBehavior](#getcursorcommitbehavior)|Określa efekt zatwierdzania transakcji dla obiektu Otwórz zestaw rekordów.|  
|[CDatabase::GetCursorRollbackBehavior](#getcursorrollbackbehavior)|Określa efekt wycofywania transakcji w obiekcie Otwórz zestaw rekordów.|  
|[CDatabase::GetDatabaseName](#getdatabasename)|Zwraca nazwę bazy danych obecnie w użyciu.|  
|[CDatabase::IsOpen](#isopen)|Zwraca różną od zera, jeśli `CDatabase` obiekt jest aktualnie połączony ze źródłem danych.|  
|[CDatabase::OnSetOptions](#onsetoptions)|Wywoływane przez platformę, by ustawić opcje standardowego połączenia. Domyślna implementacja ustawia wartość limitu czasu zapytania. Te opcje wcześniej, można ustanowić przez wywołanie metody `SetQueryTimeout`.|  
|[CDatabase::Open](#open)|Ustanawia połączenie ze źródłem danych (za pośrednictwem sterownika ODBC).|  
|[CDatabase::OpenEx](#openex)|Ustanawia połączenie ze źródłem danych (za pośrednictwem sterownika ODBC).|  
|[CDatabase::Rollback](#rollback)|Odwraca zmiany wprowadzone podczas bieżącej transakcji. Źródło danych zwraca do jego poprzedniego stanu, zgodnie z definicją w **BeginTrans** wywołania niezmieniony.|  
|[CDatabase::SetLoginTimeout](#setlogintimeout)|Ustawia liczbę sekund, po których limit czasu będzie próby połączenia źródła danych.|  
|[CDatabase::SetQueryTimeout](#setquerytimeout)|Ustawia liczbę sekund, po której bazy danych zapytania operacje będą upłynął limit czasu. Ma wpływ na wszystkie kolejne rekordów **Otwórz**, `AddNew`, **Edytuj**, i **usunąć** wywołania.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDatabase::m_hdbc](#m_hdbc)|Otwórz połączenie bazy danych (ODBC) dojścia połączenia ze źródłem danych. Typ **HDBC**.|  
  
## <a name="remarks"></a>Uwagi  
 Źródło danych jest konkretne wystąpienie danych obsługiwanych przez niektóre system zarządzania bazami (danych DBMS). Przykłady programu Microsoft SQL Server, programu Microsoft Access Borland dBASE i xBASE. Może mieć co najmniej jeden `CDatabase` obiektów aktywnych w czasie w aplikacji.  
  
> [!NOTE]
>  Jeśli pracujesz z klas obiektów DAO (Data Access), a nie klasy otwarte połączenie bazy danych (ODBC), należy użyć klasy [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) zamiast tego. Aby uzyskać więcej informacji, zobacz artykuł [omówienie: programowania bazy danych](../../data/data-access-programming-mfc-atl.md).  
  
 Aby użyć `CDatabase`, utworzenia `CDatabase` obiekt i wywołanie jego `OpenEx` funkcji członkowskiej. Spowoduje to otwarcie połączenia. Jeśli następnie utworzyć `CRecordset` obiekty korzysta z połączonego źródła danych, Przekaż Konstruktora zestawu rekordów wskaźnik do Twojej `CDatabase` obiektu. Po zakończeniu przy użyciu połączenia należy wywołać **Zamknij** element członkowski funkcji i zniszcz `CDatabase` obiektu. **Zamknij** zamyka wszystkie zestawy rekordów nie został wcześniej zamknięty.  
  
 Aby uzyskać więcej informacji na temat `CDatabase`, zobacz artykuły [źródła danych (ODBC)](../../data/odbc/data-source-odbc.md) i [omówienie: programowania bazy danych](../../data/data-access-programming-mfc-atl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDatabase`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  
  
##  <a name="begintrans"></a>CDatabase::BeginTrans  
 Wywołanie tej funkcji elementu członkowskiego, aby rozpocząć transakcji z połączonego źródła danych.  
  
```  
BOOL BeginTrans();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wywołanie zakończyło się pomyślnie, a zmiany zostaną zatwierdzone tylko ręcznie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Transakcja składa się z co najmniej jednego wywołania `AddNew`, **Edytuj**, **usunąć**, i **aktualizacji** funkcji Członkowskich `CRecordset` obiektu. Przed rozpoczęciem transakcji, `CDatabase` obiektu musi już zostaną podłączone do źródła danych przez wywołanie jego `OpenEx` lub **Otwórz** funkcję elementu członkowskiego. Aby zakończyć transakcji, należy wywołać [CommitTrans](#committrans) Zaakceptuj wszystkie zmiany do źródła danych (i ich) lub zadzwoń [wycofywania](#rollback) przerwania cała transakcja. Wywołanie **BeginTrans** po Otwórz wszystkie zestawy rekordów zaangażowane w transakcji i jak blisko rzeczywiste operacje aktualizacji jak to możliwe.  
  
> [!CAUTION]
>  W zależności od sterownika ODBC otwieranie rekordów przed wywołaniem **BeginTrans** mogą powodować problemy podczas wywoływania **wycofywania**. Należy sprawdzić określonego sterownika, którego używasz. Na przykład gdy za pomocą sterownika Microsoft Access uwzględnione w programie Microsoft ODBC pulpitu sterownik pakiet 3.0, należy uwzględnić wymagania aparatu bazy danych Jet nie powinna rozpoczynać transakcji na wszystkie bazy danych ma otwartego kursora. W klasami baz danych MFC, otwórz kursora oznacza, że otwarty `CRecordset` obiektu. Aby uzyskać więcej informacji, zobacz [68 Uwaga techniczna](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md).  
  
 **BeginTrans** może również zablokować rekordów danych na serwerze, w zależności od żądanego współbieżności i możliwości źródła danych. Aby uzyskać informacje o danych, blokowania, zobacz artykuł [zestaw rekordów: blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md).  
  
 Zdefiniowane przez użytkownika transakcje opisano szczegółowo w artykule [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).  
  
 **BeginTrans** ustanawia stanu, do którego sekwencji transakcji można wycofać (odwrócone). Ustanowienie nowy stan dla wycofań zatwierdzić wszystkie bieżącej transakcji wywoływać **BeginTrans** ponownie.  
  
> [!CAUTION]
>  Wywoływanie **BeginTrans** ponownie bez wywoływania elementu **CommitTrans** lub **wycofywania** jest błędem.  
  
 Wywołanie [CanTransact](#cantransact) funkcji członkowskiej, aby sprawdzić, czy sterownik obsługuje transakcji określonej bazy danych. Należy także wywołać [GetCursorCommitBehavior](#getcursorcommitbehavior) i [GetCursorRollbackBehavior](#getcursorrollbackbehavior) ustalenie obsługę zachowywania kursora.  
  
 Aby uzyskać więcej informacji na temat transakcji, zobacz artykuł [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).  
  
### <a name="example"></a>Przykład  
  Zapoznaj się z artykułem [transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
##  <a name="bindparameters"></a>CDatabase::BindParameters  
 Zastąpienie `BindParameters` potrzebne do powiązania parametrów przed wywołaniem [CDatabase::ExecuteSQL](#executesql).  
  
```  
virtual void BindParameters(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Parametry  
 `hstmt`  
 Dojście instrukcji ODBC, dla którego chcesz powiązać parametry.  
  
### <a name="remarks"></a>Uwagi  
 Takie rozwiązanie jest przydatne, gdy nie ma potrzeby wynik określony na podstawie procedury składowanej.  
  
 W przypadku zastąpienia, należy wywołać **SQLBindParameters** i powiązane funkcje ODBC do powiązania parametrów. Zastąpienia przed wywołania do wywołania MFC `ExecuteSQL`. Nie należy wywołać **SQLPrepare**; `ExecuteSQL` wywołania **SQLExecDirect** i niszczy **hstmt**, która jest używana tylko raz.  
  
##  <a name="cancel"></a>CDatabase::Cancel  
 Wywołanie funkcji członkowskiej na żądanie, że źródło danych anulować operacji asynchronicznej w toku lub procesu z drugiego wątku.  
  
```  
void Cancel();
```  
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, że klasach MFC ODBC nie jest już przetwarzania asynchronicznego; Próba wykonania operacji asychronous, możesz bezpośrednio wywołanie funkcji interfejsu API ODBC [SQLSetConnectOption](https://msdn.microsoft.com/library/ms713564.aspx). Aby uzyskać więcej informacji, zobacz [operacji asynchronicznych](https://msdn.microsoft.com/library/ms713563.aspx) w zestawie Windows SDK.  
  
##  <a name="cantransact"></a>CDatabase::CanTransact  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, czy bazy danych umożliwia transakcji.  
  
```  
BOOL CanTransact() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli podano niezerowe zestawów rekordów za pomocą tej `CDatabase` obiektu Zezwalaj transakcji; w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać informacje dotyczące transakcji, zobacz artykuł [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="canupdate"></a>CDatabase::CanUpdate  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, czy `CDatabase` obiektu zezwala na aktualizacje.  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli różną od zera `CDatabase` obiektu zezwala na aktualizacje; w przeciwnym razie wartość 0, wskazującą, albo że możesz przekazać **TRUE** w `bReadOnly` przy otwieraniu `CDatabase` obiektu lub że źródła danych, sam jest tylko do odczytu. Źródło danych jest tylko do odczytu wywołanie funkcji interfejsu API ODBC **SQLGetInfo** dla **SQL_DATASOURCE_READ_ONLY** zwraca "y".  
  
### <a name="remarks"></a>Uwagi  
 Nie wszystkie sterowniki obsługują aktualizacji.  
  
##  <a name="cdatabase"></a>CDatabase::CDatabase  
 Konstruuje `CDatabase` obiektu.  
  
```  
CDatabase();
```  
  
### <a name="remarks"></a>Uwagi  
 Po konstruowania obiektu, należy wywołać jej `OpenEx` lub **Otwórz** funkcji członkowskiej nawiązać połączenia ze źródłem danych określonym.  
  
 Użytkownik może okazać się osadzić `CDatabase` obiektów w klasie dokumentu.  
  
### <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono przy użyciu `CDatabase` w `CDocument`-klasy.  
  
 [!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]  
  
 [!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]  
  
##  <a name="close"></a>CDatabase::Close  
 Wywołania funkcji członkowskiej, jeśli chcesz odłączyć od źródła danych.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Uwagi  
 Należy zamknąć wszystkie zestawy rekordów skojarzone z `CDatabase` obiekt przed wywołaniem funkcji członkowskiej. Ponieważ **Zamknij** nie niszczy `CDatabase` obiektu, można użyć ponownie obiektu przez otwarcie nowego połączenia z tym samym źródle danych lub innego źródła danych.  
  
 Wszystkie oczekujące `AddNew` lub **Edytuj** instrukcje korzystania z bazy danych — zestawy rekordów są anulowane, a wszystkie oczekujące transakcje są wycofywane. Wszystkie zestawy rekordów zależne `CDatabase` obiektu pozostają w stanie niezdefiniowany.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]  
  
##  <a name="committrans"></a>CDatabase::CommitTrans  
 Wywołanie funkcji członkowskiej po zakończeniu transakcji.  
  
```  
BOOL CommitTrans();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli te aktualizacje zostały pomyślnie zatwierdzone; w przeciwnym razie 0. Jeśli **CommitTrans** kończy się niepowodzeniem, stan źródła danych jest niezdefiniowany. Należy sprawdzić danych można określić jego stanu.  
  
### <a name="remarks"></a>Uwagi  
 Transakcja składa się z szeregu wywołań `AddNew`, **Edytuj**, **usunąć**, i **aktualizacji** funkcji Członkowskich `CRecordset` obiekt, który zostało uruchomione z wywołanie [BeginTrans](#begintrans) funkcję elementu członkowskiego. **CommitTrans** zatwierdza transakcji. Domyślnie aktualizacje zostają zatwierdzone natychmiast; wywoływanie **BeginTrans** powoduje, że zaangażowanie aktualizacji opóźnione aż do **CommitTrans** jest wywoływana.  
  
 Do czasu wywołania **CommitTrans** do końca transakcji, można wywołać [wycofywania](#rollback) funkcji członkowskiej, aby przerwać transakcji i pozostawić źródła danych na oryginalnego stanu. Aby rozpocząć nowej transakcji, należy wywołać **BeginTrans** ponownie.  
  
 Aby uzyskać więcej informacji na temat transakcji, zobacz artykuł [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).  
  
### <a name="example"></a>Przykład  
  Zapoznaj się z artykułem [transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
##  <a name="executesql"></a>CDatabase::ExecuteSQL  
 Wywołania funkcji członkowskiej, gdy trzeba wykonać polecenia SQL bezpośrednio.  
  
```  
void ExecuteSQL(LPCTSTR lpszSQL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszSQL`  
 Wskaźnik do zerem ciąg zawierający prawidłowe polecenie SQL do wykonania. Można przekazać [cstring —](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Uwagi  
 Utwórz polecenie jako ciąg znaków zakończony znakiem null. `ExecuteSQL`zwraca rekordów danych. Do działania na rekordy, należy użyć obiektu zestawu rekordów.  
  
 Większość poleceń dla źródła danych są wystawiane przez zestaw rekordów obiektów, które obsługuje poleceń dotyczących wybierania danych, wstawianie nowych rekordów, usuwanie rekordów i edycji rekordów. Jednak nie wszystkie funkcje ODBC bezpośrednio jest obsługiwana przez klasy baz danych, dlatego czasami może być konieczne nawiązać bezpośrednie połączenie SQL za pomocą `ExecuteSQL`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]  
  
##  <a name="getbookmarkpersistence"></a>CDatabase::GetBookmarkPersistence  
 Wywołanie tej funkcji elementu członkowskiego, aby określić stan trwały zakładki na obiekt zestawu rekordów po pewnych operacji.  
  
```  
DWORD GetBookmarkPersistence() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maska bitowa identyfikujący operacji za pomocą których zakładki utrwalić obiektu zestawu rekordów. Aby uzyskać więcej informacji zobacz uwagi.  
  
### <a name="remarks"></a>Uwagi  
 Na przykład, jeśli wywołujesz `CRecordset::GetBookmark` , a następnie wywołać `CRecordset::Requery`, zakładki uzyskane z `GetBookmark` może nie być już prawidłowe. Należy wywołać `GetBookmarkPersistence` przed wywołaniem `CRecordset::SetBookmark`.  
  
 W poniższej tabeli wymieniono wartości maski bitów, które można łączyć dla wartości zwracanej z `GetBookmarkPersistence`.  
  
|Wartość maski bitowej|Trwałość zakładki|  
|-------------------|--------------------------|  
|`SQL_BP_CLOSE`|Zakładki są prawidłowe po **Requery** operacji.|  
|`SQL_BP_DELETE`|Zakładki dla wiersza jest nieprawidłowy po **usunąć** operacji w tym wierszu.|  
|`SQL_BP_DROP`|Zakładki są prawidłowe po **Zamknij** operacji.|  
|`SQL_BP_SCROLL`|Zakładki są prawidłowe po dowolnym **Przenieś** operacji. To po prostu Określa, czy zakładki są obsługiwane w zestawie rekordów zwrócony przez `CRecordset::CanBookmark`.|  
|`SQL_BP_TRANSACTION`|Zakładki są prawidłowe po transakcji jest zatwierdzona lub wycofana.|  
|`SQL_BP_UPDATE`|Zakładki dla wiersza jest nieprawidłowy po **aktualizacji** operacji w tym wierszu.|  
|`SQL_BP_OTHER_HSTMT`|Zakładki skojarzone z jednego obiektu zestawu rekordów są prawidłowe dla drugiego zestawu wierszy.|  
  
 Aby uzyskać więcej informacji o tej wartości zwracanej, zobacz opis funkcji interfejsu API ODBC **SQLGetInfo** w zestawie Windows SDK. Aby uzyskać więcej informacji na temat zakładki, zobacz artykuł [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
##  <a name="getconnect"></a>CDatabase::GetConnect  
 Wywołanie tej funkcji członkowskich można pobrać parametry połączenia używane podczas wywołania `OpenEx` lub `Open` który połączony `CDatabase` obiektu ze źródłem danych.  
  
```  
const CString GetConnect() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `const` [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) zawierający parametry połączenia w przypadku `OpenEx` lub `Open` została wywołana; w przeciwnym razie wartość pustego ciągu.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [CDatabase::Open](#open) opis sposobu tworzenia ciągu połączenia.  
  
##  <a name="getcursorcommitbehavior"></a>CDatabase::GetCursorCommitBehavior  
 Wywołanie tej funkcji Członkowskich, aby określić sposób [CommitTrans](#committrans) operacji wpływa na kursory obiektów Otwórz zestaw rekordów.  
  
```  
int GetCursorCommitBehavior() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość wskazująca, efekt transakcji w obiektach Otwórz zestaw rekordów. Aby uzyskać więcej informacji zobacz uwagi.  
  
### <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono możliwe wartości zwracane dla `GetCursorCommitBehavior` i ich wpływ na otwieranie zestawu rekordów.  
  
|Wartość zwracana|Wpływ na crecordset — obiekty|  
|------------------|----------------------------------|  
|`SQL_CB_CLOSE`|Wywołanie `CRecordset::Requery` bezpośrednio po zatwierdzania transakcji.|  
|`SQL_CB_DELETE`|Wywołanie `CRecordset::Close` bezpośrednio po zatwierdzania transakcji.|  
|`SQL_CB_PRESERVE`|Należy kontynuować `CRecordset` operacji.|  
  
 Aby uzyskać więcej informacji o tej wartości zwracanej, zobacz opis funkcji interfejsu API ODBC **SQLGetInfo** w zestawie Windows SDK. Aby uzyskać więcej informacji na temat transakcji, zobacz artykuł [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="getcursorrollbackbehavior"></a>CDatabase::GetCursorRollbackBehavior  
 Wywołanie tej funkcji Członkowskich, aby określić sposób [wycofywania](#rollback) operacji wpływa na kursory obiektów Otwórz zestaw rekordów.  
  
```  
int GetCursorRollbackBehavior() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość wskazująca, efekt transakcji w obiektach Otwórz zestaw rekordów. Aby uzyskać więcej informacji zobacz uwagi.  
  
### <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono możliwe wartości zwracane dla `GetCursorRollbackBehavior` i ich wpływ na otwieranie zestawu rekordów.  
  
|Wartość zwracana|Wpływ na crecordset — obiekty|  
|------------------|----------------------------------|  
|`SQL_CB_CLOSE`|Wywołanie `CRecordset::Requery` bezpośrednio po wycofanie transakcji.|  
|`SQL_CB_DELETE`|Wywołanie `CRecordset::Close` bezpośrednio po wycofanie transakcji.|  
|`SQL_CB_PRESERVE`|Należy kontynuować `CRecordset` operacji.|  
  
 Aby uzyskać więcej informacji o tej wartości zwracanej, zobacz opis funkcji interfejsu API ODBC **SQLGetInfo** w zestawie Windows SDK. Aby uzyskać więcej informacji na temat transakcji, zobacz artykuł [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="getdatabasename"></a>CDatabase::GetDatabaseName  
 Wywołanie tej funkcji Członkowskich pobrać nazwy bazy danych w aktualnie połączony (pod warunkiem, że źródło danych określa nazwanego obiektu o nazwie "baza danych").  
  
```  
CString GetDatabaseName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) zawierającą nazwę bazy danych w przypadku powodzenia; w przeciwnym razie, pustą `CString`.  
  
### <a name="remarks"></a>Uwagi  
 To nie jest taka sama jak nazwa źródła danych (DSN) określona w `OpenEx` lub **Otwórz** wywołania. Co `GetDatabaseName` zwraca zależy od ODBC. Ogólnie rzecz biorąc bazy danych to kolekcja tabel. Jeśli ta jednostka ma nazwę, `GetDatabaseName` zwraca go.  
  
 Na przykład można wyświetlać tę nazwę w pozycji. Jeśli wystąpi błąd podczas pobierania nazwy z ODBC, `GetDatabaseName` zwraca pustą **cstring —**.  
  
##  <a name="isopen"></a>CDatabase::IsOpen  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, czy `CDatabase` obiekt jest aktualnie połączony ze źródłem danych.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli podano niezerowe `CDatabase` obiekt jest aktualnie połączony; w przeciwnym razie wartość 0.  
  
##  <a name="m_hdbc"></a>CDatabase::m_hdbc  
 Zawiera publiczne dojścia do połączenia ze źródłem danych ODBC — "dojścia połączenia".  
  
### <a name="remarks"></a>Uwagi  
 Zazwyczaj użytkownik zostanie nie ma potrzeby uzyskiwania dostępu do tego elementu członkowskiego zmiennej bezpośrednio. Zamiast tego platformę przydziela dojście podczas wywoływania `OpenEx` lub **Otwórz**. Platformę zwalnia dojście podczas wywoływania **usunąć** operator na `CDatabase` obiektu. Należy pamiętać, że **Zamknij** funkcji członkowskiej nie deallocate dojście.  
  
 Jednak w pewnych okolicznościach może być konieczne użycie dojście bezpośrednio. Na przykład, jeśli należy wywołać funkcji ODBC API bezpośrednio, a nie za pośrednictwem klasy `CDatabase`, może być konieczne dojścia połączenia, aby przekazać jako parametru. Zobacz poniższy przykład kodu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]  
  
##  <a name="onsetoptions"></a>CDatabase::OnSetOptions  
 Struktura wywołuje funkcji członkowskiej podczas bezpośrednio wykonywania instrukcji SQL z `ExecuteSQL` funkcję elementu członkowskiego.  
  
```  
virtual void OnSetOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>Parametry  
 `hstmt`  
 Dojście instrukcji ODBC, dla których zostały ustawione opcje.  
  
### <a name="remarks"></a>Uwagi  
 `CRecordset::OnSetOptions`również wywołuje funkcję tego elementu członkowskiego.  
  
 `OnSetOptions`Ustawia wartość limitu czasu logowania. Jeśli zostały poprzednich wywołań `SetQueryTimeout` i funkcja członkowska `OnSetOptions` odzwierciedla bieżące wartości; w przeciwnym razie ustawia wartości domyślne.  
  
> [!NOTE]
>  Przed MFC 4.2 `OnSetOptions` także ustawić tryb przetwarzania albo snychronous lub asynchronicznej. Począwszy od MFC 4.2, wszystkie operacje są synchroniczne. Aby wykonać operację asynchroniczną, należy wybrać bezpośrednie wywołanie funkcji interfejsu API ODBC **SQLSetPos**.  
  
 Nie trzeba zastąpić `OnSetOptions` Aby zmienić wartość limitu czasu. Zamiast tego, aby dostosować wartość limitu czasu kwerendy, należy wywołać `SetQueryTimeout` przed utworzeniem zestawu rekordów; `OnSetOptions` będzie używać nowej wartości. Zestaw wartości dotyczą kolejnych operacji na wszystkich zestawów rekordów lub bezpośrednich wywołań SQL.  
  
 Zastąpienie `OnSetOptions` Jeśli chcesz ustawić opcje dodatkowe. Zastąpienia powinny wywoływać klasę podstawową `OnSetOptions` przed lub po wywołaniu funkcji interfejsu API ODBC **SQLSetStmtOption**. Wykonaj w sposób określony w ramach domyślną implementację `OnSetOptions`.  
  
##  <a name="open"></a>CDatabase::Open  
 Wywołanie tej funkcji Członkowskich zainicjować nowo utworzone `CDatabase` obiektu.  
  
```  
virtual BOOL Open(
    LPCTSTR lpszDSN,  
    BOOL bExclusive = FALSE,  
    BOOL bReadOnly = FALSE,  
    LPCTSTR lpszConnect = _T("ODBC;"),  
    BOOL bUseCursorLib = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszDSN`  
 Określa nazwę źródła danych — zarejestrowaną nazwę z ODBC, za pomocą programu ODBC Administrator. Jeśli określono wartość DSN w `lpszConnect` (w postaci "DSN =\<źródło danych >"), nie może być określony w ponownie w `lpszDSN`. W takim przypadku `lpszDSN` powinien być **NULL**. W przeciwnym razie można przekazać **NULL** mają do zaoferowania użytkownikowi okno dialogowe źródła danych, w którym użytkownik może wybrać źródło danych. Aby uzyskać więcej informacji zobacz uwagi.  
  
 `bExclusive`  
 Nie są obsługiwane w tej wersji biblioteki klas. Obecnie potwierdzenia zakończy się niepowodzeniem, jeśli ten parametr ma **TRUE**. Źródło danych jest zawsze otwierany jako udostępniony (nie wyłącznie).  
  
 `bReadOnly`  
 **Wartość TRUE,** Jeśli jest planowane połączenie tylko do odczytu i uniemożliwić aktualizację ze źródłem danych. Wszystkie zależne zestawy rekordów dziedziczą tego atrybutu. Wartość domyślna to **FALSE**.  
  
 `lpszConnect`  
 Określa parametry połączenia. Parametry połączenia łączy informacje, w tym prawdopodobnie nazwa źródła danych, prawidłowy identyfikator użytkownika w źródle danych, ciąg uwierzytelniania użytkownika (hasło, jeśli źródło danych wymaga jednej) i inne informacje. Parametry połączenia całego muszą być poprzedzone ciągiem "ODBC;" (wielkich i małych liter). "ODBC;" ciąg jest używany w celu wskazania, czy połączenie ma źródła danych ODBC; jest to górę zgodności podczas przyszłych wersji biblioteki klas może obsługiwać z systemem innym niż ODBC — źródła danych.  
  
 `bUseCursorLib`  
 **Wartość TRUE,** Jeśli chcesz DLL biblioteki kursorów ODBC do załadowania. Biblioteka kursorów maski niektóre funkcje odpowiedni sterownik ODBC, efektywnie uniemożliwia korzystanie z zestawów dynamicznych (Jeśli sterownik obsługuje je). Kursory obsługiwane, gdy jest ładowany z biblioteki kursorów są statyczne migawki i kursory tylko do przodu. Wartość domyślna to **TRUE**. Jeśli zamierzasz utworzyć zestaw rekordów obiektu bezpośrednio z `CRecordset` bez wynikające z niego, nie powinien ładować z biblioteki kursorów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli połączenie zostanie nawiązane pomyślnie; w przeciwnym razie wartość 0, jeśli użytkownik wybierze anulowania, jeśli wyświetlone okno dialogowe z pytaniem, aby uzyskać więcej informacji o połączeniu. We wszystkich innych przypadkach w ramach zgłasza wyjątek.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt bazy danych muszą zostać zainicjowane, przed użyciem do konstruowania obiektu zestawu rekordów.  
  
> [!NOTE]
>  Wywoływanie [OpenEx](#openex) funkcja członkowska jest preferowany sposób połączyć się ze źródłem danych i zainicjowania obiektu bazy danych.  
  
 Jeśli parametry w Twojej **Otwórz** wywołania nie zawiera wystarczających informacji do nawiązania połączenia, sterownik ODBC otwiera okno dialogowe, aby uzyskać niezbędne informacje od użytkownika. Podczas wywoływania **Otwórz**, ciąg połączenia, `lpszConnect`, są przechowywane przez użytkowników w `CDatabase` obiektu i jest dostępny przez wywołanie metody [GetConnect](#getconnect) funkcji członkowskiej.  
  
 Jeśli chcesz, można otworzyć własne okno dialogowe przed wywołaniem **Otwórz** Aby uzyskać informacje od użytkownika, takie jak hasła, następnie dodać te informacje do przekazania do ciągu połączenia **Otwórz**. Można zapisać parametry połączenia przekazywania, więc można używać dalej czasu wywołania aplikacji **Otwórz** na `CDatabase` obiektu.  
  
 Umożliwia także parametry połączenia dla różnych poziomów autoryzacji logowania (dla innej `CDatabase` obiektu) lub w celu przedstawienia inne informacje specyficzne dla źródła danych. Aby uzyskać więcej informacji dotyczących parametrów połączenia zobacz rozdział 5 w zestawie Windows SDK.  
  
 Istnieje możliwość limit czasu nawiązywania połączenia, jeśli na przykład host bazami danych jest niedostępny. Jeśli próba połączenia nie powiedzie się, **Otwórz** zgłasza `CDBException`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]  
  
##  <a name="openex"></a>CDatabase::OpenEx  
 Wywołanie tej funkcji Członkowskich zainicjować nowo utworzone `CDatabase` obiektu.  
  
```  
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,  
    DWORD dwOptions = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszConnectString`  
 Określa parametry połączenia ODBC. Dotyczy to również nazwa źródła danych, a także inne opcjonalne informacje, takie jak nazwa użytkownika i hasło. Na przykład "DSN = SQLServer_Source; IDENTYFIKATOR UID = SA; PWD = abc123 "ciąg połączenia możliwe. Należy pamiętać, że w przypadku przekazania **NULL** dla `lpszConnectString`, okno dialogowe źródła danych pojawi się monit o wybranie źródła danych.  
  
 `dwOptions`  
 Maska bitowa, która określa kombinację następujących wartości. Wartość domyślna to 0, co oznacza, że baza danych zostanie otwarta jako udostępniony z prawem do zapisu, DLL Biblioteka kursorów ODBC nie zostanie załadowany i wyświetli okno dialogowe połączenia ODBC tylko wtedy, gdy nie ma wystarczających informacji do nawiązania połączenia.  
  
- **CDatabase::openExclusive** nie są obsługiwane w tej wersji biblioteki klas. Źródło danych jest zawsze otwierany jako udostępniony (nie wyłącznie). Obecnie potwierdzenia kończy się niepowodzeniem, jeśli określono tę opcję.  
  
- **CDatabase::openReadOnly** otworzyć źródła danych jako tylko do odczytu.  
  
- **CDatabase::useCursorLib** obciążenia z biblioteki kursorów ODBC biblioteki DLL. Biblioteka kursorów maski niektóre funkcje odpowiedni sterownik ODBC, efektywnie uniemożliwia korzystanie z zestawów dynamicznych (Jeśli sterownik obsługuje je). Kursory obsługiwane, gdy jest ładowany z biblioteki kursorów są statyczne migawki i kursory tylko do przodu. Jeśli zamierzasz utworzyć zestaw rekordów obiektu bezpośrednio z `CRecordset` bez wynikające z niego, nie powinien ładować z biblioteki kursorów.  
  
- **CDatabase::noOdbcDialog** nie są wyświetlane okno dialogowe połączenia ODBC, niezależnie od tego, czy podano za mało informacji o połączeniu.  
  
- **CDatabase::forceOdbcDialog** zawsze wyświetla okno dialogowe połączenia ODBC.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli połączenie zostanie nawiązane pomyślnie; w przeciwnym razie wartość 0, jeśli użytkownik wybierze anulowania, jeśli wyświetlone okno dialogowe z pytaniem, aby uzyskać więcej informacji o połączeniu. We wszystkich innych przypadkach w ramach zgłasza wyjątek.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt bazy danych muszą zostać zainicjowane, przed użyciem do konstruowania obiektu zestawu rekordów.  
  
 Jeśli `lpszConnectString` parametru w Twojej `OpenEx` wywołania nie zawiera wystarczających informacji do nawiązania połączenia, sterownik ODBC otwiera okno dialogowe uzyskać niezbędne informacje od użytkownika, pod warunkiem nie ustawiono **cdatabase —:: noOdbcDialog** lub **CDatabase::forceOdbcDialog** w `dwOptions` parametru. Podczas wywoływania `OpenEx`, ciąg połączenia, `lpszConnectString`, są przechowywane przez użytkowników w `CDatabase` obiektu i jest dostępny przez wywołanie metody [GetConnect](#getconnect) funkcję elementu członkowskiego.  
  
 Jeśli chcesz, można otworzyć własne okno dialogowe przed wywołaniem `OpenEx` uzyskać informacje od użytkownika, takie jak hasła, a następnie dodać te informacje do przekazania do ciągu połączenia `OpenEx`. Można zapisać parametry połączenia przekazywania, więc można używać dalej czasu wywołania aplikacji `OpenEx` na `CDatabase` obiektu.  
  
 Umożliwia także parametry połączenia dla różnych poziomów autoryzacji logowania (dla innej `CDatabase` obiektu) lub w celu przedstawienia inne informacje specyficzne dla źródła danych. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz rozdział 6 w *Podręcznik programisty ODBC*.  
  
 Istnieje możliwość limit czasu nawiązywania połączenia, jeśli na przykład host bazami danych jest niedostępny. Jeśli próba połączenia nie powiedzie się, `OpenEx` zgłasza `CDBException`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]  
  
##  <a name="rollback"></a>CDatabase::Rollback  
 Wywołanie tej funkcji Członkowskich, aby wycofać zmiany wprowadzone podczas transakcji.  
  
```  
BOOL Rollback();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli transakcja została pomyślnie cofnięta; w przeciwnym razie 0. Jeśli **wycofywania** wywołanie zakończy się niepowodzeniem, źródła danych i transakcji stanów jest nieokreślona. Jeśli **wycofywania** zwraca wartość 0, należy sprawdzić źródło danych, aby określić jego stan.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie `CRecordset` `AddNew`, **Edytuj**, **usunąć**, i **aktualizacji** wywołania wykonane od momentu ostatniego [BeginTrans](#begintrans) są wycofana Stan, który istniał w momencie tego wywołania.  
  
 Po wywołaniu **wycofywania**transakcji znajduje się nad i należy wywołać **BeginTrans** ponownie przez inną transakcję. Rekord aktualna, aby było można wywołać **BeginTrans** staje się bieżącym rekordem ponownie po **wycofywania**.  
  
 Po wycofaniu rekordu, które były aktualne przed wycofaniem pozostaje bieżącej. Aby uzyskać szczegółowe informacje o stanie zestawu rekordów i źródła danych po wycofanie, zobacz artykuł [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).  
  
### <a name="example"></a>Przykład  
  Zapoznaj się z artykułem [transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md).  
  
##  <a name="setlogintimeout"></a>CDatabase::SetLoginTimeout  
 Wywołanie tej funkcji Członkowskich — przed wywołaniem `OpenEx` lub **Otwórz** — do przesłonięcia domyślna liczba sekund przed danych próba połączenia ze źródłem upłynie limit czasu.  
  
```  
void SetLoginTimeout(DWORD dwSeconds);
```  
  
### <a name="parameters"></a>Parametry  
 `dwSeconds`  
 Liczba sekund przed próba połączenia upłynie limit czasu.  
  
### <a name="remarks"></a>Uwagi  
 Próba połączenia może upłynął limit czasu, jeśli na przykład systemu DBMS nie jest dostępna. Wywołanie **SetLoginTimeout** po utworzymy niezainicjowanej `CDatabase` obiekt, ale przed wywołaniem `OpenEx` lub **Otwórz**.  
  
 Wartość domyślna limitów czasu logowania to 15 sekund. Nie wszystkie źródła danych obsługuje możliwość określenia wartości limitu czasu logowania. Jeśli źródło danych nie obsługuje limitu czasu, możesz uzyskać dane wyjściowe śledzenia, ale nie wystąpił wyjątek. Wartość 0 oznacza "nieskończoność".  
  
##  <a name="setquerytimeout"></a>CDatabase::SetQueryTimeout  
 Wywołanie tej funkcji elementu członkowskiego, aby zastąpić domyślną liczbę sekund, przed kolejnych operacji na limit czasu źródła danych połączenia.  
  
```  
void SetQueryTimeout(DWORD dwSeconds);
```  
  
### <a name="parameters"></a>Parametry  
 `dwSeconds`  
 Liczba sekund przed próbą zapytania upłynie limit czasu.  
  
### <a name="remarks"></a>Uwagi  
 Operacja może przekroczono limit czasu ze względu na problemy z dostępem do sieci, czas przetwarzania zapytania nadmiernego i tak dalej. Wywołanie `SetQueryTimeout` przed otwarciem zestawu rekordów lub przed wywołaniem w zestawie rekordów `AddNew`, **aktualizacji** lub **usunąć** funkcje Członkowskie, jeśli chcesz zmienić wartość limitu czasu zapytania. Ustawienie ma wpływ na wszystkie kolejne **Otwórz**, `AddNew`, **aktualizacji**, i **usunąć** wywołania żadnych zestawów rekordów skojarzonych z tym `CDatabase` obiektu. Wartość limitu czasu zapytania dla zestawu rekordów po otwarciu nie zmiana wartości dla zestawu rekordów. Na przykład kolejnych **Przenieś** operacje nie należy używać nowej wartości.  
  
 Wartość domyślna limitów czasu zapytania to 15 sekund. Nie wszystkie źródła danych obsługuje możliwość określenia wartości limitu czasu zapytania. Jeśli ustawisz wartość limitu czasu kwerendy 0 nie przekroczony limit czasu; Komunikacja z źródła danych może przestać odpowiadać. To działanie może być przydatne podczas programowania. Jeśli źródło danych nie obsługuje limitu czasu, możesz uzyskać dane wyjściowe śledzenia, ale nie wystąpił wyjątek.  
  
## <a name="see-also"></a>Zobacz też  
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Crecordset — klasa](../../mfc/reference/crecordset-class.md)
