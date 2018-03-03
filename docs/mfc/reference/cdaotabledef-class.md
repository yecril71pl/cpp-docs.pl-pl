---
title: Klasa CDaoTableDef | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDaoTableDef
- AFXDAO/CDaoTableDef
- AFXDAO/CDaoTableDef::CDaoTableDef
- AFXDAO/CDaoTableDef::Append
- AFXDAO/CDaoTableDef::CanUpdate
- AFXDAO/CDaoTableDef::Close
- AFXDAO/CDaoTableDef::Create
- AFXDAO/CDaoTableDef::CreateField
- AFXDAO/CDaoTableDef::CreateIndex
- AFXDAO/CDaoTableDef::DeleteField
- AFXDAO/CDaoTableDef::DeleteIndex
- AFXDAO/CDaoTableDef::GetAttributes
- AFXDAO/CDaoTableDef::GetConnect
- AFXDAO/CDaoTableDef::GetDateCreated
- AFXDAO/CDaoTableDef::GetDateLastUpdated
- AFXDAO/CDaoTableDef::GetFieldCount
- AFXDAO/CDaoTableDef::GetFieldInfo
- AFXDAO/CDaoTableDef::GetIndexCount
- AFXDAO/CDaoTableDef::GetIndexInfo
- AFXDAO/CDaoTableDef::GetName
- AFXDAO/CDaoTableDef::GetRecordCount
- AFXDAO/CDaoTableDef::GetSourceTableName
- AFXDAO/CDaoTableDef::GetValidationRule
- AFXDAO/CDaoTableDef::GetValidationText
- AFXDAO/CDaoTableDef::IsOpen
- AFXDAO/CDaoTableDef::Open
- AFXDAO/CDaoTableDef::RefreshLink
- AFXDAO/CDaoTableDef::SetAttributes
- AFXDAO/CDaoTableDef::SetConnect
- AFXDAO/CDaoTableDef::SetName
- AFXDAO/CDaoTableDef::SetSourceTableName
- AFXDAO/CDaoTableDef::SetValidationRule
- AFXDAO/CDaoTableDef::SetValidationText
- AFXDAO/CDaoTableDef::m_pDAOTableDef
- AFXDAO/CDaoTableDef::m_pDatabase
dev_langs:
- C++
helpviewer_keywords:
- CDaoTableDef [MFC], CDaoTableDef
- CDaoTableDef [MFC], Append
- CDaoTableDef [MFC], CanUpdate
- CDaoTableDef [MFC], Close
- CDaoTableDef [MFC], Create
- CDaoTableDef [MFC], CreateField
- CDaoTableDef [MFC], CreateIndex
- CDaoTableDef [MFC], DeleteField
- CDaoTableDef [MFC], DeleteIndex
- CDaoTableDef [MFC], GetAttributes
- CDaoTableDef [MFC], GetConnect
- CDaoTableDef [MFC], GetDateCreated
- CDaoTableDef [MFC], GetDateLastUpdated
- CDaoTableDef [MFC], GetFieldCount
- CDaoTableDef [MFC], GetFieldInfo
- CDaoTableDef [MFC], GetIndexCount
- CDaoTableDef [MFC], GetIndexInfo
- CDaoTableDef [MFC], GetName
- CDaoTableDef [MFC], GetRecordCount
- CDaoTableDef [MFC], GetSourceTableName
- CDaoTableDef [MFC], GetValidationRule
- CDaoTableDef [MFC], GetValidationText
- CDaoTableDef [MFC], IsOpen
- CDaoTableDef [MFC], Open
- CDaoTableDef [MFC], RefreshLink
- CDaoTableDef [MFC], SetAttributes
- CDaoTableDef [MFC], SetConnect
- CDaoTableDef [MFC], SetName
- CDaoTableDef [MFC], SetSourceTableName
- CDaoTableDef [MFC], SetValidationRule
- CDaoTableDef [MFC], SetValidationText
- CDaoTableDef [MFC], m_pDAOTableDef
- CDaoTableDef [MFC], m_pDatabase
ms.assetid: 7c5d2254-8475-43c4-8a6c-2d32ead194c9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7b140d61689672f9d27b8078ad7d2eab732c1582
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cdaotabledef-class"></a>Klasa CDaoTableDef
Reprezentuje przechowywanych definicji tabeli podstawowej lub dołączonej tabeli.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDaoTableDef : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDaoTableDef::CDaoTableDef](#cdaotabledef)|Konstruuje **CDaoTableDef** obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDaoTableDef::Append](#append)|Dodaje nową tabelę w bazie danych.|  
|[CDaoTableDef::CanUpdate](#canupdate)|Zwraca wartość niezerową, jeśli można zaktualizować tabeli (można zmodyfikować definicję pola lub właściwości tabeli).|  
|[CDaoTableDef::Close](#close)|Zamyka otwarte tabledef.|  
|[CDaoTableDef::Create](#create)|Tworzy tabelę, której można dodać do bazy danych przy użyciu [Append](#append).|  
|[CDaoTableDef::CreateField](#createfield)|Wywołuje się, by utworzyć pola tabeli.|  
|[CDaoTableDef::CreateIndex](#createindex)|Wywołuje się, by utworzyć indeks dla tabeli.|  
|[CDaoTableDef::DeleteField](#deletefield)|Wywołuje się, by usunąć pola z tabeli.|  
|[CDaoTableDef::DeleteIndex](#deleteindex)|Wywołuje się, by usunąć indeksu z tabeli.|  
|[CDaoTableDef::GetAttributes](#getattributes)|Zwraca wartość wskazującą, jeden lub więcej właściwości `CDaoTableDef` obiektu.|  
|[CDaoTableDef::GetConnect](#getconnect)|Zwraca wartość, która zawiera informacje o źródle tabeli.|  
|[CDaoTableDef::GetDateCreated](#getdatecreated)|Zwraca datę i godzinę, w tabeli podstawowej odpowiadającego `CDaoTableDef` obiekt został utworzony.|  
|[CDaoTableDef::GetDateLastUpdated](#getdatelastupdated)|Zwraca datę i godzinę ostatniej zmiany wprowadzone w projekcie tabeli podstawowej.|  
|[CDaoTableDef::GetFieldCount](#getfieldcount)|Zwraca wartość reprezentującą liczbę pól w tabeli.|  
|[CDaoTableDef::GetFieldInfo](#getfieldinfo)|Zwraca określonych rodzajów informacji o polach w tabeli.|  
|[CDaoTableDef::GetIndexCount](#getindexcount)|Zwraca liczbę indeksów dla tabeli.|  
|[CDaoTableDef::GetIndexInfo](#getindexinfo)|Zwraca określonych rodzajów informacji na temat indeksów dla tabeli.|  
|[CDaoTableDef::GetName](#getname)|Zwraca nazwę użytkownika w tabeli.|  
|[CDaoTableDef::GetRecordCount](#getrecordcount)|Zwraca liczbę rekordów w tabeli.|  
|[CDaoTableDef::GetSourceTableName](#getsourcetablename)|Zwraca wartość, która określa nazwę dołączonej tabeli źródłowej bazy danych.|  
|[CDaoTableDef::GetValidationRule](#getvalidationrule)|Zwraca wartość, która weryfikuje dane w polu, ponieważ jest zmienione lub dodane do tabeli.|  
|[CDaoTableDef::GetValidationText](#getvalidationtext)|Zwraca wartość, która określa tekst wiadomości, które będą wyświetlane w aplikacji, jeśli wartość obiektu pola nie spełnia określona reguła walidacji.|  
|[CDaoTableDef::IsOpen](#isopen)|Zwraca wartość niezerową, jeśli tabela jest Otwórz.|  
|[CDaoTableDef::Open](#open)|Otwiera istniejący tabledef przechowywane w bazie danych użytkownika TableDef w kolekcji.|  
|[CDaoTableDef::RefreshLink](#refreshlink)|Aktualizuje informacje o połączeniu dla dołączonej tabeli.|  
|[CDaoTableDef::SetAttributes](#setattributes)|Ustawia wartość wskazującą, jeden lub więcej właściwości `CDaoTableDef` obiektu.|  
|[CDaoTableDef::SetConnect](#setconnect)|Ustawia wartość, która zawiera informacje o źródle tabeli.|  
|[CDaoTableDef::SetName](#setname)|Ustawia nazwę tabeli.|  
|[CDaoTableDef::SetSourceTableName](#setsourcetablename)|Ustawia wartość, która określa nazwę dołączonej tabeli źródłowej bazy danych.|  
|[CDaoTableDef::SetValidationRule](#setvalidationrule)|Ustawia wartość, która weryfikuje dane w polu, ponieważ jest zmienione lub dodane do tabeli.|  
|[CDaoTableDef::SetValidationText](#setvalidationtext)|Ustawia wartość, która określa tekst wiadomości, które będą wyświetlane w aplikacji, jeśli wartość obiektu pola nie spełnia określona reguła walidacji.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDaoTableDef::m_pDAOTableDef](#m_pdaotabledef)|Wskaźnik do interfejsu DAO tabledef obiektu źródłowego.|  
|[CDaoTableDef::m_pDatabase](#m_pdatabase)|Źródłowej bazy danych dla tej tabeli.|  
  
## <a name="remarks"></a>Uwagi  
 Każdy obiekt bazy danych DAO przechowuje kolekcję o nazwie tabledefs —, który zawiera wszystkie zapisane obiektów DAO tabledef.  
  
 Manipulować definicji tabeli za pomocą `CDaoTableDef` obiektu. Możesz na przykład:  
  
-   Sprawdź, czy pole i indeksu struktury dowolnej tabeli w bazie danych lokalnych, dołączone lub zewnętrznego.  
  
-   Wywołanie `SetConnect` i `SetSourceTableName` funkcje Członkowskie dla tabel dołączonych i użyj `RefreshLink` funkcji członkowskiej zaktualizować połączeń, aby dołączyć tabel.  
  
-   Wywołanie `CanUpdate` funkcji członkowskiej, aby określić, czy można edytować definicji pola w tabeli.  
  
-   Pobrać lub ustawić warunki weryfikacji przy użyciu `GetValidationRule` i `SetValidationRule`i `GetValidationText` i `SetValidationText` funkcji elementów członkowskich.  
  
-   Użyj **Otwórz** funkcji członkowskiej do utworzenia tabeli, dynamiczny lub typu migawka `CDaoRecordset` obiektu.  
  
    > [!NOTE]
    >  Klasy baz danych DAO różnią się od klasy baz danych MFC oparte na otwarte połączenie bazy danych (ODBC). Wszystkie nazwy klasy bazy danych DAO mają prefiks "CDao". Możesz nadal dostęp do źródła danych ODBC z klasy DAO; klasy DAO zazwyczaj oferują możliwości wyższego poziomu, ponieważ zależą one od aparatu bazy danych programu Microsoft Jet.  
  
### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>Aby użyć obiektów tabledef do pracy z istniejącej tabeli lub Utwórz nową tabelę  
  
1.  We wszystkich przypadkach, należy najpierw utworzyć `CDaoTableDef` obiektu, podając wskaźnik do [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiekt, do której należy tabeli.  
  
2.  Następnie wykonaj następujące czynności, w zależności od tego, co chcesz:  
  
    -   Aby korzystać z istniejącego zapisanego tabeli, należy wywołać obiektu tabledef [Otwórz](#open) funkcji członkowskiej, podając nazwę zapisanego tabeli.  
  
    -   Aby utworzyć nową tabelę, należy wywołać obiekt tabledef [Utwórz](#create) funkcji członkowskiej, podając nazwę tabeli. Wywołanie [CreateField](#createfield) i [CreateIndex](#createindex) można dodać pól i indeksów do tabeli.  
  
    -   Wywołanie [Append](#append) można zapisać tabeli przez dodanie go do bazy danych tabledefs — kolekcja. **Utwórz** umieszcza tabledef w stanie otwartym, tak po wywołaniu **Utwórz** Nie wywołuj **Otwórz**.  
  
        > [!TIP]
        >  Najprostszym sposobem tworzenia tabel zapisany jest je utworzyć i zapisać je w bazie danych przy użyciu programu Microsoft Access. Następnie możesz otworzyć i używać ich w kodzie MFC.  
  
 Aby użyć obiektu tabledef otwarciu lub utworzone, Utwórz i Otwórz `CDaoRecordset` obiekt określający nazwę tabledef z **dbOpenTable** wartość w `nOpenType` parametru.  
  
 Aby utworzyć za pomocą obiektu tabledef `CDaoRecordset` obiektu, należy zwykle Utwórz lub Otwórz tabledef zgodnie z powyższym opisem, a następnie skonstruować obiektu zestawu rekordów, przekazanie wskaźnika do obiektu tabledef podczas wywoływania [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open). Tabledef, które przekazujesz musi być w stanie otwartym. Aby uzyskać więcej informacji, zobacz klasy [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md).  
  
 Po zakończeniu przy użyciu obiektu tabledef wywołać jej [Zamknij](../../mfc/reference/cdaorecordset-class.md#close) element członkowski funkcji; następnie zniszcz obiektu tabledef.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoTableDef`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
##  <a name="append"></a>CDaoTableDef::Append  
 Wywołanie funkcji członkowskiej po wywołaniu metody [Utwórz](#create) można utworzyć nowego obiektu tabledef, aby zapisać tabledef w bazie danych.  
  
```  
virtual void Append();
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja dołącza obiektu do bazy danych tabledefs — kolekcja. Podczas określania go nie dołączając ją służy tabledef jako tymczasowy obiekt, ale jeśli chcesz zapisać i używać go, należy wywołać **Append**.  
  
> [!NOTE]
>  Próba dołączenia tabledef bez nazwy (wartość null lub pusty ciąg zawierający) MFC zgłasza wyjątek.  
  
 Powiązane informacje zobacz temat "Dołącz Method" w pomocy DAO.  
  
##  <a name="canupdate"></a>CDaoTableDef::CanUpdate  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, czy definicja tabeli podstawowych `CDaoTableDef` obiektu można zmieniać.  
  
```  
BOOL CanUpdate();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli można zmodyfikować struktury tabeli (schemat) (Dodaj lub Usuń indeksy i pola), w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie źródłowego nowo utworzonej tabeli `CDaoTableDef` obiekt może być aktualizowany i dołączonej tabeli podstawowej `CDaoTableDef` nie można zaktualizować obiektu. A `CDaoTableDef` obiekt może być nadaje się do aktualizacji, nawet jeśli nie nadaje Wynikowy zestaw rekordów.  
  
 Powiązane informacje zobacz temat "Nadaje się do aktualizacji właściwości" w pomocy DAO.  
  
##  <a name="cdaotabledef"></a>CDaoTableDef::CDaoTableDef  
 Konstruuje **CDaoTableDef** obiektu.  
  
```  
CDaoTableDef(CDaoDatabase* pDatabase);
```  
  
### <a name="parameters"></a>Parametry  
 `pDatabase`  
 Wskaźnik do [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Po konstruowania obiektu, należy wywołać [Utwórz](#create) lub [Otwórz](#open) funkcję elementu członkowskiego. Po zakończeniu z obiektem, należy wywołać jej [Zamknij](#close) element członkowski funkcji i zniszcz `CDaoTableDef` obiektu.  
  
##  <a name="close"></a>CDaoTableDef::Close  
 Wywołanie tej funkcji Członkowskich, zamknij i wersji obiektu tabledef.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwykle po wywołaniu **Zamknij**, Usuń obiekt tabledef, jeśli został przydzielony z **nowe**.  
  
 Możesz wywołać [Otwórz](#open) ponownie po wywołaniu **Zamknij**. Dzięki temu można użyć ponownie obiektu tabledef.  
  
 Powiązane informacje zobacz temat "Metody Close" w pomocy DAO.  
  
##  <a name="create"></a>CDaoTableDef::Create  
 Wywołanie tej funkcji Członkowskich, aby utworzyć nową tabelę zapisane.  
  
```  
virtual void Create(
    LPCTSTR lpszName,  
    long lAttributes = 0,  
    LPCTSTR lpszSrcTable = NULL,  
    LPCTSTR lpszConnect = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Wskaźnik do ciąg zawierający nazwę tabeli.  
  
 `lAttributes`  
 Wartość odpowiadającą właściwości reprezentowanych przez obiekt tabledef tabeli. Można użyć wartości bitowe lub można użyć dowolnej z następujących stałych:  
  
|Stała|Opis|  
|--------------|-----------------|  
|**dbAttachExclusive**|W przypadku baz danych, które używają aparatu bazy danych programu Microsoft Jet wskazuje, że tabela jest otwarta w trybie wyłączności dołączonej tabeli.|  
|**dbAttachSavePWD**|W przypadku baz danych, które używają aparatu bazy danych programu Microsoft Jet wskazuje identyfikator użytkownika i hasło dla dołączonej tabeli są zapisywane z informacjami o połączeniu.|  
|**dbSystemObject**|Wskazuje, że tabela jest tabelą systemową dostarczone przez aparat bazy danych programu Microsoft Jet.|  
|**dbHiddenObject**|Wskazuje, że tabela jest ukryta tabeli dostarczone przez aparat bazy danych programu Microsoft Jet.|  
  
 *lpszSrcTable*  
 Wskaźnik do ciąg zawierający nazwy tabeli źródłowej. Domyślnie ta wartość zostanie zainicjowany jako **NULL**.  
  
 `lpszConnect`  
 Wskaźnik do ciąg zawierający domyślne parametry połączenia. Domyślnie ta wartość zostanie zainicjowany jako **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Gdy ma nazwanych tabledef, można wywołać [Append](#append) do zapisania w bazie danych tabledefs — kolekcja tabledef. Po wywołaniu **Append**tabledef jest w stanie otwartym i służy do tworzenia [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) obiektu.  
  
 Powiązane informacje zobacz temat "CreateTableDef Method" w pomocy DAO.  
  
##  <a name="createfield"></a>CDaoTableDef::CreateField  
 Wywołanie tej funkcji Członkowskich, aby dodać pole do tabeli.  
  
```  
void CreateField(
    LPCTSTR lpszName,  
    short nType,  
    long lSize,  
    long lAttributes = 0);  
  
void CreateField(CDaoFieldInfo& fieldinfo);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Wskaźnik do wyrażenia ciąg określający nazwę tego pola.  
  
 `nType`  
 Wartość wskazująca typ danych pola. Ustawienie może być jedną z następujących wartości:  
  
|Typ|Rozmiar (w bajtach)|Opis|  
|----------|--------------------|-----------------|  
|**dbBoolean**|1 bajt|WARTOŚĆ LOGICZNA|  
|**dbByte**|1|BYTE|  
|**dbInteger**|2|int|  
|**dbLong**|4|long|  
|**dbCurrency**|8|Currency ( [COleCurrency](../../mfc/reference/colecurrency-class.md))|  
|**dbSingle**|4|float|  
|**dbDouble**|8|double|  
|**dbDate**|8|Data/Godzina ( [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|  
|**dbText**|1 - 255|Tekst ( [cstring —](../../atl-mfc-shared/reference/cstringt-class.md))|  
|**dbLongBinary**|0|Długie pliku binarnego (obiekt OLE), [clongbinary —](../../mfc/reference/clongbinary-class.md) lub [CByteArray](../../mfc/reference/cbytearray-class.md)|  
|**dbMemo**|0|Memo ( [cstring —](../../atl-mfc-shared/reference/cstringt-class.md))|  
  
 `lSize`  
 Wartość, która określa maksymalny rozmiar w bajtach pola zawierającej tekst, czy stały rozmiar pola, który zawiera wartości tekstowe lub liczbowe. `lSize` Parametr jest ignorowany dla wszystkich pól tekstowych.  
  
 `lAttributes`  
 Wartość odpowiadającą właściwości pola i które można łączyć, używając logiczną lub.  
  
|Stała|Opis|  
|--------------|-----------------|  
|**dbFixedField**|Rozmiar pola jest stała (domyślnie dla pól liczbowych).|  
|**dbVariableField**|Rozmiar pola jest zmienną (tylko pola tekstowe).|  
|**dbAutoIncrField**|Wartość pola dla nowych rekordów, automatycznie zostaje zwiększona do unikatowy długich liczb całkowitych, nie można jej zmienić. Obsługiwane tylko dla tabel bazy danych programu Microsoft Jet.|  
|**dbUpdatableField**|Można zmienić wartość pola.|  
|**dbDescending**|Pola są posortowane w malejącej (Z - A lub 100-0) zamówienia (dotyczy tylko pola obiektu w kolekcji pól obiektu indeks). W przypadku pominięcia tego stała, pole są posortowane w kolejności rosnącej (A - Z lub 0 - 100) zamówienia (ustawienie domyślne).|  
  
 `fieldinfo`  
 Odwołanie do [cdaofieldinfo —](../../mfc/reference/cdaofieldinfo-structure.md) struktury.  
  
### <a name="remarks"></a>Uwagi  
 A **DAOField** (OLE) obiekt został utworzony i dołączane do kolekcji pól **DAOTableDef** obiektu (OLE). Oprócz obsługi badania właściwości obiektu, można również użyć `CDaoFieldInfo` do utworzenia przy tworzeniu nowych pól w tabledef parametru wejściowego. Pierwszej wersji `CreateField` jest łatwiejsze do użycia, ale jeśli chcesz bardziej precyzyjną kontrolę, można użyć druga wersja `CreateField`, który bierze `CDaoFieldInfo` parametru.  
  
 Jeśli używasz wersji `CreateField` pobierającej `CDaoFieldInfo` parametru, należy starannie ustawić każdego z następujących członków `CDaoFieldInfo` struktury:  
  
- **m_strName**  
  
- `m_nType`  
  
- **m_lSize**  
  
- **m_lAttributes**  
  
- **m_bAllowZeroLength**  
  
 Pozostałe elementy członkowskie z `CDaoFieldInfo` powinien być ustawiony na **0**, **FALSE**, lub pusty ciąg, odpowiednio do elementu członkowskiego, lub `CDaoException` mogą wystąpić.  
  
 Powiązane informacje zobacz temat "CreateField Method" w pomocy DAO.  
  
##  <a name="createindex"></a>CDaoTableDef::CreateIndex  
 Wywołanie tej funkcji można dodać do tabeli indeks.  
  
```  
void CreateIndex(CDaoIndexInfo& indexinfo);
```  
  
### <a name="parameters"></a>Parametry  
 `indexinfo`  
 Odwołanie do [cdaoindexinfo —](../../mfc/reference/cdaoindexinfo-structure.md) struktury.  
  
### <a name="remarks"></a>Uwagi  
 Indeksy określić kolejność rekordów dostępne z tabel bazy danych i czy zduplikowane rekordy są akceptowane. Indeksy udostępniają wydajny dostęp do danych.  
  
 Nie trzeba utworzyć indeksy tabel, ale w tabelach z dużych, nieindeksowanych, dostęp do określonego rekordu lub tworzenie zestawu rekordów może zająć dużo czasu. Z drugiej strony, spowalnia tworzenie indeksów zbyt wiele aktualizacji, Dołącz, a następnie usunąć operacji wszystkie indeksy są automatycznie aktualizowane. Te czynniki wziąć pod uwagę zdecydujesz indeksów, które można utworzyć.  
  
 Następujące elementy członkowskie z `CDaoIndexInfo` struktury musi być ustawiona:  
  
- **m_strName** należy podać nazwę.  
  
- `m_pFieldInfos`Tablica musi wskazywać `CDaoIndexFieldInfo` struktury.  
  
- `m_nFields`Musisz określić liczbę pól w tablicy `CDaoFieldInfo` struktury.  
  
 Pozostałe elementy członkowskie zostaną zignorowane w przypadku ustawione na **FALSE**. Ponadto **m_lDistinctCount** elementu członkowskiego jest ignorowany podczas tworzenia indeksu.  
  
##  <a name="deletefield"></a>CDaoTableDef::DeleteField  
 Wywołanie tej funkcji Członkowskich, aby usunąć pole i stał się niedostępny.  
  
```  
void DeleteField(LPCTSTR lpszName);  
void DeleteField(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Wskaźnik do wyrażenia jest nazwą istniejącego pola tekstowego.  
  
 `nIndex`  
 Indeks pola w tabeli liczony od zera kolekcji pól, wyszukiwanie według indeksu.  
  
### <a name="remarks"></a>Uwagi  
 Możesz użyć tej funkcji Członkowskich w nowy obiekt, który ma ono dołączane do bazy danych lub gdy [CanUpdate](#canupdate) zwraca różną od zera.  
  
 Powiązane informacje zobacz temat "Usuń Method" w pomocy DAO.  
  
##  <a name="deleteindex"></a>CDaoTableDef::DeleteIndex  
 Wywołanie tej funkcji członkowskich można usunąć indeksu w tabeli podstawowej.  
  
```  
void DeleteIndex(LPCTSTR lpszName);  
void DeleteIndex(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Wskaźnik do wyrażeniem, zawierającym nazwę istniejącego indeksu.  
  
 `nIndex`  
 Indeks tablicy obiektu indeksu w bazy danych liczony od zera tabledefs — kolekcja, wyszukiwanie według indeksu.  
  
### <a name="remarks"></a>Uwagi  
 Możesz użyć tej funkcji Członkowskich w nowy obiekt, który nie został dodany do bazy danych lub gdy [CanUpdate](#canupdate) zwraca różną od zera.  
  
 Powiązane informacje zobacz temat "Usuń Method" w pomocy DAO.  
  
##  <a name="getattributes"></a>CDaoTableDef::GetAttributes  
 Dla `CDaoTableDef` obiektu, zwracana wartość określa charakterystykę tabeli reprezentowany przez `CDaoTableDef` obiektu i może być sumę te stałe:  
  
```  
long GetAttributes();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość wskazującą, jeden lub więcej właściwości `CDaoTableDef` obiektu.  
  
### <a name="remarks"></a>Uwagi  
  
|Stała|Opis|  
|--------------|-----------------|  
|**dbAttachExclusive**|W przypadku baz danych, które używają aparatu bazy danych programu Microsoft Jet wskazuje, że tabela jest otwarta w trybie wyłączności dołączonej tabeli.|  
|**dbAttachSavePWD**|W przypadku baz danych, które używają aparatu bazy danych programu Microsoft Jet wskazuje identyfikator użytkownika i hasło dla dołączonej tabeli są zapisywane z informacjami o połączeniu.|  
|**dbSystemObject**|Wskazuje, że tabela jest tabelą systemową dostarczone przez aparat bazy danych programu Microsoft Jet.|  
|**dbHiddenObject**|Wskazuje, że tabela jest ukryta tabeli dostarczone przez aparat bazy danych programu Microsoft Jet.|  
|**dbAttachedTable**|Wskazuje, że jest dołączona tabela z bazy danych z systemem innym niż ODBC, takich jak Paradox bazy danych.|  
|**dbAttachedODBC**|Wskazuje, że jest dołączona tabela z bazy danych ODBC, takich jak Microsoft SQL Server.|  
  
 Tabela systemowa jest tworzony przez aparat bazy danych programu Microsoft Jet zawiera różne informacje wewnętrznej tabeli.  
  
 Ukryte tabeli znajduje się tabela utworzona tymczasowego używana przez aparat bazy danych programu Microsoft Jet.  
  
 Powiązane informacje zobacz temat "Właściwość Attributes" w pomocy DAO.  
  
##  <a name="getconnect"></a>CDaoTableDef::GetConnect  
 Wywołanie tej funkcji Członkowskich uzyskać ciąg połączenia dla źródła danych.  
  
```  
CString GetConnect();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CString` obiekt zawierający typ ścieżki i bazy danych dla tabeli.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać `CDaoTableDef` obiekt, który reprezentuje dołączonej tabeli `CString` obiekt składa się z co najmniej dwa elementy (specyfikatora typu bazy danych i ścieżka do bazy danych).  
  
 Ścieżka, jak pokazano w poniższej tabeli pełną ścieżkę do katalogu zawierającego pliki bazy danych i musi być poprzedzony przez identyfikator "bazy danych =". W niektórych przypadkach (zgodnie z bazy danych programu Microsoft Excel i Microsoft Jet) określonej nazwy pliku jest uwzględniona w argumencie ścieżki bazy danych.  
  
 Tabela w [CDaoTableDef::SetConnect](#setconnect) zawiera typy możliwe bazy danych oraz ich odpowiednich specyfikatory bazy danych i ścieżki:  
  
 Dla tabel bazowych bazy danych programu Microsoft Jet, specyfikator jest pustym ciągiem ("").  
  
 Jeśli hasło jest wymagana, ale nie podano, sterownik ODBC wyświetla logowania oknie dialogowym po raz pierwszy uzyskać dostępu do tabeli i ponownie, jeśli połączenie jest zamknięte i otwarte ponownie. Jeśli ma dołączonej tabeli **dbAttachSavePWD** atrybutu, monit logowania nie pojawi się po otwarciu tabeli.  
  
 Powiązane informacje zobacz temat "Połącz Property" w pomocy DAO.  
  
##  <a name="getdatecreated"></a>CDaoTableDef::GetDateCreated  
 Wywołanie tej funkcji, aby określić datę i godzinę, tabela podstawowa `CDaoTableDef` obiekt został utworzony.  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość zawierającą datę i godzinę utworzenia tabeli podstawowych `CDaoTableDef` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ustawienia daty i godziny są uzyskiwane z komputera, na którym utworzenia lub ostatniej aktualizacji tabeli podstawowej. W środowisku wielodostępnym użytkowników należy uzyskać te ustawienia bezpośrednio z serwera plików, aby uniknąć niezgodności; oznacza to, że wszystkie klienci powinni używać źródła "standardowy" czas — na przykład od jednego serwera.  
  
 Powiązane informacje zobacz temat "DateCreated właściwości LastUpdated" w pomocy DAO.  
  
##  <a name="getdatelastupdated"></a>CDaoTableDef::GetDateLastUpdated  
 Wywołanie tej funkcji, aby określić datę i godzinę, tabela podstawowa **CDaoTableDef** ostatniej aktualizacji obiektu.  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość, która zawiera daty i godziny tabeli odpowiadającego **CDaoTableDef** ostatniej aktualizacji obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ustawienia daty i godziny są uzyskiwane z komputera, na którym utworzenia lub ostatniej aktualizacji tabeli podstawowej. W środowisku wielodostępnym użytkowników należy uzyskać te ustawienia bezpośrednio z serwera plików, aby uniknąć niezgodności; oznacza to, że wszystkie klienci powinni używać źródła "standardowy" czas — na przykład od jednego serwera.  
  
 Powiązane informacje zobacz temat "DateCreated właściwości LastUpdated" w pomocy DAO.  
  
##  <a name="getfieldcount"></a>CDaoTableDef::GetFieldCount  
 Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę pola zdefiniowane w tabeli.  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba pól w tabeli.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli jego wartość wynosi 0, nie ma żadnych obiektów w kolekcji.  
  
 Powiązane informacje zobacz temat "Właściwość Count" w pomocy DAO.  
  
##  <a name="getfieldinfo"></a>CDaoTableDef::GetFieldInfo  
 Wywołanie tej funkcji Członkowskich uzyskać różne rodzaje informacji na temat pola zdefiniowane w tabledef.  
  
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
 Indeks obiektu pola w tabeli liczony od zera kolekcji pól, wyszukiwanie według indeksu.  
  
 `fieldinfo`  
 Odwołanie do [cdaofieldinfo —](../../mfc/reference/cdaofieldinfo-structure.md) struktury.  
  
 `dwInfoOptions`  
 Opcje, które określają, które informacje o polu do pobrania. Dostępne opcje są wyświetlane tutaj wraz z co spowodują one funkcja zwracająca:  
  
- `AFX_DAO_PRIMARY_INFO`(Ustawienie domyślne) Nazwa, typ, rozmiar, atrybuty. Użyj tej opcji dla największą wydajność.  
  
- `AFX_DAO_SECONDARY_INFO`Podstawowe informacje plus: numer pozycji, wymagane, Zezwalaj tabeli źródłowej zerowej długości, kolejność sortowania, obcego Nazwa pola źródła  
  
- `AFX_DAO_ALL_INFO`Informacje o podstawowych i pomocniczych plus: wartość domyślna reguła sprawdzania poprawności, tekst sprawdzania poprawności  
  
 `lpszName`  
 Wskaźnik na nazwę obiektu pole wyszukiwania według nazwy. Nazwa jest ciągiem o długości maksymalnie 64 znaków unikatowej nazwy pola.  
  
### <a name="remarks"></a>Uwagi  
 Jedna wersja funkcji umożliwia pole wyszukiwania według indeksu. Druga wersja umożliwia wyszukiwania według nazwy pola.  
  
 Aby uzyskać opis zwracanych informacji, zobacz [cdaofieldinfo —](../../mfc/reference/cdaofieldinfo-structure.md) struktury. Ta struktura ma elementów członkowskich, które odpowiadają informacje wymienione powyżej w opisie `dwInfoOptions`. Gdy użytkownik żąda informacji o jeden poziom, można pobrać informacji o żadnych poprzednich poziomach.  
  
 Powiązane informacje zobacz temat "Właściwość Attributes" w pomocy DAO.  
  
##  <a name="getindexcount"></a>CDaoTableDef::GetIndexCount  
 Wywołanie tej funkcji Członkowskich uzyskanie liczba indeksów dla tabeli.  
  
```  
short GetIndexCount();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba indeksów dla tabeli.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli jego wartość wynosi 0, brak jest indeksów w kolekcji.  
  
 Powiązane informacje zobacz temat "Właściwość Count" w pomocy DAO.  
  
##  <a name="getindexinfo"></a>CDaoTableDef::GetIndexInfo  
 Wywołanie tej funkcji Członkowskich uzyskać różne rodzaje informacji o zdefiniowanych w tabledef indeksu.  
  
```  
void GetIndexInfo(
    int nIndex,  
    CDaoIndexInfo& indexinfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

 
void GetIndexInfo(
    LPCTSTR lpszName,  
    CDaoIndexInfo& indexinfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Indeksu liczbowego obiektu indeksu w tabeli liczony od zera indeksów kolekcji, wyszukiwanie za pomocą jego pozycji w kolekcji.  
  
 `indexinfo`  
 Odwołanie do [cdaoindexinfo —](../../mfc/reference/cdaoindexinfo-structure.md) struktury.  
  
 `dwInfoOptions`  
 Opcje, które określają, które informacje o indeksie do pobrania. Dostępne opcje są wyświetlane tutaj wraz z co spowodują one funkcja zwracająca:  
  
- `AFX_DAO_PRIMARY_INFO`Nazwa pola Info, pola. Użyj tej opcji dla największą wydajność.  
  
- `AFX_DAO_SECONDARY_INFO`Podstawowe informacje plus: podstawowej, Unique, klastra, Ignoruj wartości null, wymagane, obcy  
  
- `AFX_DAO_ALL_INFO`Informacje o podstawowych i pomocniczych plus: liczności unikatowych wartości  
  
 `lpszName`  
 Wskaźnik na nazwę obiektu indeksu wyszukiwania według nazwy.  
  
### <a name="remarks"></a>Uwagi  
 Jedna wersja funkcji umożliwia wyszukiwanie indeksu za pomocą jego pozycji w kolekcji. Druga wersja pozwala indeksu wyszukiwania według nazwy.  
  
 Aby uzyskać opis zwracanych informacji, zobacz [cdaoindexinfo —](../../mfc/reference/cdaoindexinfo-structure.md) struktury. Ta struktura ma elementów członkowskich, które odpowiadają informacje wymienione powyżej w opisie `dwInfoOptions`. Gdy użytkownik żąda informacji o jeden poziom, można pobrać informacji o żadnych poprzednich poziomach.  
  
 Powiązane informacje zobacz temat "Właściwość Attributes" w pomocy DAO.  
  
##  <a name="getname"></a>CDaoTableDef::GetName  
 Wywołanie tej funkcji członkowskich można uzyskać nazwy użytkownika w tabeli podstawowej.  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zdefiniowane przez użytkownika nazwę tabeli.  
  
### <a name="remarks"></a>Uwagi  
 Ta nazwa rozpoczyna się od litery i może zawierać maksymalnie 64 znaki. Może zawierać cyfry i znaki podkreślenia, ale nie może zawierać znaków interpunkcyjnych i spacji.  
  
 Aby uzyskać odpowiednie informacje zobacz temat "Właściwości Name" w pomocy DAO.  
  
##  <a name="getrecordcount"></a>CDaoTableDef::GetRecordCount  
 Wywołanie tej funkcji Członkowskich, aby dowiedzieć się, jak wiele rekordów jest `CDaoTableDef` obiektu.  
  
```  
long GetRecordCount();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba rekordów dostępne w obiekcie tabledef.  
  
### <a name="remarks"></a>Uwagi  
 Wywoływanie `GetRecordCount` dla typu tabeli `CDaoTableDef` obiektu odzwierciedla przybliżoną liczbę rekordów w tabeli i ma to wpływ na natychmiast wraz z dodawaniem i usunąć rekordy tabeli. Wycofane transakcje będą wyświetlane jako część liczba rekordów do czasu wywołania [CDaoWorkSpace::CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase). A `CDaoTableDef` obiekt z żadne rekordy nie ma ustawienia właściwości liczba rekordów 0. Podczas pracy z dołączonymi tabelami lub baz danych ODBC `GetRecordCount` zawsze zwraca wartość -1.  
  
 Powiązane informacje zobacz temat "RecordCount Property" w pomocy DAO.  
  
##  <a name="getsourcetablename"></a>CDaoTableDef::GetSourceTableName  
 Wywołanie tej funkcji Członkowskich pobrać nazwy dołączonej tabeli źródłowej bazy danych.  
  
```  
CString GetSourceTableName();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CString` obiekt, który określa nazwę źródła dołączonej tabeli lub ciąg pusty, jeśli tabela danych natywnych.  
  
### <a name="remarks"></a>Uwagi  
 Dołączone jest tabela w innej bazie danych, połączony z bazą danych programu Microsoft Jet. Dane dołączone tabel pozostaną w zewnętrznej bazy danych, gdzie mogą być ustawiane przez inne aplikacje.  
  
 Powiązane informacje zobacz temat "SourceTableName Property" w pomocy DAO.  
  
##  <a name="getvalidationrule"></a>CDaoTableDef::GetValidationRule  
 Wywołanie tej funkcji członkowskich można pobrać reguły walidacji dla tabledef.  
  
```  
CString GetValidationRule();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A **cstring —** obiekt, który sprawdza poprawność danych w polu, ponieważ jest zmienione lub dodane do tabeli.  
  
### <a name="remarks"></a>Uwagi  
 Reguły sprawdzania poprawności są używane w operacjach aktualizowania. Jeśli tabledef zawiera reguły sprawdzania poprawności, aktualizacje tego tabledef muszą być zgodne ustalonej kryteriów przed danych zostanie zmieniona. Jeśli zmiana nie zgodne z kryteriami wyjątek zawierające wartość [GetValidationText](#getvalidationtext) jest generowany. Aby uzyskać `CDaoTableDef` obiektu, to `CString` jest tylko do odczytu dla dołączonej tabeli i odczytu/zapisu dla tabeli podstawowej.  
  
 Powiązane informacje zobacz temat "ValidationRule Property" w pomocy DAO.  
  
##  <a name="getvalidationtext"></a>CDaoTableDef::GetValidationText  
 Wywołanie tej funkcji można pobrać ciąg wyświetlany, gdy użytkownik wprowadza danych, która jest niezgodna z reguły weryfikacji.  
  
```  
CString GetValidationText();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CString` obiekt, który określa tekst wyświetlany, jeśli użytkownik wprowadzi danych, która jest niezgodna z reguły weryfikacji.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać `CDaoTableDef` obiektu, to `CString` jest tylko do odczytu dla dołączonej tabeli i odczytu/zapisu dla tabeli podstawowej.  
  
 Powiązane informacje zobacz temat "Komunikat Property" w pomocy DAO.  
  
##  <a name="isopen"></a>CDaoTableDef::IsOpen  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, czy `CDaoTableDef` obiekt jest obecnie otwarty.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli podano niezerowe `CDaoTableDef` obiekt jest otwarty; w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_pdatabase"></a>CDaoTableDef::m_pDatabase  
 Zawiera wskaźnik do [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiektu dla tej tabeli.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_pdaotabledef"></a>CDaoTableDef::m_pDAOTableDef  
 Zawiera wskaźnik do interfejsu OLE dla DAO tabledef obiektu odpowiadającego `CDaoTableDef` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli potrzebujesz dostępu interfejsu DAO bezpośrednio za pomocą tego wskaźnika.  
  
##  <a name="open"></a>CDaoTableDef::Open  
 Wywołanie tej funkcji członkowskiej, aby otworzyć tabledef wcześniej zapisanych w bazie danych użytkownika TableDef w kolekcji.  
  
```  
virtual void Open(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Wskaźnik do ciąg określający nazwę tabeli.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="refreshlink"></a>CDaoTableDef::RefreshLink  
 Wywołanie tej funkcji Członkowskich, aby zaktualizować informacje o połączeniu dla dołączonej tabeli.  
  
```  
void RefreshLink();
```  
  
### <a name="remarks"></a>Uwagi  
 Zmień informacje o połączeniu dla dołączonej tabeli przez wywołanie metody [SetConnect](#setconnect) w odpowiedniej `CDaoTableDef` obiektu, a następnie użyć `RefreshLink` funkcji członkowskiej, aby zaktualizować informacje. Podczas wywoływania `RefreshLink`, nie są zmieniane właściwości dołączonej tabeli.  
  
 Aby wymusić zmodyfikowane połączyć informacji zaczęły obowiązywać, wszystkie otwarte [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) oparte na tym tabledef obiekty muszą być zamknięte.  
  
 Powiązane informacje zobacz temat "RefreshLink Method" w pomocy DAO.  
  
##  <a name="setattributes"></a>CDaoTableDef::SetAttributes  
 Ustawia wartość wskazującą, jeden lub więcej właściwości `CDaoTableDef` obiektu.  
  
```  
void SetAttributes(long lAttributes);
```  
  
### <a name="parameters"></a>Parametry  
 `lAttributes`  
 Właściwości tabeli reprezentowany przez `CDaoTableDef` obiektu i może być sumę te stałe:  
  
|Stała|Opis|  
|--------------|-----------------|  
|**dbAttachExclusive**|W przypadku baz danych, które używają aparatu bazy danych programu Microsoft Jet wskazuje, że tabela jest otwarta w trybie wyłączności dołączonej tabeli.|  
|**dbAttachSavePWD**|W przypadku baz danych, które używają aparatu bazy danych programu Microsoft Jet wskazuje identyfikator użytkownika i hasło dla dołączonej tabeli są zapisywane z informacjami o połączeniu.|  
|**dbSystemObject**|Wskazuje, że tabela jest tabelą systemową dostarczone przez aparat bazy danych programu Microsoft Jet.|  
|**dbHiddenObject**|Wskazuje, że tabela jest ukryta tabeli dostarczone przez aparat bazy danych programu Microsoft Jet.|  
  
### <a name="remarks"></a>Uwagi  
 Podczas ustawiania wiele atrybutów, można połączyć je przez zsumowanie odpowiednie stałe przy użyciu operatora bitowego OR. Ustawienie **dbAttachExclusive** w tabeli nie dołączony tworzy wyjątek. Łączenie następujące wartości również produktu o wyjątku:  
  
- **dbAttachExclusive &#124; dbAttachedODBC**  
  
- **dbAttachSavePWD &#124; dbAttachedTable**  
  
 Powiązane informacje zobacz temat "Właściwość Attributes" w pomocy DAO.  
  
##  <a name="setconnect"></a>CDaoTableDef::SetConnect  
 Aby uzyskać `CDaoTableDef` obiekt, który reprezentuje dołączonej tabeli z obiektem ciągu składa się z co najmniej dwie części (specyfikatora typu bazy danych i ścieżka do bazy danych).  
  
```  
void SetConnect(LPCTSTR lpszConnect);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszConnect`  
 Wskaźnik do wyrażenia ciągu, który określa dodatkowe parametry do przekazania do ODBC i zainstalowania sterowników ISAM.  
  
### <a name="remarks"></a>Uwagi  
 Ścieżka, jak pokazano w poniższej tabeli pełną ścieżkę do katalogu zawierającego pliki bazy danych i musi być poprzedzony przez identyfikator "bazy danych =". W niektórych przypadkach (zgodnie z bazy danych programu Microsoft Excel i Microsoft Jet) określonej nazwy pliku jest uwzględniona w argumencie ścieżki bazy danych.  
  
> [!NOTE]
>  Nie dołączaj odstępy wokół znaku równości w instrukcjach ścieżkę w postaci "bazy danych = dysk:\\\path". To spowoduje wyjątek i błędom połączenia.  
  
 W poniższej tabeli przedstawiono typy możliwe bazy danych oraz ich odpowiednich specyfikatory bazy danych i ścieżki:  
  
|Typ bazy danych|Specyfikator|Ścieżka|  
|-------------------|---------------|----------|  
|Bazy danych przy użyciu aparatu bazy danych Jet|"[ `database`];"|" `drive`:\\\ *ścieżki*\\\ *filename*. MDB"|  
|dBASE III|"dBASE III;"|" `drive`:\\\ *ścieżka*"|  
|dBASE IV|"dBASE IV;"|" `drive`:\\\ *ścieżka*"|  
|dBASE 5|"dBASE 5.0;"|" `drive`:\\\ *ścieżka*"|  
|Paradox 3.x|"Paradox 3.x;"|" `drive`:\\\ *ścieżka*"|  
|Paradox 4.x|"Paradox 4.x;"|" `drive`:\\\ *ścieżka*"|  
|Paradox 5.x|"Paradox 5.x;"|" `drive`:\\\ *ścieżka*"|  
|Excel 3.0|"Excel 3.0;"|" `drive`:\\\ *ścieżki*\\\ *filename*. XLS"|  
|Excel 4.0|"Excel 4.0;"|" `drive`:\\\ *ścieżki*\\\ *filename*. XLS"|  
|Excel w wersji 5.0 lub Excel 95|"Excel 5.0".|" `drive`:\\\ *ścieżki*\\\ *filename*. XLS"|  
|Excel 97|"Excel 8.0;"|" `drive`:\\\ *ścieżki*\ *filename*. XLS"|  
|HTML Import|"HTML Import;"|" `drive`:\\\ *ścieżki*\ *filename*"|  
|Eksport HTML|"HTML Export;"|" `drive`:\\\ *ścieżka*"|  
|Tekst|"Tekst";|"dysk:\\\path"|  
|ODBC|"ODBC; Baza danych = `database`; Identyfikator UID = *użytkownika*; PWD = *hasło*; Nazwa DSN = *datasourcename;* LOGINTIMEOUT = *sekundy;*" (Nie może to być ciąg połączenia pełną dla wszystkich serwerów; jest tylko przykładowe. Bardzo ważne jest nie powinien być spacji między parametrami.)|Brak|  
|Program Exchange|"Do programu Exchange;<br /><br /> MAPILEVEL = *folderpath*;<br /><br /> [TYPEM = {0 &#124; 1}]<br /><br /> [Profil = *profilu*;]<br /><br /> [PWD = *hasło*;]<br /><br /> [BAZA DANYCH = `database`;] "|*"dysku*:\\\ *ścieżki*\\\ *filename*. MDB"|  
  
> [!NOTE]
>  Btrieve jest już obsługiwany w wersji DAO 3.5.  
  
 Należy użyć podwójny ukośnik odwrotny (\\\\) w parametrach połączenia. Jeśli zmieniono właściwości istniejącego połączenia za pomocą `SetConnect`, następnie należy wywołać [RefreshLink](#refreshlink). Jeśli są inicjowania właściwości połączenia za pomocą `SetConnect`, należy nie wywołania `RefreshLink`, ale najpierw należy wybrać to zrobić, Dodaj tabledef.  
  
 Jeśli hasło jest wymagana, ale nie podano, sterownik ODBC wyświetla logowania oknie dialogowym po raz pierwszy uzyskać dostępu do tabeli i ponownie, jeśli połączenie jest zamknięte i otwarte ponownie.  
  
 Można ustawić parametry połączenia dla `CDaoTableDef` obiektu podając argument źródła **Utwórz** funkcję elementu członkowskiego. Możesz sprawdzić ustawienie, aby określić typ, ścieżka, identyfikator użytkownika, hasło lub źródła danych ODBC bazy danych. Aby uzyskać więcej informacji zobacz dokumentację dla określonego sterownika.  
  
 Powiązane informacje zobacz temat "Połącz Property" w pomocy DAO.  
  
##  <a name="setname"></a>CDaoTableDef::SetName  
 Wywołanie tej funkcji Członkowskich, aby ustawić nazwę użytkownika dla tabeli.  
  
```  
void SetName(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Wskaźnik do wyrażenia ciągu, który określa nazwę tabeli.  
  
### <a name="remarks"></a>Uwagi  
 Nazwa musi rozpoczynać się od litery i może zawierać maksymalnie 64 znaki. Może zawierać cyfry i znaki podkreślenia, ale nie może zawierać znaków interpunkcyjnych i spacji.  
  
 Aby uzyskać odpowiednie informacje zobacz temat "Właściwości Name" w pomocy DAO.  
  
##  <a name="setsourcetablename"></a>CDaoTableDef::SetSourceTableName  
 Wywołanie tej funkcji Członkowskich, aby podać nazwę dołączonej tabeli lub nazwa tabeli podstawowej, na których `CDaoTableDef` podstawie obiektu, ponieważ znajduje się ona z oryginalnego źródła danych.  
  
```  
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszSrcTableName*  
 Wskaźnik do wyrażenia ciągu, który określa nazwę tabeli w zewnętrznej bazy danych. Dla tabeli podstawowej, ustawienie to ciąg pusty ("").  
  
### <a name="remarks"></a>Uwagi  
 Następnie należy wywołać [RefreshLink](#refreshlink). Ustawienie tej właściwości jest pusta dla tabeli podstawowej i odczytu/zapisu dla dołączonej tabeli lub obiektu nie są dołączane do kolekcji.  
  
 Powiązane informacje zobacz temat "SourceTableName Property" w pomocy DAO.  
  
##  <a name="setvalidationrule"></a>CDaoTableDef::SetValidationRule  
 Wywołanie tej funkcji członkowskich można ustawić reguły walidacji dla tabledef.  
  
```  
void SetValidationRule(LPCTSTR lpszValidationRule);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszValidationRule*  
 Wskaźnik do wyrażenia ciągu, która weryfikuje operacji.  
  
### <a name="remarks"></a>Uwagi  
 Reguły sprawdzania poprawności są używane w operacjach aktualizowania. Jeśli tabledef zawiera reguły sprawdzania poprawności, aktualizacje tego tabledef muszą być zgodne ustalonej kryteriów przed danych zostanie zmieniona. Jeśli zmiana nie zgodne z kryteriami wyjątek zawierający tekst [GetValidationText](#getvalidationtext) jest wyświetlany.  
  
 Walidacja jest obsługiwany tylko w przypadku baz danych, które używają aparatu bazy danych programu Microsoft Jet. Wyrażenie nie może odwoływać się do funkcje zdefiniowane przez użytkownika, funkcjach agregujących domeny, funkcje agregacji lub zapytania. Reguły sprawdzania poprawności `CDaoTableDef` obiektu mogą odwoływać się do wielu pól w tym obiekcie.  
  
 Na przykład dla pola o nazwie `hire_date` i `termination_date`, może być reguły sprawdzania poprawności:  
  
 [!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]  
  
 Powiązane informacje zobacz temat "ValidationRule Property" w pomocy DAO.  
  
##  <a name="setvalidationtext"></a>CDaoTableDef::SetValidationText  
 Wywołanie tej funkcji elementu członkowskiego, aby ustawić tekst wyjątku reguły sprawdzania poprawności `CDaoTableDef` obiektu z podstawowej tabeli obsługiwane przez aparat bazy danych programu Microsoft Jet.  
  
```  
void SetValidationText(LPCTSTR lpszValidationText);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszValidationText*  
 Wskaźnik do wyrażenia ciągu, który określa tekst wyświetlany, jeśli wprowadzonych danych jest nieprawidłowa.  
  
### <a name="remarks"></a>Uwagi  
 Nie można ustawić tekst sprawdzania poprawności dołączonej tabeli.  
  
 Powiązane informacje zobacz temat "Komunikat Property" w pomocy DAO.  
  
## <a name="see-also"></a>Zobacz też  
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)   
 [Klasa CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)
