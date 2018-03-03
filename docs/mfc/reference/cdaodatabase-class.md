---
title: Klasa CDaoDatabase | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDaoDatabase
- AFXDAO/CDaoDatabase
- AFXDAO/CDaoDatabase::CDaoDatabase
- AFXDAO/CDaoDatabase::CanTransact
- AFXDAO/CDaoDatabase::CanUpdate
- AFXDAO/CDaoDatabase::Close
- AFXDAO/CDaoDatabase::Create
- AFXDAO/CDaoDatabase::CreateRelation
- AFXDAO/CDaoDatabase::DeleteQueryDef
- AFXDAO/CDaoDatabase::DeleteRelation
- AFXDAO/CDaoDatabase::DeleteTableDef
- AFXDAO/CDaoDatabase::Execute
- AFXDAO/CDaoDatabase::GetConnect
- AFXDAO/CDaoDatabase::GetName
- AFXDAO/CDaoDatabase::GetQueryDefCount
- AFXDAO/CDaoDatabase::GetQueryDefInfo
- AFXDAO/CDaoDatabase::GetQueryTimeout
- AFXDAO/CDaoDatabase::GetRecordsAffected
- AFXDAO/CDaoDatabase::GetRelationCount
- AFXDAO/CDaoDatabase::GetRelationInfo
- AFXDAO/CDaoDatabase::GetTableDefCount
- AFXDAO/CDaoDatabase::GetTableDefInfo
- AFXDAO/CDaoDatabase::GetVersion
- AFXDAO/CDaoDatabase::IsOpen
- AFXDAO/CDaoDatabase::Open
- AFXDAO/CDaoDatabase::SetQueryTimeout
- AFXDAO/CDaoDatabase::m_pDAODatabase
- AFXDAO/CDaoDatabase::m_pWorkspace
dev_langs:
- C++
helpviewer_keywords:
- CDaoDatabase [MFC], CDaoDatabase
- CDaoDatabase [MFC], CanTransact
- CDaoDatabase [MFC], CanUpdate
- CDaoDatabase [MFC], Close
- CDaoDatabase [MFC], Create
- CDaoDatabase [MFC], CreateRelation
- CDaoDatabase [MFC], DeleteQueryDef
- CDaoDatabase [MFC], DeleteRelation
- CDaoDatabase [MFC], DeleteTableDef
- CDaoDatabase [MFC], Execute
- CDaoDatabase [MFC], GetConnect
- CDaoDatabase [MFC], GetName
- CDaoDatabase [MFC], GetQueryDefCount
- CDaoDatabase [MFC], GetQueryDefInfo
- CDaoDatabase [MFC], GetQueryTimeout
- CDaoDatabase [MFC], GetRecordsAffected
- CDaoDatabase [MFC], GetRelationCount
- CDaoDatabase [MFC], GetRelationInfo
- CDaoDatabase [MFC], GetTableDefCount
- CDaoDatabase [MFC], GetTableDefInfo
- CDaoDatabase [MFC], GetVersion
- CDaoDatabase [MFC], IsOpen
- CDaoDatabase [MFC], Open
- CDaoDatabase [MFC], SetQueryTimeout
- CDaoDatabase [MFC], m_pDAODatabase
- CDaoDatabase [MFC], m_pWorkspace
ms.assetid: 8ff5b342-964d-449d-bef1-d0ff56aadf6d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 48646e0635098aceea957f93015a5de93515096d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cdaodatabase-class"></a>Klasa CDaoDatabase
Reprezentuje połączenie z bazą danych za pomocą których może wykonywać operacje na danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDaoDatabase : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDaoDatabase::CDaoDatabase](#cdaodatabase)|Konstruuje `CDaoDatabase` obiektu. Wywołanie **Otwórz** nawiązywania połączenia z bazą danych obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDaoDatabase::CanTransact](#cantransact)|Zwraca wartość niezerową, jeśli baza danych obsługuje transakcji.|  
|[CDaoDatabase::CanUpdate](#canupdate)|Zwraca różną od zera, jeśli `CDaoDatabase` nadaje obiektu (nie tylko do odczytu).|  
|[CDaoDatabase::Close](#close)|Zamyka połączenie z bazą danych.|  
|[CDaoDatabase::Create](#create)|Tworzy podstawowego obiektu bazy danych DAO i inicjuje `CDaoDatabase` obiektu.|  
|[CDaoDatabase::CreateRelation](#createrelation)|Definiuje nowej relacji między tabelami w bazie danych.|  
|[CDaoDatabase::DeleteQueryDef](#deletequerydef)|Usuwa obiekt querydef zapisane w bazie danych querydefs — kolekcja.|  
|[CDaoDatabase::DeleteRelation](#deleterelation)|Usuwa istniejącej relacji między tabelami w bazie danych.|  
|[CDaoDatabase::DeleteTableDef](#deletetabledef)|Usuwa definicję tabeli w bazie danych. Spowoduje to usunięcie tabeli rzeczywiste i wszystkie jej dane.|  
|[CDaoDatabase::Execute](#execute)|Wykonuje zapytanie akcji. Wywoływanie **Execute** dla zapytania, które zwraca wyniki zgłasza wyjątek.|  
|[CDaoDatabase::GetConnect](#getconnect)|Zwraca ciąg połączenia używany do łączenia `CDaoDatabase` obiektu do bazy danych. Używane dla ODBC.|  
|[CDaoDatabase::GetName](#getname)|Zwraca nazwę bazy danych obecnie w użyciu.|  
|[CDaoDatabase::GetQueryDefCount](#getquerydefcount)|Zwraca liczbę zapytań zdefiniowane dla bazy danych.|  
|[CDaoDatabase::GetQueryDefInfo](#getquerydefinfo)|Zwraca informacje o określonej kwerendy w bazie danych.|  
|[CDaoDatabase::GetQueryTimeout](#getquerytimeout)|Zwraca liczbę sekund, po której bazy danych zapytania operacje będą upłynął limit czasu. Ma wpływ na wszystkie kolejne otworzyć, dodawanie nowych aktualizacji i Edytuj operacje i inne operacje dotyczące źródeł danych ODBC (tylko) takie jak **Execute** wywołania.|  
|[CDaoDatabase::GetRecordsAffected](#getrecordsaffected)|Zwraca liczbę rekordów wpływ ostatniej aktualizacji, edytować lub operacja dodania lub przez wywołanie do **Execute**.|  
|[CDaoDatabase::GetRelationCount](#getrelationcount)|Zwraca liczbę relacje zdefiniowane między tabelami w bazie danych.|  
|[CDaoDatabase::GetRelationInfo](#getrelationinfo)|Zwraca informacje o określonej relacji zdefiniowanych między tabelami w bazie danych.|  
|[CDaoDatabase::GetTableDefCount](#gettabledefcount)|Zwraca liczbę tabel w bazie danych.|  
|[CDaoDatabase::GetTableDefInfo](#gettabledefinfo)|Zwraca informacje o określonej tabeli w bazie danych.|  
|[CDaoDatabase::GetVersion](#getversion)|Zwraca wersję aparatu bazy danych skojarzony z bazą danych.|  
|[CDaoDatabase::IsOpen](#isopen)|Zwraca różną od zera, jeśli `CDaoDatabase` obiekt jest aktualnie połączony z bazą danych.|  
|[CDaoDatabase::Open](#open)|Ustanawia połączenie z bazą danych.|  
|[CDaoDatabase::SetQueryTimeout](#setquerytimeout)|Limit czasu będzie Ustawia liczbę sekund, po której bazy danych zapytania operacje (w ODBC tylko źródła danych). Ma wpływ na wszystkie kolejne otworzyć, dodawanie nowych aktualizacji i operacji usunięcia.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDaoDatabase::m_pDAODatabase](#m_pdaodatabase)|Wskaźnik do podstawowego obiektu bazy danych DAO.|  
|[CDaoDatabase::m_pWorkspace](#m_pworkspace)|Wskaźnik do [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) obiekt, który zawiera bazę danych i definiuje jego przestrzeni transakcji.|  
  
## <a name="remarks"></a>Uwagi  
 Informacje o obsługiwanych formatach bazy danych, zobacz [GetName](../../mfc/reference/cdaoworkspace-class.md#getname) funkcję elementu członkowskiego. Może mieć co najmniej jeden `CDaoDatabase` obiektów active naraz w danym "obszaru roboczego," reprezentowanego przez [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) obiektu. Obszar roboczy obsługuje kolekcję obiektów bazy danych, nazywane kolekcji baz danych.  
  
> [!NOTE]
>  Klasy baz danych MFC DAO różnią się od klasy baz danych MFC ODBC — na podstawie. Wszystkie nazwy klasy bazy danych DAO mają prefiks "CDao". Klasa `CDaoDatabase` udostępnia interfejsem podobnym do tej klasy ODBC [cdatabase —](../../mfc/reference/cdatabase-class.md). Główną różnicą jest to, że `CDatabase` uzyskuje dostęp do systemu DBMS za pośrednictwem otwarte połączenie bazy danych (ODBC) i sterownik ODBC dla tego systemu DBMS. `CDaoDatabase`uzyskuje dostęp do danych za pośrednictwem obiektu DAO (Data Access) oparte na aparacie bazy danych programu Microsoft Jet. Ogólnie rzecz biorąc klas MFC DAO w oparciu mogą więcej niż klas MFC ODBC; w oparciu klasy oparte na DAO można uzyskać dostępu do danych, w tym za pomocą sterowników ODBC, za pomocą ich własnych aparatu bazy danych. Klasy oparte na DAO również obsługiwać operacji języka definicji danych (DDL), takich jak dodawanie tabel za pomocą klasy, bez konieczności wywoływanie obiektów DAO bezpośrednio.  
  
## <a name="usage"></a>Użycie  
 Obiekty bazy danych można utworzyć domyślnie podczas tworzenia obiektów zestawu rekordów. Ale można również jawnie tworzyć obiektów bazy danych. Aby użyć istniejącej bazy danych, używając `CDaoDatabase`, wykonaj jedną z następujących czynności:  
  
-   Utworzyć `CDaoDatabase` przekazania wskaźnik do otwartego obiektu [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) obiektu.  
  
-   Lub konstrukcji `CDaoDatabase` obiektu bez określania obszaru roboczego (MFC tworzy obiekt tymczasowego obszaru roboczego).  
  
 Aby utworzyć nowy Microsoft Jet (. MDB) bazy danych, utworzyć `CDaoDatabase` obiekt i wywołanie jego [Utwórz](#create) funkcję elementu członkowskiego. Czy *nie* wywołać **Otwórz** po **Utwórz**.  
  
 Aby otworzyć istniejącą bazę danych, należy utworzyć `CDaoDatabase` obiekt i wywołanie jego [Otwórz](#open) funkcję elementu członkowskiego.  
  
 Dowolną z poniższych metod dołącza obiektu bazy danych DAO do kolekcji baz danych obszaru roboczego i otwiera połączenie z danymi. Jeśli następnie utworzymy [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md), [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), lub [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) obiekty korzysta z połączenia bazy danych, Przekaż konstruktorów dla tych obiektów wskaźnik do Twojej `CDaoDatabase` obiektu. Po zakończeniu przy użyciu połączenia należy wywołać [Zamknij](#close) element członkowski funkcji i zniszcz `CDaoDatabase` obiektu. **Zamknij** zamyka wszystkie zestawy rekordów nie został wcześniej zamknięty.  
  
## <a name="transactions"></a>Transakcje  
 Przetwarzanie transakcji bazy danych znajduje się na poziomie roboczym — zobacz [BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans), [CommitTrans](../../mfc/reference/cdaoworkspace-class.md#committrans), i [wycofywania](../../mfc/reference/cdaoworkspace-class.md#rollback) funkcji elementów członkowskich klasy `CDaoWorkspace` .  
  
## <a name="odbc-connections"></a>Połączenia ODBC  
 Jest to zalecany sposób pracy z źródła danych ODBC dołączyć tabel zewnętrznych do programu Microsoft Jet (. Baza danych MDB).  
  
## <a name="collections"></a>Kolekcje  
 Każda baza danych zachowuje własną kolekcje tabledef, querydef zestawu rekordów i obiekty w relacji. Klasa `CDaoDatabase` udostępnia funkcje elementów członkowskich do manipulowania tych obiektów.  
  
> [!NOTE]
>  Obiekty są przechowywane w DAO, nie w obiekcie bazy danych MFC. MFC udostępnia klasy tabledef querydef i zestawu rekordów, ale nie dla obiektów relacji.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoDatabase`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
##  <a name="cantransact"></a>CDaoDatabase::CanTransact  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, czy bazy danych umożliwia transakcji.  
  
```  
BOOL CanTransact();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli baza danych obsługuje transakcje; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Transakcje są zarządzane w obszarze roboczym bazy danych.  
  
##  <a name="canupdate"></a>CDaoDatabase::CanUpdate  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, czy `CDaoDatabase` obiektu zezwala na aktualizacje.  
  
```  
BOOL CanUpdate();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli różną od zera `CDaoDatabase` obiektu zezwala na aktualizacje; w przeciwnym razie wartość 0, wskazującą, albo że możesz przekazać **TRUE** w `bReadOnly` przy otwieraniu `CDaoDatabase` obiektu lub że sama baza danych jest tylko do odczytu. Zobacz [Otwórz](#open) funkcję elementu członkowskiego.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać informacje o aktualizacji bazy danych zobacz temat "Nadaje się do aktualizacji właściwości" w pomocy DAO.  
  
##  <a name="cdaodatabase"></a>CDaoDatabase::CDaoDatabase  
 Konstruuje `CDaoDatabase` obiektu.  
  
```  
CDaoDatabase(CDaoWorkspace* pWorkspace = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pWorkspace*  
 Wskaźnik do `CDaoWorkspace` obiektu, który będzie zawierać nowy obiekt bazy danych. Jeśli zaakceptuj wartość domyślną **NULL**, konstruktora tworzy tymczasowy `CDaoWorkspace` obiekt, który używa DAO domyślny obszar roboczy. Można otrzymywać wskaźnik do obiektu obszar roboczy za pomocą [m_pWorkspace](#m_pworkspace) element członkowski danych.  
  
### <a name="remarks"></a>Uwagi  
 Po konstruowania obiektu, jeśli tworzysz nowy Microsoft Jet (. MDB) bazy danych, należy wywołać obiektu [Utwórz](#create) funkcję elementu członkowskiego. Jeśli, zamiast tego otworzyć istniejącą bazę danych, wywołania obiektu [Otwórz](#open) funkcję elementu członkowskiego.  
  
 Po zakończeniu z obiektem, należy wywołać jej [Zamknij](#close) elementu członkowskiego działać, a następnie zniszcz `CDaoDatabase` obiektu.  
  
 Użytkownik może okazać się osadzić `CDaoDatabase` obiektów w klasie dokumentu.  
  
> [!NOTE]
>  A `CDaoDatabase` obiektu tworzona jest również niejawnie po otwarciu [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) obiektu bez przekazywania wskaźnik do istniejącej `CDaoDatabase` obiektu. Ten obiekt bazy danych jest zamknięty podczas zamykania obiektu zestawu rekordów.  
  
##  <a name="close"></a>CDaoDatabase::Close  
 Wywołanie tej funkcji elementu członkowskiego, aby zakończyć połączenie z bazą danych i zamknij wszystkie otwarte zestawy rekordów, tabledefs — i querydefs — skojarzonego z bazą danych.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Uwagi  
 Dobrym rozwiązaniem, aby zamknąć te obiekty samodzielnie przed wywołaniem funkcji członkowskiej jest. Zamykanie `CDaoDatabase` obiektu usuwa go z kolekcji baz danych w skojarzonym [obszaru roboczego](../../mfc/reference/cdaoworkspace-class.md). Ponieważ **Zamknij** nie niszczy `CDaoDatabase` obiektu, obiekt można użyć ponownie otwierając tę samą bazę danych lub innej bazy danych.  
  
> [!CAUTION]
>  Wywołanie [aktualizacji](../../mfc/reference/cdaorecordset-class.md#update) funkcji członkowskiej (jeśli istnieją oczekujące zmiany) i **zamknąć** funkcji członkowskiej na wszystkich obiektach Otwórz zestaw rekordów przed zamknięciem bazy danych. Jeśli zakończysz funkcję, która deklaruje [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) lub `CDaoDatabase` obiektów na stosie, bazy danych jest zamknięty, wszystkie niezapisane zmiany zostaną utracone i wszystkie oczekujące transakcje są wycofywane oraz wszystkie oczekujące edycje, aby dane zostaną utracone.  
  
> [!CAUTION]
>  Jeśli spróbujesz zamknąć obiektu bazy danych, gdy wszystkie obiekty rekordów są otwarte lub Jeśli spróbujesz zamknąć obiekt workspace, gdy wszystkie obiekty bazy danych należące do tego określonego obszaru roboczego są otwarte, te obiekty rekordów zostaną zamknięte, a wszystkie oczekujące aktualizacje lub zmiany będą wycofane. Próba zamknięcia obiektu roboczym, gdy wszystkie obiekty bazy danych należące do niego są otwarte operacji zamyka wszystkie obiekty bazy danych należące do tego obiektu określonego obszaru roboczego, co może spowodować obiektów niezamknięty rekordów jest zamknięty. Jeśli nie zamkniesz obiektu bazy danych, MFC zgłasza błąd potwierdzenia w kompilacjach debugowania.  
  
 Jeśli obiekt bazy danych jest zdefiniowany poza zakresem funkcji i zakończyć konfigurację funkcji bez jego zamknięciem, obiektu bazy danych pozostanie otwarte, dopóki jawnie zamknięty lub moduł, w którym jest zdefiniowany jest poza zakresem.  
  
##  <a name="create"></a>CDaoDatabase::Create  
 Aby utworzyć nowy Microsoft Jet (. MDB) bazy danych, wywołania tej funkcji członkowskiej, po utworzymy `CDaoDatabase` obiektu.  
  
```  
virtual void Create(
    LPCTSTR lpszName,  
    LPCTSTR lpszLocale = dbLangGeneral,  
    int dwOptions = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Wyrażenia ciągu jest nazwa pliku bazy danych, które tworzysz. Jest pełna ścieżka i nazwa pliku, taką jak "C:\\\MYDB. MDB". Należy podać nazwę. Jeśli nie podasz rozszerzenie nazwy pliku. MDB jest dołączany. Jeśli sieć obsługuje jednolitego konwencji nazewnictwa (UNC), można dodawać ścieżkę sieciową, taką jak "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB". Tylko dla programu Microsoft Jet (. Pliki bazy danych MDB) mogą być tworzone przy użyciu funkcji członkowskiej. (Podwójnych odwróconych są wymagane w literałach ciągu, ponieważ "\\" jest znak ucieczki C++.)  
  
 `lpszLocale`  
 Wyrażenia ciągu służy do określania kolejności sortowania do tworzenia bazy danych. Wartość domyślna to **dbLangGeneral**. Możliwe wartości to:  
  
- **dbLangGeneral** angielski, niemiecki, francuski, portugalski, włoski i hiszpański Modern  
  
- **dbLangArabic** arabski  
  
- **dbLangCyrillic** rosyjski  
  
- **dbLangCzech** czeski  
  
- **dbLangDutch** holenderski  
  
- **dbLangGreek** grecki  
  
- **dbLangHebrew** (wersja hebrajska)  
  
- **dbLangHungarian** węgierski  
  
- **dbLangIcelandic** islandzkim  
  
- **dbLangNordic** języki nordyckie (Microsoft Jet aparatu bazy danych wersji 1.0 tylko)  
  
- **dbLangNorwdan** norweski i duński  
  
- **dbLangPolish** Polski  
  
- **dbLangSpanish** hiszpański (tradycyjny)  
  
- **dbLangSwedfin** szwedzki i fiński  
  
- **dbLangTurkish** turecki  
  
 `dwOptions`  
 Liczba całkowita, która określa jedną lub więcej opcji. Możliwe wartości to:  
  
- **dbEncrypt** Utwórz bazę danych zaszyfrowanych.  
  
- **dbVersion10** Utwórz bazę danych z bazy danych programu Microsoft Jet w wersji 1.0.  
  
- **dbVersion11** Utwórz bazę danych z bazy danych programu Microsoft Jet w wersji 1.1.  
  
- **dbVersion20** Utwórz bazę danych z bazy danych programu Microsoft Jet w wersji 2.0.  
  
- **dbVersion30** Utwórz bazę danych z bazy danych programu Microsoft Jet w wersji 3.0.  
  
 W przypadku pominięcia stała szyfrowania, niezaszyfrowane baza danych została utworzona. Można określić tylko jedną wersję stała. Jeśli pominięto stała wersji bazy danych, która używa bazy danych Microsoft Jet w wersji 3.0 zostanie utworzony.  
  
> [!CAUTION]
>  Jeśli bazy danych nie są szyfrowane, jest to możliwe, nawet jeśli implementuje zabezpieczeń użytkownika/hasło, bezpośrednio odczytać plik binarny dysku, który stanowi bazy danych.  
  
### <a name="remarks"></a>Uwagi  
 **Utwórz** tworzy plik bazy danych i podstawowego obiektu bazy danych DAO i inicjuje obiekt C++. Obiekt jest dołączany do kolekcji baz danych obszaru roboczego skojarzone. Obiekt bazy danych jest w stanie otwartym; Nie wywołuj **Otwórz** po **Utwórz**.  
  
> [!NOTE]
>  Z **Utwórz**, można utworzyć tylko Microsoft Jet (. Bazy danych MDB). Nie można utworzyć bazy danych ISAM lub baz danych ODBC.  
  
##  <a name="createrelation"></a>CDaoDatabase::CreateRelation  
 Wywołanie tej funkcji Członkowskich ustanowienie relacji między co najmniej jedno pole w tabeli podstawowej w bazie danych i co najmniej jednego pola w tabeli obcej (innej tabeli w bazie danych).  
  
```  
void CreateRelation(
    LPCTSTR lpszName,  
    LPCTSTR lpszTable,  
    LPCTSTR lpszForeignTable,  
    long lAttributes,  
    LPCTSTR lpszField,  
    LPCTSTR lpszForeignField);  
  
void CreateRelation(CDaoRelationInfo& relinfo);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Unikatowa nazwa obiektu relacji. Nazwa musi rozpoczynać się od litery i może zawierać maksymalnie 40 znaków. Może zawierać cyfry i znaki podkreślenia, ale nie może zawierać znaków interpunkcyjnych i spacji.  
  
 `lpszTable`  
 Nazwa tabeli podstawowej w relacji. Jeśli tabela nie istnieje, MFC zgłasza wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
 `lpszForeignTable`  
 Nazwa tabeli obcego w relacji. Jeśli tabela nie istnieje, MFC zgłasza wyjątek typu `CDaoException`.  
  
 `lAttributes`  
 Długa wartość, która zawiera informacje o typie relacji. Tej wartości można użyć w wymuszaniu integralności referencyjnej, między innymi. Można użyć operatora bitowego OR ( **&#124;**) do łączenia z dowolnej z następujących wartości (o ile kombinacja sens):  
  
- **dbRelationUnique** jest relacja jeden do jednego.  
  
- **dbRelationDontEnforce** relacji nie jest wymuszana (nie integralności referencyjnej).  
  
- **dbRelationInherited** relacja istnieje w bazie danych innych niż bieżące zawiera dwie tabele dołączone.  
  
- **dbRelationUpdateCascade** aktualizacji będzie kaskadowo (Aby uzyskać więcej informacji na temat kaskady, zobacz Uwagi).  
  
- **dbRelationDeleteCascade** kaskadowo zostaną usunięte.  
  
 *lpszField*  
 Wskaźnik do zerem ciąg zawierający nazwę pola w tabeli podstawowej (o nazwie `lpszTable`).  
  
 *lpszForeignField*  
 Wskaźnik do zerem ciąg zawierający nazwę pola w tabeli obcego (o nazwie `lpszForeignTable`).  
  
 *relinfo*  
 Odwołanie do [cdaorelationinfo —](../../mfc/reference/cdaorelationinfo-structure.md) obiekt, który zawiera informacje o relacja, w którym chcesz utworzyć.  
  
### <a name="remarks"></a>Uwagi  
 Relacja nie może dotyczyć zapytanie lub dołączonej tabeli z zewnętrznej bazy danych.  
  
 Gdy relacja obejmuje jedno pole w każdym z dwóch tabel, należy użyć pierwszej wersji funkcji. Druga wersja należy użyć, gdy relacja obejmuje wiele pól. Maksymalna liczba pól w relacji jest 14.  
  
 Ta akcja tworzy obiekt relacji DAO, ale jest to szczegóły implementacji MFC, ponieważ hermetyzacja przez MFC relacji obiektów znajduje się w obrębie klasy `CDaoDatabase`. MFC nie dostarcza klasy relacji.  
  
 Jeśli ustawisz relacji atrybutów obiektu do aktywowania operacji cascade, aparatu bazy danych automatycznie aktualizuje lub usuwa rekordy w co najmniej jednej tabeli, podczas wprowadzania zmian w tabelach pokrewnych klucza podstawowego.  
  
 Na przykład załóżmy, że ustanowić cascade usuwania relacji między tabelami Klienci i zamówienia. Podczas usuwania rekordów z tabeli Klienci, również są usuwane rekordy w tabeli poleceń związanych z tego klienta. Ponadto po nawiązaniu cascade Usuń relacje między tabelą zleceń i inne tabele rekordy z tych tabel zostaną automatycznie usunięte podczas usuwania rekordów z tabeli Klienci.  
  
 Powiązane informacje zobacz temat "CreateRelation Method" w pomocy DAO.  
  
##  <a name="deletequerydef"></a>CDaoDatabase::DeleteQueryDef  
 Wywołanie tej funkcji członkowskich można usunąć określonego querydef — zapisane kwerendy — od `CDaoDatabase` obiektu querydefs — kolekcja.  
  
```  
void DeleteQueryDef(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Nazwa zapisanego zapytania, aby usunąć.  
  
### <a name="remarks"></a>Uwagi  
 Po tej kwerendy jest już zdefiniowana w bazie danych.  
  
 Informacji o tworzeniu querydef obiektów, zobacz klasy [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Obiektu querydef skojarzenie z określonego `CDaoDatabase` obiekt utworzenia `CDaoQueryDef` obiektu przekazaniem go wskaźnik do obiektu bazy danych.  
  
##  <a name="deleterelation"></a>CDaoDatabase::DeleteRelation  
 Wywołanie tej funkcji członka do usunięcia istniejącej relacji z kolekcji Relations obiektu bazy danych.  
  
```  
void DeleteRelation(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Nazwa relacji do usunięcia.  
  
### <a name="remarks"></a>Uwagi  
 Później istnieje już relacja.  
  
 Powiązane informacje zobacz temat "Usuń Method" w pomocy DAO.  
  
##  <a name="deletetabledef"></a>CDaoDatabase::DeleteTableDef  
 Wywołanie tej funkcji członkowskich można usunąć określonej tabeli i wszystkie jej dane z `CDaoDatabase` obiektu tabledefs — kolekcja.  
  
```  
void DeleteTableDef(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Nazwa tabledef do usunięcia.  
  
### <a name="remarks"></a>Uwagi  
 Po tej tabeli nie jest już zdefiniowane w bazie danych.  
  
> [!NOTE]
>  Należy zwrócić szczególną uwagę na nie usunąć tabel systemowych.  
  
 Informacji o tworzeniu tabledef obiektów, zobacz klasy [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md). Obiekt tabledef skojarzenie z określonego `CDaoDatabase` obiekt utworzenia `CDaoTableDef` obiektu przekazaniem go wskaźnik do obiektu bazy danych.  
  
 Powiązane informacje zobacz temat "Usuń Method" w pomocy DAO.  
  
##  <a name="execute"></a>CDaoDatabase::Execute  
 Wywołaj tę funkcję elementu członkowskiego, aby uruchomić kwerendę akcji lub wykonaj instrukcję SQL w bazie danych.  
  
```  
void Execute(
    LPCTSTR lpszSQL,  
    int nOptions = dbFailOnError);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszSQL`  
 Wskaźnik do zerem ciąg zawierający prawidłowe polecenie SQL do wykonania.  
  
 `nOptions`  
 Liczba całkowita, która określa opcje związane z integralności zapytania. Można użyć operatora bitowego OR ( **&#124;**) można użyć dowolnej z następujących stałych (pod warunkiem kombinacja sens — na przykład użytkownik może zrezygnować z łączenia **dbInconsistent** z **dbConsistent**):  
  
- **dbDenyWrite** Odmów uprawnienie zapisu do innych użytkowników.  
  
- **dbInconsistent** niespójne aktualizacje (ustawienie domyślne).  
  
- **dbConsistent** spójne aktualizacji.  
  
- **dbSQLPassThrough** przekazywanego SQL. Powoduje, że instrukcji SQL, które mają być przekazane do źródła danych ODBC do przetwarzania.  
  
- **dbFailOnError** wycofać aktualizacji, jeśli wystąpi błąd.  
  
- **dbSeeChanges** generowanie błędów czasu wykonywania, jeśli inny użytkownik zmienia edytowania danych.  
  
> [!NOTE]
>  Jeśli oba **dbInconsistent** i **dbConsistent** uwzględniono lub jeśli nie będzie uwzględniony, wynikiem jest wartość domyślna. Aby uzyskać informacje o tych stałe zobacz temat "Wykonywanie metody" w pomocy DAO.  
  
### <a name="remarks"></a>Uwagi  
 **Wykonanie** działa tylko w przypadku akcji zapytania lub przekazujący zapytania SQL, które nie zwracają wartości. Nie działa dla zapytań wybierz, które zwraca rekordów.  
  
 Dla definicji i informacji o zapytaniach akcji zobacz tematy "Akcja zapytań" i "Wykonywanie metody" w pomocy DAO.  
  
> [!TIP]
>  Podana poprawna składniowo instrukcji SQL i odpowiednie uprawnienia, **Execute** funkcji członkowskiej nie powiedzie się nawet jeśli nie pojedynczy wiersz można zmodyfikować lub usunąć. W związku z tym należy zawsze używać **dbFailOnError** przy użyciu **Execute** funkcji członkowskiej, aby zaktualizować lub usunąć zapytania. Ta opcja powoduje, że MFC do zgłoszenia wyjątku typu [CDaoException](../../mfc/reference/cdaoexception-class.md) i wycofuje wszystkie zmiany pomyślne żadnego zmodyfikowanych rekordów jest zablokowany i nie można zaktualizować lub usunąć. Należy pamiętać, że zawsze można wywołać `GetRecordsAffected` Aby wyświetlić liczbę rekordów zostały zainfekowane.  
  
 Wywołanie [GetRecordsAffected](#getrecordsaffected) funkcji członkowskiej obiektu bazy danych, aby określić liczbę rekordów wpływ najnowszej **Execute** wywołania. Na przykład `GetRecordsAffected` zwraca informacje na temat liczby rekordów usunięty, zaktualizować lub wstawić podczas wykonywania zapytania akcji. Liczba zwrócił nie zreflektuje zmiany w tabelach pokrewnych, gdy w kaskadowego aktualizuje lub usuwa obowiązują.  
  
 **Wykonanie** nie zwraca zestawu rekordów. Przy użyciu **Execute** na zapytanie wybierające rekordy powoduje, że MFC do zgłoszenia wyjątku typu `CDaoException`. (Brak nie `ExecuteSQL` analogiczne do funkcji członkowskiej `CDatabase::ExecuteSQL`.)  
  
##  <a name="getconnect"></a>CDaoDatabase::GetConnect  
 Wywołanie tej funkcji członkowskich można pobrać ciągu połączenia używanego do łączenia `CDaoDatabase` obiektu do bazy danych ODBC lub ISAM.  
  
```  
CString GetConnect();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Parametrów połączenia, jeśli [Otwórz](#open) została wywołana pomyślnie w źródle danych ODBC; w przeciwnym razie wartość pustego ciągu. Dla programu Microsoft Jet (. Bazy danych MDB), ten ciąg jest zawsze pusta, chyba że zostanie ustawiona do użycia z **dbSQLPassThrough** używana z opcją [Execute](#execute) funkcji członkowskiej lub użyty podczas otwierania zestawu rekordów.  
  
### <a name="remarks"></a>Uwagi  
 Ciąg zawiera informacje o źródle otwartą bazę danych lub bazy danych używanych w zapytaniu przekazujące. Parametry połączenia składa się z specyfikatora typu bazy danych i zero lub więcej parametrów, oddzielając je średnikami.  
  
> [!NOTE]
>  Przy użyciu klas MFC DAO nawiązywania połączenia ze źródłem danych za pośrednictwem ODBC jest mniej wydajne niż nawiązywaniu połączeń za pośrednictwem dołączonej tabeli.  
  
> [!NOTE]
>  Ciąg połączenia jest używany do przekazania dodatkowych informacji do ODBC i sterownikami niektórych ISAM, zgodnie z potrzebami. Nie jest on używany dla. MDB bazy danych. Dla tabel bazowych bazy danych programu Microsoft Jet, ciąg połączenia jest pustym ciągiem ("") z wyjątkiem przypadków, jeśli używasz go w przypadku kwerendy SQL zgodnie z opisem w zwrócić wartość powyżej.  
  
 Zobacz [Otwórz](#open) funkcji członkowskiej opis sposobu tworzenia ciągu połączenia. Po ustawieniu parametrów połączenia **Otwórz** wywołanie, możesz później służy do Sprawdź ustawienie, aby określić typ, ścieżka, identyfikator, hasło lub ODBC źródło danych użytkownika bazy danych.  
  
##  <a name="getname"></a>CDaoDatabase::GetName  
 Wywołanie tej funkcji Członkowskich, aby pobrać nazwę aktualnie otwartej bazy danych, który jest nazwą istniejącego pliku bazy danych lub nazwę zarejestrowanego źródła danych ODBC.  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pełna ścieżka i nazwa pliku bazy danych w przypadku powodzenia; w przeciwnym razie wartość pustą [cstring —](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Uwagi  
 Jeśli sieć obsługuje jednolitego konwencji nazewnictwa (UNC), można również określić ścieżkę sieciową — na przykład "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Podwójnych odwróconych są wymagane w literałach ciągu, ponieważ "\\" jest znak ucieczki C++.)  
  
 Na przykład można wyświetlać tę nazwę w pozycji. Jeśli wystąpi błąd podczas pobierania nazwy, MFC zgłasza wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
> [!NOTE]
>  W celu poprawy wydajności podczas uzyskują dostęp do zewnętrznych baz danych, zaleca się dołączenie tabel zewnętrznych baz danych do bazy danych programu Microsoft Jet (. MDB) zamiast bezpośrednie połączenie ze źródłem danych.  
  
 Typ bazy danych jest określane przez plik lub katalog, który ścieżkę, w następujący sposób:  
  
|Wskazuje nazwy ścieżki.|Typ bazy danych|  
|--------------------------|-------------------|  
|. Plik MDB|Baza danych programu Microsoft Jet (programu Microsoft Access)|  
|Katalog, który zawiera. Pliki DBF|dBASE bazy danych|  
|Katalog, który zawiera. Pliku XLS|Baza danych programu Microsoft Excel|  
|Katalog, który zawiera. Pliki PDX|Aparat|  
|Katalog zawierający pliki bazy danych odpowiednio sformatowanego tekstu|Bazę danych w formacie tekstowym|  
  
 Dla baz danych ODBC, takich jak SQL Server i Oracle ciąg połączenia bazy danych określa nazwę źródła danych (DSN), który jest zarejestrowany przez sterownik ODBC.  
  
##  <a name="getquerydefcount"></a>CDaoDatabase::GetQueryDefCount  
 Wywołanie tej funkcji członkowskich można pobrać liczby zapytań zdefiniowane w bazie danych querydefs — kolekcja.  
  
```  
short GetQueryDefCount();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba zapytań w bazie danych.  
  
### <a name="remarks"></a>Uwagi  
 `GetQueryDefCount`jest przydatne w przypadku wszystkich querydefs — w querydefs — kolekcja pętli. Aby uzyskać informacje dotyczące określonego zapytania w kolekcji, zobacz [GetQueryDefInfo](#getquerydefinfo).  
  
##  <a name="getquerydefinfo"></a>CDaoDatabase::GetQueryDefInfo  
 Wywołanie tej funkcji Członkowskich uzyskać różne rodzaje informacji na temat kwerendy w bazie danych.  
  
```  
void GetQueryDefInfo(
    int nIndex,  
    CDaoQueryDefInfo& querydefinfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

 
void GetQueryDefInfo(
    LPCTSTR lpszName,  
    CDaoQueryDefInfo& querydefinfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks wstępnie zdefiniowanego zapytania w querydefs — kolekcja bazy danych, wyszukiwanie według indeksu.  
  
 *querydefinfo*  
 Odwołanie do [cdaoquerydefinfo —](../../mfc/reference/cdaoquerydefinfo-structure.md) obiekt, który zwraca żądane informacje.  
  
 `dwInfoOptions`  
 Opcje, które określają, które informacje dotyczące rekordów do pobrania. Dostępne opcje są wyświetlane tutaj oraz jakie spowodują one funkcji do zwrócenia o zestaw rekordów:  
  
- `AFX_DAO_PRIMARY_INFO`(Ustawienie domyślne) Nazwa, typ  
  
- `AFX_DAO_SECONDARY_INFO`Informacje o podstawowym plus: utworzono daty, Data ostatniej aktualizacji, zwraca rekordy, aktualizowalne  
  
- `AFX_DAO_ALL_INFO`Głównych i dodatkowych informacji plus: ODBCTimeout SQL, Connect,  
  
 `lpszName`  
 Ciąg zawierający nazwę kwerendy w bazie danych, wyszukiwanie według nazwy.  
  
### <a name="remarks"></a>Uwagi  
 Dwie wersje funkcji są dostarczane, można wybrać zapytanie przez indeks w kolekcji querydefs — bazy danych lub nazwa zapytania.  
  
 Opis informacje zwracane w *querydefinfo*, zobacz [cdaoquerydefinfo —](../../mfc/reference/cdaoquerydefinfo-structure.md) struktury. Ta struktura ma elementów członkowskich, które odpowiadają informacje wymienione powyżej w opisie `dwInfoOptions`. Jeśli użytkownik żąda informacji o jeden poziom, możesz uzyskać wszystkie wcześniejsze poziomy również informacje.  
  
##  <a name="getquerytimeout"></a>CDaoDatabase::GetQueryTimeout  
 Wywołanie tej funkcji Członkowskich pobrać bieżącą liczbę sekund, zanim kolejnych operacji w bazie danych połączonych są upłynął limit czasu.  
  
```  
short GetQueryTimeout();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Krótki całkowitą, zawierający wartość limitu czasu w sekundach.  
  
### <a name="remarks"></a>Uwagi  
 Operacja może przekroczono limit czasu ze względu na problemy z dostępem do sieci, czas przetwarzania zapytania nadmiernego i tak dalej. Ustawienie w czasie działania, ma wpływ na wszystkie otwarte, dodawanie nowych aktualizacji i usuwanie operacji na wszystkie zestawy rekordów skojarzonych z tym `CDaoDatabase` obiektu. Bieżące ustawienie limitu czasu można zmienić, wywołując [SetQueryTimeout](#setquerytimeout). Wartość limitu czasu zapytania dla zestawu rekordów po otwarciu nie zmiana wartości dla zestawu rekordów. Na przykład kolejnych [Przenieś](../../mfc/reference/cdaorecordset-class.md#move) operacje nie należy używać nowej wartości. Wartością domyślną jest ustawiany po zainicjowaniu aparatu bazy danych.  
  
 Wartość domyślna dla przekroczeń limitu czasu zapytania jest pobierana z rejestru systemu Windows. Jeśli nie ma ustawienia rejestru, wartość domyślna to 60 sekund. Nie wszystkie bazy danych obsługują możliwość określenia wartości limitu czasu zapytania. Jeśli ustawisz wartość limitu czasu kwerendy 0 nie przekroczony limit czasu; i komunikacji z bazą danych może przestać odpowiadać. To działanie może być przydatne podczas programowania. Jeśli wystąpi błąd wywołania MFC zgłasza wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
 Powiązane informacje zobacz temat "QueryTimeout Property" w pomocy DAO.  
  
##  <a name="getrecordsaffected"></a>CDaoDatabase::GetRecordsAffected  
 Wywołanie tej funkcji elementu członkowskiego, aby określić liczbę rekordów wpływ najnowszych wywołanie [Execute](#execute) funkcję elementu członkowskiego.  
  
```  
long GetRecordsAffected();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Długich liczb całkowitych zawierające liczbę zmodyfikowanych rekordów.  
  
### <a name="remarks"></a>Uwagi  
 Wartość zwracana obejmuje to liczba rekordów usunięty, zaktualizować lub wstawiane przez uruchomienie z zapytania akcji **Execute**. Liczba zwrócił nie zreflektuje zmiany w tabelach pokrewnych, gdy w kaskadowego aktualizuje lub usuwa obowiązują.  
  
 Powiązane informacje zobacz temat "RecordsAffected Property" w pomocy DAO.  
  
##  <a name="getrelationcount"></a>CDaoDatabase::GetRelationCount  
 Wywołanie tej funkcji elementu członkowskiego w celu uzyskania liczby relacje zdefiniowane między tabelami w bazie danych.  
  
```  
short GetRelationCount();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba relacji zdefiniowanych między tabelami w bazie danych.  
  
### <a name="remarks"></a>Uwagi  
 **GetRelationCount** jest przydatne w przypadku pętli wszystkich relacji zdefiniowanych w kolekcji Relations bazy danych. Aby uzyskać informacje dotyczące danego relacji w kolekcji, zobacz [GetRelationInfo](#getrelationinfo).  
  
 W celu zilustrowania koncepcji relację, należy wziąć pod uwagę tabeli dostawcy i tabeli Produkty, który może mieć relacji jeden do wielu. Ta relacja jeden dostawca może dostarczyć więcej niż jeden produkt. Inne relacje są jeden do jednego lub wiele do wielu.  
  
##  <a name="getrelationinfo"></a>CDaoDatabase::GetRelationInfo  
 Wywołanie tej funkcji Członkowskich, aby uzyskać informacje o określonej relacji w kolekcji Relations bazy danych.  
  
```  
void GetRelationInfo(
    int nIndex,  
    CDaoRelationInfo& relinfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

 
void GetRelationInfo(
    LPCTSTR lpszName,  
    CDaoRelationInfo& relinfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks obiektu relacji w kolekcji Relations bazy danych, wyszukiwanie według indeksu.  
  
 *relinfo*  
 Odwołanie do [cdaorelationinfo —](../../mfc/reference/cdaorelationinfo-structure.md) obiekt, który zwraca żądane informacje.  
  
 `dwInfoOptions`  
 Opcje, które określają, które informacje dotyczące relacji do pobrania. Dostępne opcje są wyświetlane tutaj oraz jakie spowodują one zwracaną o relacja funkcję:  
  
- `AFX_DAO_PRIMARY_INFO`(Ustawienie domyślne) Nazwa tabeli, Tabela obcego  
  
- `AFX_DAO_SECONDARY_INFO`Atrybuty i informacje zawarte w polu  
  
 Informacje pola [cdaorelationfieldinfo —](../../mfc/reference/cdaorelationfieldinfo-structure.md) obiektu zawierającego pola w tabeli podstawowej uczestniczących w relacji.  
  
 `lpszName`  
 Ciąg zawierający nazwę obiektu relacji, wyszukiwanie według nazwy.  
  
### <a name="remarks"></a>Uwagi  
 Dwie wersje tej funkcji dostęp przez indeks lub według nazwy. Opis informacje zwracane w *relinfo*, zobacz [cdaorelationinfo —](../../mfc/reference/cdaorelationinfo-structure.md) struktury. Ta struktura ma elementów członkowskich, które odpowiadają informacje wymienione powyżej w opisie `dwInfoOptions`. Jeśli użytkownik żąda informacji o jeden poziom, również uzyskać informacje o wszelkich poprzednich poziomach.  
  
> [!NOTE]
>  Jeśli ustawisz relacji atrybutów obiektu do aktywowania operacjami kaskadowego ( **dbRelationUpdateCascades** lub **dbRelationDeleteCascades**), aparat bazy danych programu Microsoft Jet automatycznie aktualizuje lub Usuwa rekordy w co najmniej jedną tabelę podczas wprowadzania zmian w tabelach pokrewnych klucza podstawowego. Na przykład załóżmy, że ustanowić cascade usuwania relacji między tabelami Klienci i zamówienia. Podczas usuwania rekordów z tabeli Klienci, również są usuwane rekordy w tabeli poleceń związanych z tego klienta. Ponadto po nawiązaniu cascade Usuń relacje między tabelą zleceń i inne tabele rekordy z tych tabel zostaną automatycznie usunięte podczas usuwania rekordów z tabeli Klienci.  
  
##  <a name="gettabledefcount"></a>CDaoDatabase::GetTableDefCount  
 Wywołanie tej funkcji Członkowskich, aby pobrać liczbę tabel w bazie danych.  
  
```  
short GetTableDefCount();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba tabledefs — w bazie danych.  
  
### <a name="remarks"></a>Uwagi  
 `GetTableDefCount`jest przydatne w przypadku pętli wszystkich tabledefs — w kolekcji tabledefs — bazy danych. Aby uzyskać informacje o danej tabeli w kolekcji, zobacz [GetTableDefInfo](#gettabledefinfo).  
  
##  <a name="gettabledefinfo"></a>CDaoDatabase::GetTableDefInfo  
 Wywołanie tej funkcji Członkowskich uzyskać różne rodzaje informacji o tabeli w bazie danych.  
  
```  
void GetTableDefInfo(
    int nIndex,  
    CDaoTableDefInfo& tabledefinfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

 
void GetTableDefInfo(
    LPCTSTR lpszName,  
    CDaoTableDefInfo& tabledefinfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeks obiektu tabledef w tabledefs — kolekcja bazy danych, wyszukiwanie według indeksu.  
  
 `tabledefinfo`  
 Odwołanie do [cdaotabledefinfo —](../../mfc/reference/cdaotabledefinfo-structure.md) obiekt, który zwraca żądane informacje.  
  
 `dwInfoOptions`  
 Opcje, które określają, które informacje o tabelę, aby pobrać. Dostępne opcje są wyświetlane tutaj oraz jakie spowodują one zwracaną o relacja funkcję:  
  
- `AFX_DAO_PRIMARY_INFO`(Ustawienie domyślne) Nazwa nadaje się do aktualizacji, atrybutów  
  
- `AFX_DAO_SECONDARY_INFO`Informacje o podstawowym plus: utworzono daty, Data ostatniej aktualizacji nazwy tabeli źródłowej, Połącz  
  
- `AFX_DAO_ALL_INFO`Głównych i dodatkowych informacji plus: liczba rekordów reguły sprawdzania poprawności, tekst sprawdzania poprawności  
  
 `lpszName`  
 Nazwa obiektu tabledef wyszukiwania według nazwy.  
  
### <a name="remarks"></a>Uwagi  
 Dwie wersje funkcji są dostarczane, więc możesz wybrać tabelę przez indeks w kolekcji tabledefs — bazy danych lub nazwę tabeli.  
  
 Opis informacje zwracane w `tabledefinfo`, zobacz [cdaotabledefinfo —](../../mfc/reference/cdaotabledefinfo-structure.md) struktury. Ta struktura ma elementów członkowskich, które odpowiadają informacje wymienione powyżej w opisie `dwInfoOptions`. Jeśli użytkownik żąda informacji o jeden poziom, możesz uzyskać informacje o wszelkich poprzednich poziomach.  
  
> [!NOTE]
>  `AFX_DAO_ALL_INFO` Opcja zawiera informacje, które mogą być powolne uzyskać. W takim przypadku zliczanie rekordów w tabeli może być bardzo czasochłonne, jeśli istnieje wiele rekordów.  
  
##  <a name="getversion"></a>CDaoDatabase::GetVersion  
 Wywołanie tej funkcji członkowskich można ustalić wersji pliku bazy danych programu Microsoft Jet.  
  
```  
CString GetVersion();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) wskazujący wersję pliku bazy danych skojarzony z obiektem.  
  
### <a name="remarks"></a>Uwagi  
 Wartość zwracana reprezentuje numer wersji w postaci "major.minor"; na przykład "3.0". Numer wersji produktu (na przykład 3.0) składa się z numerem wersji (3), okres i numer wersji (0). Wersje do daty są 1.0, 1.1, 2.0 i 3.0.  
  
 Powiązane informacje zobacz temat "Właściwość Version" w pomocy DAO.  
  
##  <a name="isopen"></a>CDaoDatabase::IsOpen  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, czy `CDaoDatabase` obiekt jest obecnie otwarty w bazie danych.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli podano niezerowe `CDaoDatabase` obiekt jest obecnie otwarty; w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_pdaodatabase"></a>CDaoDatabase::m_pDAODatabase  
 Zawiera wskaźnik do interfejsu OLE dla podstawowego obiektu bazy danych DAO `CDaoDatabase` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli potrzebujesz dostępu interfejsu DAO bezpośrednio za pomocą tego wskaźnika.  
  
 Informacje o wywołującym DAO bezpośrednio, zobacz [54 Uwaga techniczna](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md).  
  
##  <a name="m_pworkspace"></a>CDaoDatabase::m_pWorkspace  
 Zawiera wskaźnik do [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) obiekt, który zawiera obiekt bazy danych.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli potrzebujesz dostępu do obszaru roboczego bezpośrednio za pomocą tego wskaźnika — na przykład, aby uzyskać wskaźniki do innych obiektów bazy danych w kolekcji baz danych obszaru roboczego.  
  
##  <a name="open"></a>CDaoDatabase::Open  
 Należy wywołać funkcji członkowskiej zainicjować nowo utworzone `CDaoDatabase` obiekt, który reprezentuje istniejącej bazy danych.  
  
```  
virtual void Open(
    LPCTSTR lpszName,  
    BOOL bExclusive = FALSE,  
    BOOL bReadOnly = FALSE,  
    LPCTSTR lpszConnect = _T(""));
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Wyrażeniem, zawierającym nazwę istniejącej Microsoft Jet (. Plik bazy danych MDB). Jeśli nazwa pliku ma rozszerzenie, jest wymagany. Jeśli sieć obsługuje jednolitego konwencji nazewnictwa (UNC), można dodawać ścieżkę sieciową, taką jak "\\\\\\\MYSERVER\\\MYSHARE\\\MYDIR\\\MYDB. MDB". (Podwójnych odwróconych są wymagane w literałach ciągu, ponieważ "\\" jest znak ucieczki C++.)  
  
 Zagadnienia do rozważenia przy użyciu `lpszName`. Jeśli go:  
  
-   Odwołuje się do bazy danych, który jest już otwarty w trybie wyłączności przez innego użytkownika, MFC zgłaszającej wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md). Pułapki ten wyjątek, aby umożliwić użytkownikowi wiedzieć, że baza danych jest niedostępny.  
  
-   To ciąg pusty ("") i *lpszConnect* jest "ODBC;", jest wyświetlane okno dialogowe listę wszystkich zarejestrowanych nazwy źródeł danych ODBC, więc użytkownik może wybrać bazę danych. Należy unikać bezpośredniego połączenia ze źródłami danych ODBC; Zamiast tego użyj dołączonej tabeli.  
  
-   W przeciwnym razie nie odwołuje się do istniejącej bazy danych lub prawidłową nazwę źródła danych ODBC, MFC zgłaszającej wyjątek typu `CDaoException`.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji o kodach błędów DAO Zobacz DAOERR. Plik godz. Aby uzyskać odpowiednie informacje zobacz temat "Przechwytywalny błędami dostępu do danych" w pomocy DAO.  
  
 `bExclusive`  
 Wartość logiczna, która jest **TRUE** Jeśli baza danych ma zostać otwarty w trybie wyłączności (udostępniana) i **FALSE** Jeśli baza danych ma zostać otwarty dla dostępu współdzielonego. Jeśli ten argument zostanie pominięty, bazy danych jest otwarty dla dostępu współdzielonego.  
  
 `bReadOnly`  
 Wartość logiczna, która jest **TRUE** czy ma być otwarta z dostępem tylko do odczytu do bazy danych i **FALSE** Jeśli baza danych ma zostać otwarty do odczytu i zapisu. Jeśli ten argument zostanie pominięty, bazy danych został otwarty do odczytu i zapisu. Wszystkie zależne zestawy rekordów dziedziczą tego atrybutu.  
  
 `lpszConnect`  
 Wyrażenia ciągu używany do otwierania bazy danych. Ten ciąg stanowi ODBC połączyć argumentów. Należy podać argumenty wyłączne i tylko do odczytu do ciągu źródła. Jeśli baza danych jest bazą danych programu Microsoft Jet (. MDB), ten ciąg jest pusty (""). Składnia dla wartości domyślnej — **_t —**("") — zawiera przenośność Unicode, a także ANSI kompilacji aplikacji.  
  
### <a name="remarks"></a>Uwagi  
 **Otwórz** kojarzy bazy danych z obiekt DAO. Nie można użyć obiektu bazy danych, aby utworzyć zestaw rekordów, tabledef lub querydef obiektów do momentu zainicjowania. **Otwórz** dołącza do kolekcji baz danych obszaru roboczego skojarzonego obiektu bazy danych.  
  
 Użyj parametrów w następujący sposób:  
  
-   Podczas otwierania programu Microsoft Jet (. Baza danych MDB), użyj `lpszName` parametru i przekazać pusty ciąg dla `lpszConnect` przebieg ciąg hasła w postaci lub parametr "; PWD = hasło ", jeśli baza danych jest chroniona hasłem (. MDB bazy danych tylko).  
  
-   Podczas otwierania źródła danych ODBC, należy przekazać prawidłowy ciąg połączenia ODBC w `lpszConnect` i pusty ciąg `lpszName`.  
  
 Powiązane informacje zobacz temat "OpenDatabase Method" w pomocy DAO.  
  
> [!NOTE]
>  W celu poprawy wydajności podczas uzyskiwania dostępu do zewnętrznych baz danych, w tym ISAM baz danych i źródła danych ODBC, zaleca się dołączenie tabel zewnętrznych baz danych do bazy danych aparatu Microsoft Jet (. MDB) zamiast bezpośrednie połączenie ze źródłem danych.  
  
 Istnieje możliwość limit czasu nawiązywania połączenia, jeśli na przykład host bazami danych jest niedostępny. Jeśli próba połączenia nie powiedzie się, **Otwórz** zgłasza wyjątek typu [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
 Pozostałe uwagi dotyczą tylko bazy danych ODBC:  
  
 Jeśli baza danych jest bazą danych ODBC i parametrów w Twojej **Otwórz** wywołania nie zawiera wystarczających informacji do nawiązania połączenia, sterownik ODBC otwiera okno dialogowe, aby uzyskać niezbędne informacje od użytkownika. Podczas wywoływania **Otwórz**, ciąg połączenia, `lpszConnect`, są przechowywane przez użytkowników i jest dostępny przez wywołanie metody [GetConnect](#getconnect) funkcję elementu członkowskiego.  
  
 Jeśli chcesz, można otworzyć własne okno dialogowe przed wywołaniem **Otwórz** Aby uzyskać informacje od użytkownika, takie jak hasła, następnie dodać te informacje do przekazania do ciągu połączenia **Otwórz**. Można zapisać parametry połączenia, Przekaż (np. w rejestrze systemu Windows), więc można używać dalej czasu wywołania aplikacji **Otwórz** na `CDaoDatabase` obiektu.  
  
 Umożliwia także parametry połączenia dla różnych poziomów autoryzacji logowania (dla innej `CDaoDatabase` obiektu) lub w celu przedstawienia inne informacje specyficzne dla bazy danych.  
  
##  <a name="setquerytimeout"></a>CDaoDatabase::SetQueryTimeout  
 Wywołanie tej funkcji Członkowskich, aby zastąpić domyślną liczbę sekund, zanim kolejnych operacji na limit czasu połączenia bazy danych.  
  
```  
void SetQueryTimeout(short nSeconds);
```  
  
### <a name="parameters"></a>Parametry  
 `nSeconds`  
 Liczba sekund przed próbą zapytania upłynie limit czasu.  
  
### <a name="remarks"></a>Uwagi  
 Operacja może przekroczono limit czasu ze względu na problemy z dostępem do sieci, czas przetwarzania zapytania nadmiernego i tak dalej. Wywołanie `SetQueryTimeout` przed otwarciem zestawu rekordów lub przed wywołaniem metody w zestawie rekordów [AddNew](../../mfc/reference/cdaorecordset-class.md#addnew), [aktualizacji](../../mfc/reference/cdaorecordset-class.md#update), lub [usunąć](../../mfc/reference/cdaorecordset-class.md#delete) funkcje Członkowskie, jeśli chcesz zmienić zapytania wartość limitu czasu. Ustawienie ma wpływ na wszystkie kolejne [Otwórz](../../mfc/reference/cdaorecordset-class.md#open), `AddNew`, **aktualizacji**, i **usunąć** wywołania żadnych zestawów rekordów skojarzonych z tym `CDaoDatabase` obiektu. Wartość limitu czasu zapytania dla zestawu rekordów po otwarciu nie zmiana wartości dla zestawu rekordów. Na przykład kolejnych [Przenieś](../../mfc/reference/cdaorecordset-class.md#move) operacje nie należy używać nowej wartości.  
  
 Wartością domyślną dla zapytania przekroczeń limitu czasu wynosi 60 sekund. Nie wszystkie bazy danych obsługują możliwość określenia wartości limitu czasu zapytania. Jeśli ustawisz wartość limitu czasu kwerendy 0 nie przekroczony limit czasu; Komunikacja z bazą danych może przestać odpowiadać. To działanie może być przydatne podczas programowania.  
  
 Powiązane informacje zobacz temat "QueryTimeout Property" w pomocy DAO.  
  
## <a name="see-also"></a>Zobacz też  
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)   
 [Cdaorecordset — klasa](../../mfc/reference/cdaorecordset-class.md)   
 [Klasa CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)   
 [Klasa CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)   
 [Cdatabase — klasa](../../mfc/reference/cdatabase-class.md)   
 [Klasa CDaoException](../../mfc/reference/cdaoexception-class.md)
