---
title: Klasa CDaoTableDef
ms.date: 11/04/2016
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
ms.openlocfilehash: b2f431b250da4b791c06a629315d59bbc7935802
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579243"
---
# <a name="cdaotabledef-class"></a>Klasa CDaoTableDef

Przedstawia przechowywaną definicję tabeli bazowej lub dołączonej tabeli.

## <a name="syntax"></a>Składnia

```
class CDaoTableDef : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoTableDef::CDaoTableDef](#cdaotabledef)|Konstruuje `CDaoTableDef` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoTableDef::Append](#append)|Dodaje nową tabelę w bazie danych.|
|[CDaoTableDef::CanUpdate](#canupdate)|Zwraca wartość różną od zera, jeśli można zaktualizować tabeli (możesz zmodyfikować definicję pola lub właściwości tabeli).|
|[CDaoTableDef::Close](#close)|Zamyka otwarty tabledef.|
|[CDaoTableDef::Create](#create)|Tworzy tabelę, które mogą być dodawane do bazy danych przy użyciu [Append](#append).|
|[CDaoTableDef::CreateField](#createfield)|Wywołuje się, by utworzyć pole dla tabeli.|
|[CDaoTableDef::CreateIndex](#createindex)|Wywołuje się, by utworzyć indeks dla tabeli.|
|[CDaoTableDef::DeleteField](#deletefield)|Wywoływana, aby usunąć pola z tabeli.|
|[CDaoTableDef::DeleteIndex](#deleteindex)|Wywoływana, aby usunąć indeks z tabeli.|
|[CDaoTableDef::GetAttributes](#getattributes)|Zwraca wartość wskazującą, co najmniej jeden charakterystyki `CDaoTableDef` obiektu.|
|[CDaoTableDef::GetConnect](#getconnect)|Zwraca wartość, która zawiera informacje o źródle w tabeli.|
|[CDaoTableDef::GetDateCreated](#getdatecreated)|Zwraca datę i godzinę, w tabeli podstawowej bazowego `CDaoTableDef` został utworzony obiekt.|
|[CDaoTableDef::GetDateLastUpdated](#getdatelastupdated)|Zwraca datę i godzinę ostatniej zmiany wprowadzone do projektowania tabeli podstawowej.|
|[CDaoTableDef::GetFieldCount](#getfieldcount)|Zwraca wartość, która reprezentuje liczbę pól w tabeli.|
|[CDaoTableDef::GetFieldInfo](#getfieldinfo)|Zwraca wartość określonego rodzaju informacje dotyczące pól w tabeli.|
|[CDaoTableDef::GetIndexCount](#getindexcount)|Zwraca liczbę indeksów dla tabeli.|
|[CDaoTableDef::GetIndexInfo](#getindexinfo)|Zwraca określonych rodzajów informacji na temat indeksów dla tabeli.|
|[CDaoTableDef::GetName](#getname)|Zwraca nazwę użytkownika w tabeli.|
|[CDaoTableDef::GetRecordCount](#getrecordcount)|Zwraca liczbę rekordów w tabeli.|
|[CDaoTableDef::GetSourceTableName](#getsourcetablename)|Zwraca wartość, która określa nazwę dołączonej tabeli w bazie danych źródłowych.|
|[CDaoTableDef::GetValidationRule](#getvalidationrule)|Zwraca wartość, która weryfikuje dane w polu, ponieważ ona jest zmieniane ani dodawane do tabeli.|
|[CDaoTableDef::GetValidationText](#getvalidationtext)|Zwraca wartość, która określa tekst komunikatu, który wyświetla aplikacji, jeśli wartość obiektu pola nie spełnia określona reguła walidacji.|
|[CDaoTableDef::IsOpen](#isopen)|Zwraca wartość różną od zera, jeśli tabela jest Otwórz.|
|[CDaoTableDef::Open](#open)|Otwiera istniejący tabledef przechowywane w bazie danych przez firmy TableDef kolekcji.|
|[CDaoTableDef::RefreshLink](#refreshlink)|Aktualizuje informacje o połączeniu dla dołączonej tabeli.|
|[CDaoTableDef::SetAttributes](#setattributes)|Ustawia wartość wskazującą, co najmniej jeden charakterystyki `CDaoTableDef` obiektu.|
|[CDaoTableDef::SetConnect](#setconnect)|Ustawia wartość, która zawiera informacje o źródle w tabeli.|
|[CDaoTableDef::SetName](#setname)|Ustawia nazwę tabeli.|
|[CDaoTableDef::SetSourceTableName](#setsourcetablename)|Ustawia wartość, która określa nazwę dołączonej tabeli w bazie danych źródłowych.|
|[CDaoTableDef::SetValidationRule](#setvalidationrule)|Ustawia wartość, która weryfikuje dane w polu, ponieważ ona jest zmieniane ani dodawane do tabeli.|
|[CDaoTableDef::SetValidationText](#setvalidationtext)|Ustawia wartość, która określa tekst komunikatu, który wyświetla aplikacji, jeśli wartość obiektu pola nie spełnia określona reguła walidacji.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDaoTableDef::m_pDAOTableDef](#m_pdaotabledef)|Wskaźnik do bazowego obiektu tabledef interfejsu DAO.|
|[CDaoTableDef::m_pDatabase](#m_pdatabase)|Źródłowa baza danych dla tej tabeli.|

## <a name="remarks"></a>Uwagi

Każdy obiekt bazy danych DAO przechowuje kolekcję o nazwie tabledefs — zawierający wszystkie zapisane obiekty tabledef DAO.

Możesz manipulować definicji tabeli przy użyciu `CDaoTableDef` obiektu. Możesz na przykład:

- Sprawdź pola i indeks struktury dowolnej lokalnym, dołączonych lub zewnętrznego tabeli w bazie danych.

- Wywołaj `SetConnect` i `SetSourceTableName` funkcji elementów członkowskich dla tabel dołączonych i użyj `RefreshLink` funkcja elementu członkowskiego, aby zaktualizować połączenia dołączone tabel.

- Wywołaj `CanUpdate` funkcja elementu członkowskiego, aby określić, jeśli można edytować definicje pól w tabeli.

- Pobieranie lub Ustawianie warunków poprawności przy użyciu `GetValidationRule` i `SetValidationRule`i `GetValidationText` i `SetValidationText` funkcji elementów członkowskich.

- Użyj `Open` funkcji elementu członkowskiego, aby utworzyć tabelę, dynamiczny lub typ migawki `CDaoRecordset` obiektu.

    > [!NOTE]
    >  Klasy bazy danych DAO różnią się od klas baz danych MFC, które są oparte na Open Database Connectivity (ODBC). Wszystkie nazwy klasy bazy danych DAO mają prefiks "CDao". Możesz nadal dostęp do źródła danych ODBC przy użyciu klas DAO; klasy DAO ogólnie oferują możliwości wyższego poziomu, ponieważ są one specyficzne dla aparatu bazy danych Microsoft Jet.

### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>Aby użyć obiektów tabledef, pracować z istniejącej tabeli lub Utwórz nową tabelę

1. We wszystkich przypadkach najpierw skonstruuj `CDaoTableDef` obiektu, podając wskaźnik do [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiekt, do którego należy tabeli.

1. Następnie wykonaj następujące czynności, w zależności od tego, co chcesz zrobić:

   - Aby użyć istniejącego zapisanego tabeli, należy wywołać obiektu tabledef [Otwórz](#open) funkcji członkowskiej, podając nazwę zapisanego tabeli.

   - Aby utworzyć nową tabelę, należy wywołać obiekt tabledef [Utwórz](#create) funkcji członkowskiej, podając nazwę tabeli. Wywołaj [CreateField](#createfield) i [CreateIndex](#createindex) do dodawania pól i indeksy do tabeli.

   - Wywołaj [Append](#append) można zapisać w tabeli, dołączając ją do bazy danych tabledefs — kolekcja. `Create` umieszcza tabledef do stanu rozwartego, więc po wywołaniu `Create` Nie wywołuj `Open`.

        > [!TIP]
        >  Najprostszym sposobem utworzenia zapisanego tabel jest je tworzyć i przechowywać je w bazie danych przy użyciu programu Microsoft Access. Następnie można otworzyć i używać ich w kodzie MFC.

Aby użyć obiektu tabledef mają otwarte lub utworzone, należy utworzyć i otworzyć `CDaoRecordset` obiektu, określając nazwę tabledef z `dbOpenTable` wartość w *nOpenType* parametru.

Na potrzeby tworzenia obiektu tabledef `CDaoRecordset` obiektu, należy zwykle Utwórz lub Otwórz tabledef zgodnie z powyższym opisem, a następnie skonstruować obiekt zestawu rekordów przekazywania wskaźnika do obiektu tabledef po wywołaniu [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open). Tabledef, które można przekazać musi być w stanie otwartym. Aby uzyskać więcej informacji, zobacz klasy [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Po zakończeniu za pomocą obiektu tabledef wywołać jej [Zamknij](../../mfc/reference/cdaorecordset-class.md#close) element członkowski funkcji; następnie zniszczenie obiektu tabledef.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CDaoTableDef`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

##  <a name="append"></a>  CDaoTableDef::Append

Wywołaj tę funkcję elementu członkowskiego, po wywołaniu metody [Utwórz](#create) można utworzyć nowego obiektu tabledef, aby zapisać tabledef w bazie danych.

```
virtual void Append();
```

### <a name="remarks"></a>Uwagi

Funkcja dołącza obiektu do bazy danych tabledefs — kolekcja. Podczas definiowania go nie dołączając ją służy tabledef jako tymczasowy obiekt, ale jeśli chcesz zapisać i używać go, należy wywołać `Append`.

> [!NOTE]
>  MFC zgłasza wyjątek, Jeśli spróbujesz dołączyć tabledef nienazwane (zawierający wartość null lub pusty ciąg).

Aby uzyskać powiązane informacje zobacz temat "Dołącz metody" w Pomocy programu DAO.

##  <a name="canupdate"></a>  CDaoTableDef::CanUpdate

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy definicję tabeli bazowej `CDaoTableDef` obiektu można zmieniać.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli struktura tabeli (schemat), które mogą być modyfikowane (Dodaj lub Usuń indeksy i pola), w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślnie nowo utworzoną tabelę bazowego `CDaoTableDef` obiekt może być aktualizowany i dołączonej tabeli podstawowej `CDaoTableDef` nie można zaktualizować obiektu. A `CDaoTableDef` obiekt może być nadaje się do aktualizacji, nawet jeśli nie nadaje Wynikowy zestaw rekordów.

Aby uzyskać powiązane informacje zobacz temat "Można zaktualizować właściwości" w Pomocy programu DAO.

##  <a name="cdaotabledef"></a>  CDaoTableDef::CDaoTableDef

Konstruuje `CDaoTableDef` obiektu.

```
CDaoTableDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Parametry

*pDatabase*<br/>
Wskaźnik do [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiektu.

### <a name="remarks"></a>Uwagi

Po konstruowanie obiektu, należy wywołać [Utwórz](#create) lub [Otwórz](#open) funkcja elementu członkowskiego. Po zakończeniu za pomocą obiektu, należy wywołać jej [Zamknij](#close) element członkowski funkcji i zniszcz `CDaoTableDef` obiektu.

##  <a name="close"></a>  CDaoTableDef::Close

Wywołaj tę funkcję elementu członkowskiego, aby zamknąć i zwolnić obiekt tabledef.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Zwykle po wywołaniu `Close`, Usuń obiekt tabledef, jeśli został przydzielony przy użyciu **nowe**.

Możesz wywołać [Otwórz](#open) ponownie po wywołaniu `Close`. Dzięki temu można ponownie użyć obiektu tabledef.

Aby uzyskać powiązane informacje zobacz temat "Metody Close" w Pomocy programu DAO.

##  <a name="create"></a>  CDaoTableDef::Create

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć nową tabelę zapisane.

```
virtual void Create(
    LPCTSTR lpszName,
    long lAttributes = 0,
    LPCTSTR lpszSrcTable = NULL,
    LPCTSTR lpszConnect = NULL);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Wskaźnik do ciągu zawierającego nazwę tabeli.

*lAttributes*<br/>
Wartość odpowiadającą właściwości tabeli reprezentowany przez obiekt tabledef. Bitowe OR umożliwia łączenie dowolne z następujących stałych:

|Stała|Opis|
|--------------|-----------------|
|`dbAttachExclusive`|W przypadku baz danych, które używają aparatu bazy danych Microsoft Jet wskazuje, że tabela jest otwarty do wyłącznego użytku dołączonej tabeli.|
|`dbAttachSavePWD`|W przypadku baz danych, które używają aparatu bazy danych Microsoft Jet wskazuje, że identyfikator użytkownika i hasło dla dołączonej tabeli są zapisywane z informacjami o połączeniu.|
|`dbSystemObject`|Wskazuje, że tabela jest dostarczane przez aparat bazy danych Microsoft Jet tabeli systemowej.|
|`dbHiddenObject`|Wskazuje, że jest tabela ukryte, dostarczone przez aparat bazy danych Microsoft Jet.|

*lpszSrcTable*<br/>
Wskaźnik do ciągu zawierającego nazwę tabeli źródłowej. Domyślnie ta wartość jest inicjowany jako wartości NULL.

*lpszConnect*<br/>
Wskaźnik do ciągu zawierającego domyślne parametry połączenia. Domyślnie ta wartość jest inicjowany jako wartości NULL.

### <a name="remarks"></a>Uwagi

Gdy mają nazwane tabledef, można wywołać [Append](#append) zapisanie tabledef w bazie danych tabledefs — kolekcja. Po wywołaniu `Append`tabledef znajduje się w stanie otwarcia i służy do tworzenia [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obiektu.

Aby uzyskać powiązane informacje zobacz temat "CreateTableDef metody" w Pomocy programu DAO.

##  <a name="createfield"></a>  CDaoTableDef::CreateField

Wywołaj tę funkcję elementu członkowskiego, aby dodać pole do tabeli.

```
void CreateField(
    LPCTSTR lpszName,
    short nType,
    long lSize,
    long lAttributes = 0);

void CreateField(CDaoFieldInfo& fieldinfo);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Wskaźnik do wyrażenia ciągu, określając nazwę tego pola.

*nNie*<br/>
Wartość wskazująca, typ danych pola. To ustawienie może być jedną z następujących wartości:

|Typ|Rozmiar (bajty)|Opis|
|----------|--------------------|-----------------|
|`dbBoolean`|1 bajt|WARTOŚĆ LOGICZNA|
|`dbByte`|BYTE|
|`dbInteger`|2|int|
|`dbLong`|4|long|
|`dbCurrency`|8|Waluty ( [COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|float|
|`dbDouble`|8|double|
|`dbDate`|8|Data/Godzina ( [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Tekst ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Długie plik binarny (obiektu OLE) [CLongBinary](../../mfc/reference/clongbinary-class.md) lub [CByteArray](../../mfc/reference/cbytearray-class.md)|
|`dbMemo`|0|Notatka ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|

*lSize*<br/>
Wartość, który określa maksymalny rozmiar w bajtach, pola, które zawiera tekst, lub stały rozmiar pola, które zawiera wartości tekstowe lub liczbowe. *LSize* parametr jest ignorowany dla wszystkich pól poza polami tekstu.

*lAttributes*<br/>
Wartość odpowiadającą właściwości pola i że można łączyć, używając bitowe OR.

|Stała|Opis|
|--------------|-----------------|
|`dbFixedField`|Rozmiaru pola jest stały (ustawienie domyślne dla pól liczbowych).|
|`dbVariableField`|Rozmiar pola jest zmienną (tylko w przypadku pola tekstowe).|
|`dbAutoIncrField`|Wartość pola dla nowych rekordów jest automatycznie zwiększany unikatowy długa liczba całkowita, nie można jej zmienić. Obsługiwane tylko w tabelach bazy danych Microsoft Jet.|
|`dbUpdatableField`|Można zmienić wartość pola.|
|`dbDescending`|Pola są sortowane malejąco (Z - A lub 0, 100) zamówienia (dotyczy tylko pól obiektu w kolekcji pól indeks obiektu). Pominięcie tej stałej pola są posortowane w kolejności rosnącej (A - Z lub 0 - 100) zamówienia (ustawienie domyślne).|

*FieldInfo*<br/>
Odwołanie do [cdaofieldinfo —](../../mfc/reference/cdaofieldinfo-structure.md) struktury.

### <a name="remarks"></a>Uwagi

A `DAOField` obiekt (OLE) jest tworzone i dołączane do kolekcji pól `DAOTableDef` obiektu (OLE). Oprócz jej na użytek sprawdzenie właściwości obiektu, można również użyć `CDaoFieldInfo` do konstruowania przy tworzeniu nowych pól w tabledef parametru wejściowego. Pierwsza wersja `CreateField` jest łatwiejszy w obsłudze, ale jeśli chcesz, aby uzyskać bardziej precyzyjną kontrolę, można użyć drugą wersję `CreateField`, który bierze `CDaoFieldInfo` parametru.

Jeśli używasz wersji `CreateField` przyjmującej `CDaoFieldInfo` parametrów, należy starannie ustawić każdego z następujących członków `CDaoFieldInfo` strukturę:

- `m_strName`

- `m_nType`

- `m_lSize`

- `m_lAttributes`

- `m_bAllowZeroLength`

Pozostałe elementy członkowskie z `CDaoFieldInfo` powinna być równa **0**, FALSE lub pustym ciągiem, zgodnie z potrzebami dla elementu członkowskiego, lub `CDaoException` mogą wystąpić.

Aby uzyskać powiązane informacje zobacz temat "CreateField metody" w Pomocy programu DAO.

##  <a name="createindex"></a>  CDaoTableDef::CreateIndex

Wywołaj tę funkcję, aby dodać indeks do tabeli.

```
void CreateIndex(CDaoIndexInfo& indexinfo);
```

### <a name="parameters"></a>Parametry

*indexinfo*<br/>
Odwołanie do [cdaoindexinfo —](../../mfc/reference/cdaoindexinfo-structure.md) struktury.

### <a name="remarks"></a>Uwagi

Indeksy określić kolejność rekordów dostępne z tabel bazy danych i czy zduplikowane rekordy są akceptowane. Indeksy również zapewniają wydajny dostęp do danych.

Jest konieczne tworzenie indeksów dla tabel, ale w dużych, nieindeksowanym tabel, uzyskiwanie dostępu do określonego rekordu lub tworzenie zestawu rekordów może zająć dużo czasu. Z drugiej strony, spowalnia tworzenie indeksów zbyt wiele aktualizacji, Dołącz i operacje usuwania, ponieważ wszystkie indeksy są automatycznie aktualizowane. Jak zdecydować, której indeksy, aby utworzyć, należy wziąć pod uwagę te czynniki.

Następujące elementy członkowskie z `CDaoIndexInfo` struktury musi być ustawiona:

- `m_strName` Należy podać nazwę.

- `m_pFieldInfos` Musi się odnosić do tablicy `CDaoIndexFieldInfo` struktury.

- `m_nFields` Należy określić liczbę pól w tablicy `CDaoFieldInfo` struktury.

Pozostałe elementy członkowskie zostanie zignorowane, jeśli ustawiona na wartość FALSE. Ponadto `m_lDistinctCount` element jest ignorowany podczas tworzenia indeksu.

##  <a name="deletefield"></a>  CDaoTableDef::DeleteField

Wywołaj tę funkcję elementu członkowskiego, aby usunąć pole i stał się niedostępny.

```
void DeleteField(LPCTSTR lpszName);
void DeleteField(int nIndex);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Wskaźnik do wyrażenia ciągu, która jest nazwą istniejącego pola.

*nIndex*<br/>
Indeks pól w tabeli liczony od zera kolekcji pól, do wyszukiwania według indeksu.

### <a name="remarks"></a>Uwagi

Można użyć tej funkcji elementu członkowskiego na nowy obiekt, który nie został dołączane do bazy danych lub gdy [CanUpdate](#canupdate) zwraca wartość różną od zera.

Aby uzyskać powiązane informacje zobacz temat "Usuń metody" w Pomocy programu DAO.

##  <a name="deleteindex"></a>  CDaoTableDef::DeleteIndex

Wywołaj tę funkcję elementu członkowskiego, można usunąć indeksu w tabeli źródłowej.

```
void DeleteIndex(LPCTSTR lpszName);
void DeleteIndex(int nIndex);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Wskaźnik do wyrażenia ciągu, która jest nazwą istniejącego indeksu.

*nIndex*<br/>
Indeks tablicy obiektu indeksu w database liczony od zera tabledefs — kolekcja, do wyszukiwania według indeksu.

### <a name="remarks"></a>Uwagi

Można użyć tej funkcji elementu członkowskiego na nowy obiekt, który nie został dołączony do bazy danych lub gdy [CanUpdate](#canupdate) zwraca wartość różną od zera.

Aby uzyskać powiązane informacje zobacz temat "Usuń metody" w Pomocy programu DAO.

##  <a name="getattributes"></a>  CDaoTableDef::GetAttributes

Dla `CDaoTableDef` obiekt, wartość zwracana określa właściwości tabeli, reprezentowane przez `CDaoTableDef` obiektu i może być sumę te stałe:

```
long GetAttributes();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość wskazującą, co najmniej jeden charakterystyki `CDaoTableDef` obiektu.

### <a name="remarks"></a>Uwagi

|Stała|Opis|
|--------------|-----------------|
|`dbAttachExclusive`|W przypadku baz danych, które używają aparatu bazy danych Microsoft Jet wskazuje, że tabela jest otwarty do wyłącznego użytku dołączonej tabeli.|
|`dbAttachSavePWD`|W przypadku baz danych, które używają aparatu bazy danych Microsoft Jet wskazuje, że identyfikator użytkownika i hasło dla dołączonej tabeli są zapisywane z informacjami o połączeniu.|
|`dbSystemObject`|Wskazuje, że tabela jest dostarczane przez aparat bazy danych Microsoft Jet tabeli systemowej.|
|`dbHiddenObject`|Wskazuje, że jest tabela ukryte, dostarczone przez aparat bazy danych Microsoft Jet.|
|`dbAttachedTable`|Wskazuje, że tabela jest z bazy danych bez ODBC, takich jak bazy danych Paradox dołączonej tabeli.|
|`dbAttachedODBC`|Wskazuje, że tabela jest dołączonej tabeli z bazy danych ODBC, takich jak Microsoft SQL Server.|

Tabela systemowa jest tabeli utworzonej przez aparat bazy danych Microsoft Jet zawiera różne informacje wewnętrzne.

Ukryte jest tabela, dla tymczasowych utworzonych przez aparat bazy danych Microsoft Jet.

Aby uzyskać powiązane informacje zobacz temat "Atrybuty właściwości" w Pomocy programu DAO.

##  <a name="getconnect"></a>  CDaoTableDef::GetConnect

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać parametry połączenia dla źródła danych.

```
CString GetConnect();
```

### <a name="return-value"></a>Wartość zwracana

A `CString` obiekt, który zawiera typ ścieżki i bazy danych dla tabeli.

### <a name="remarks"></a>Uwagi

Aby uzyskać `CDaoTableDef` obiekt, który reprezentuje dołączonej tabeli `CString` obiekt składa się z co najmniej dwa elementy (Specyfikator typu bazy danych i ścieżka do bazy danych).

Ścieżka, jak pokazano w poniższej tabeli jest pełną ścieżką do katalogu zawierającego pliki bazy danych i muszą być poprzedzone identyfikator "bazy danych =". W niektórych przypadkach (zgodnie z bazy danych Microsoft Jet i programu Microsoft Excel) nazwa_pliku określonych znajduje się w argumencie ścieżki bazy danych.

W tabeli [CDaoTableDef::SetConnect](#setconnect) przedstawiono typy możliwe bazy danych i ich odpowiednich specyfikatory bazy danych i ścieżki:

Dla tabel bazowych bazy danych Microsoft Jet, specyfikator jest pustym ciągiem ("").

Jeśli hasło jest wymagana, ale nie podano, sterownik ODBC wyświetla logowania okna dialogowego po raz pierwszy uzyskano dostęp do tabeli i ponownie, jeśli połączenie jest zamknięte i otwarte ponownie. Jeśli ma dołączonej tabeli `dbAttachSavePWD` atrybutu, monit o zalogowanie będą widoczne po otwarciu tabeli.

Aby uzyskać powiązane informacje zobacz temat "Connect Property" w Pomocy programu DAO.

##  <a name="getdatecreated"></a>  CDaoTableDef::GetDateCreated

Wywołaj tę funkcję, aby określić datę i godzinę w tabeli bazowej `CDaoTableDef` został utworzony obiekt.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Wartość zwracana

Wartość zawierającą datę i godzinę utworzenia tabeli bazowej `CDaoTableDef` obiektu.

### <a name="remarks"></a>Uwagi

Ustawienia daty i godziny są uzyskiwane z komputera, na którym został utworzony lub ostatniej aktualizacji tabeli podstawowej. W środowisku wielodostępnym użytkowników należy uzyskać te ustawienia bezpośrednio z serwera plików, aby uniknąć niezgodności; oznacza to, że wszyscy klienci należy używać źródła czasu "standardowy" — być może z jednego serwera.

Aby uzyskać powiązane informacje zobacz temat "DateCreated LastUpdated właściwości", w Pomocy programu DAO.

##  <a name="getdatelastupdated"></a>  CDaoTableDef::GetDateLastUpdated

Wywołaj tę funkcję, aby określić datę i godzinę w tabeli bazowej `CDaoTableDef` obiekt był ostatnio aktualizowany.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która zawiera datę i godzinę w tabeli bazowej `CDaoTableDef` obiekt był ostatnio aktualizowany.

### <a name="remarks"></a>Uwagi

Ustawienia daty i godziny są uzyskiwane z komputera, na którym został utworzony lub ostatniej aktualizacji tabeli podstawowej. W środowisku wielodostępnym użytkowników należy uzyskać te ustawienia bezpośrednio z serwera plików, aby uniknąć niezgodności; oznacza to, że wszyscy klienci należy używać źródła czasu "standardowy" — być może z jednego serwera.

Aby uzyskać powiązane informacje zobacz temat "DateCreated LastUpdated właściwości", w Pomocy programu DAO.

##  <a name="getfieldcount"></a>  CDaoTableDef::GetFieldCount

Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę pól zdefiniowanych w tabeli.

```
short GetFieldCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba pól w tabeli.

### <a name="remarks"></a>Uwagi

Jeśli wartość wynosi 0, nie ma żadnych obiektów w kolekcji.

Aby uzyskać powiązane informacje zobacz temat "Właściwości liczba" w Pomocy programu DAO.

##  <a name="getfieldinfo"></a>  CDaoTableDef::GetFieldInfo

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać różne rodzaje informacji na temat pola zdefiniowane w tabledef.

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

*nIndex*<br/>
Indeks obiektu pola w tabeli liczony od zera kolekcji pól, do wyszukiwania według indeksu.

*FieldInfo*<br/>
Odwołanie do [cdaofieldinfo —](../../mfc/reference/cdaofieldinfo-structure.md) struktury.

*dwInfoOptions*<br/>
Opcje, które określają, które informacje o polu do pobrania. Dostępne opcje są wymienione w tym miejscu oraz co mogą spowodować, że funkcja zwróci:

- `AFX_DAO_PRIMARY_INFO` (Ustawienie domyślne) Nazwa, typ, rozmiar, atrybuty. Użyj tej opcji, aby uzyskać największą wydajność.

- `AFX_DAO_SECONDARY_INFO` Informacje o podstawowym, plus: numer pozycji, wymagane, Zezwalaj na tabeli źródłowej obcego Nazwa pola źródła zerową długość, kolejność sortowania,

- `AFX_DAO_ALL_INFO` Informacje podstawowe i pomocnicze, plus: wartość domyślna reguła sprawdzania poprawności, tekst sprawdzania poprawności

*lpszName*<br/>
Wskaźnik na nazwę obiektu pole wyszukiwania według nazwy. Nazwa jest ciągiem o długości maksymalnie 64 znaków, który unikatowej nazwy pola.

### <a name="remarks"></a>Uwagi

Jednej wersji funkcji umożliwia wyszukiwanie pola przez indeks. Druga wersja służy do wyszukiwania według nazwy pola.

Aby uzyskać opis zwrócone informacje, zobacz [cdaofieldinfo —](../../mfc/reference/cdaofieldinfo-structure.md) struktury. Ta struktura zawiera elementy członkowskie, które odnoszą się do elementów wymienionych powyżej w opisie informacji *dwInfoOptions*. W przypadku żądania informacji o jeden poziom, otrzymasz informacje dotyczące wszelkich poprzednich poziomach.

Aby uzyskać powiązane informacje zobacz temat "Atrybuty właściwości" w Pomocy programu DAO.

##  <a name="getindexcount"></a>  CDaoTableDef::GetIndexCount

Wywołanie tej funkcji elementu członkowskiego w celu uzyskania liczby indeksów dla tabeli.

```
short GetIndexCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba indeksów dla tabeli.

### <a name="remarks"></a>Uwagi

Jeśli wartość wynosi 0, brak jest indeksów w kolekcji.

Aby uzyskać powiązane informacje zobacz temat "Właściwości liczba" w Pomocy programu DAO.

##  <a name="getindexinfo"></a>  CDaoTableDef::GetIndexInfo

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać różne rodzaje informacji o zdefiniowanych w tabledef indeksu.

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

*nIndex*<br/>
Indeks liczbowy indeks obiektu w tabeli liczony od zera indeksów kolekcji, wyszukiwać według ich pozycji w kolekcji.

*indexinfo*<br/>
Odwołanie do [cdaoindexinfo —](../../mfc/reference/cdaoindexinfo-structure.md) struktury.

*dwInfoOptions*<br/>
Opcje, które określają, które informacje o indeksie do pobrania. Dostępne opcje są wymienione w tym miejscu oraz co mogą spowodować, że funkcja zwróci:

- `AFX_DAO_PRIMARY_INFO` Nazwa pola Info, pola. Użyj tej opcji, aby uzyskać największą wydajność.

- `AFX_DAO_SECONDARY_INFO` Podstawowe informacje, a także: podstawowy, unikatowe, Clustered Ignoruj wartości null, wymagane, zagranicznych

- `AFX_DAO_ALL_INFO` Informacje podstawowe i pomocnicze, a także: liczności unikatowych wartości

*lpszName*<br/>
Wskaźnik na nazwę obiektu indeksu wyszukiwania według nazwy.

### <a name="remarks"></a>Uwagi

Jednej wersji funkcji pozwala wyszukiwać indeksu za pomocą jego pozycji w kolekcji. Druga wersja pozwala indeksu wyszukiwania według nazwy.

Aby uzyskać opis zwrócone informacje, zobacz [cdaoindexinfo —](../../mfc/reference/cdaoindexinfo-structure.md) struktury. Ta struktura zawiera elementy członkowskie, które odnoszą się do elementów wymienionych powyżej w opisie informacji *dwInfoOptions*. W przypadku żądania informacji o jeden poziom, otrzymasz informacje dotyczące wszelkich poprzednich poziomach.

Aby uzyskać powiązane informacje zobacz temat "Atrybuty właściwości" w Pomocy programu DAO.

##  <a name="getname"></a>  CDaoTableDef::GetName

Wywołaj tę funkcję elementu członkowskiego, można uzyskać nazwy użytkownika w tabeli podstawowej.

```
CString GetName();
```

### <a name="return-value"></a>Wartość zwracana

Zdefiniowana przez użytkownika nazwa dla tabeli.

### <a name="remarks"></a>Uwagi

Ta nazwa zaczyna się od litery i może zawierać maksymalnie 64 znaki. Może zawierać cyfry i znaki podkreślenia, ale nie może zawierać znaków interpunkcyjnych lub miejsca do magazynowania.

Aby uzyskać powiązane informacje zobacz temat "Nazwa właściwości" w Pomocy programu DAO.

##  <a name="getrecordcount"></a>  CDaoTableDef::GetRecordCount

Wywołaj tę funkcję elementu członkowskiego, aby dowiedzieć się, jak wiele rekordów jest `CDaoTableDef` obiektu.

```
long GetRecordCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba rekordów, dostępne w obiekcie tabledef.

### <a name="remarks"></a>Uwagi

Wywoływanie `GetRecordCount` dla typu tabeli `CDaoTableDef` obiektu odzwierciedla przybliżoną liczbę rekordów w tabeli i jest zależna od razu zgodnie z tabeli rekordy są dodawane i usuwane. Wycofane transakcje będą wyświetlane jako część liczba rekordów, dopóki nie zostanie wywołana [CDaoWorkSpace::CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase). A `CDaoTableDef` obiekt z żadne rekordy nie ma ustawienia właściwości liczba rekordów 0. Podczas pracy z tabelami dołączonych lub baz danych ODBC, `GetRecordCount` zawsze zwraca wartość -1.

Aby uzyskać powiązane informacje zobacz temat "Właściwości RecordCount" w Pomocy programu DAO.

##  <a name="getsourcetablename"></a>  CDaoTableDef::GetSourceTableName

Wywołaj tę funkcję elementu członkowskiego, aby pobrać nazwę dołączonej tabeli źródłowej bazy danych.

```
CString GetSourceTableName();
```

### <a name="return-value"></a>Wartość zwracana

A `CString` obiekt, który określa nazwę źródła dołączonej tabeli lub pusty ciąg, jeśli tabela danych natywnych.

### <a name="remarks"></a>Uwagi

Dołączonej tabeli znajduje się tabela z innej bazy danych połączone z bazą danych Microsoft Jet. Dane dołączone tabel pozostaną w zewnętrznej bazie danych, gdzie mogą być zmieniane przez inne aplikacje.

Aby uzyskać powiązane informacje zobacz temat "SourceTableName Property" w Pomocy programu DAO.

##  <a name="getvalidationrule"></a>  CDaoTableDef::GetValidationRule

Wywołaj tę funkcję elementu członkowskiego, aby pobrać reguły sprawdzania poprawności dla tabledef.

```
CString GetValidationRule();
```

### <a name="return-value"></a>Wartość zwracana

A `CString` obiekt, który sprawdza poprawność danych w polu, ponieważ ona jest zmieniane ani dodawane do tabeli.

### <a name="remarks"></a>Uwagi

Reguły sprawdzania poprawności są używane w operacji aktualizowania. Jeśli tabledef zawiera reguły sprawdzania poprawności, aktualizacje tego tabledef musi odpowiadać wstępnie zdefiniowanych kryteriów, przed zmianą danych. Jeśli zmiana niezgodny z kryteriami, wyjątek zawierającą wartość [GetValidationText](#getvalidationtext) zgłaszany. Aby uzyskać `CDaoTableDef` obiektu to `CString` jest tylko do odczytu dla dołączonej tabeli i odczytu/zapisu dla tabeli podstawowej.

Aby uzyskać powiązane informacje zobacz temat "ValidationRule Property" w Pomocy programu DAO.

##  <a name="getvalidationtext"></a>  CDaoTableDef::GetValidationText

Wywołaj tę funkcję, aby pobrać ciąg do wyświetlenia, gdy użytkownik wprowadza dane, która jest niezgodna z reguł sprawdzania poprawności.

```
CString GetValidationText();
```

### <a name="return-value"></a>Wartość zwracana

A `CString` obiekt, który określa tekst wyświetlany, gdy użytkownik wprowadza dane, która jest niezgodna z reguł sprawdzania poprawności.

### <a name="remarks"></a>Uwagi

Aby uzyskać `CDaoTableDef` obiektu to `CString` jest tylko do odczytu dla dołączonej tabeli i odczytu/zapisu dla tabeli podstawowej.

Aby uzyskać powiązane informacje zobacz temat "Property komunikat" w Pomocy programu DAO.

##  <a name="isopen"></a>  CDaoTableDef::IsOpen

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy `CDaoTableDef` obiektu jest obecnie otwarty.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość różną od zera `CDaoTableDef` obiekt jest otwarty; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

##  <a name="m_pdatabase"></a>  CDaoTableDef::m_pDatabase

Zawiera wskaźnik do [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) obiektu dla tej tabeli.

### <a name="remarks"></a>Uwagi

##  <a name="m_pdaotabledef"></a>  CDaoTableDef::m_pDAOTableDef

Zawiera wskaźnik do interfejsu OLE dla DAO tabledef obiektu bazowego `CDaoTableDef` obiektu.

### <a name="remarks"></a>Uwagi

Jeśli potrzebujesz dostępu do interfejsu DAO bezpośrednio za pomocą tego wskaźnika.

##  <a name="open"></a>  CDaoTableDef::Open

Wywołanie tej funkcji elementu członkowskiego, aby otworzyć tabledef wcześniej zapisane w bazie danych przez firmy TableDef kolekcji.

```
virtual void Open(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Wskaźnik do ciągu, który określa nazwę tabeli.

### <a name="remarks"></a>Uwagi

##  <a name="refreshlink"></a>  CDaoTableDef::RefreshLink

Wywołaj tę funkcję elementu członkowskiego, aby zaktualizować informacje o połączeniu dla dołączonej tabeli.

```
void RefreshLink();
```

### <a name="remarks"></a>Uwagi

Zmień informacje o połączeniu dla dołączonej tabeli przez wywołanie metody [SetConnect](#setconnect) w odpowiedniej `CDaoTableDef` obiektu, a następnie używając `RefreshLink` funkcja elementu członkowskiego, aby zaktualizować informacje. Gdy wywołujesz `RefreshLink`, właściwości dołączonej tabeli nie są zmieniane.

Aby wymusić zmodyfikowanego informacji o połączeniu, aby aktywować wszystkie otwarte [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obiekty w zależności od tego tabledef muszą być zamknięte.

Aby uzyskać powiązane informacje zobacz temat "RefreshLink metody" w Pomocy programu DAO.

##  <a name="setattributes"></a>  CDaoTableDef::SetAttributes

Ustawia wartość wskazującą, co najmniej jeden charakterystyki `CDaoTableDef` obiektu.

```
void SetAttributes(long lAttributes);
```

### <a name="parameters"></a>Parametry

*lAttributes*<br/>
Właściwości tabeli, reprezentowane przez `CDaoTableDef` obiektu i może być sumę te stałe:

|Stała|Opis|
|--------------|-----------------|
|`dbAttachExclusive`|W przypadku baz danych, które używają aparatu bazy danych Microsoft Jet wskazuje, że tabela jest otwarty do wyłącznego użytku dołączonej tabeli.|
|`dbAttachSavePWD`|W przypadku baz danych, które używają aparatu bazy danych Microsoft Jet wskazuje, że identyfikator użytkownika i hasło dla dołączonej tabeli są zapisywane z informacjami o połączeniu.|
|`dbSystemObject`|Wskazuje, że tabela jest dostarczane przez aparat bazy danych Microsoft Jet tabeli systemowej.|
|`dbHiddenObject`|Wskazuje, że jest tabela ukryte, dostarczone przez aparat bazy danych Microsoft Jet.|

### <a name="remarks"></a>Uwagi

Podczas ustawiania wiele atrybutów, można połączyć je przez zsumowanie odpowiednie stałe, za pomocą operatora bitowego OR. Ustawienie `dbAttachExclusive` w tabeli nie dołączony generuje wyjątek. Łącząc następujące wartości również wygenerować wyjątek, który:

- **dbAttachExclusive &#124; dbAttachedODBC**

- **dbAttachSavePWD &#124; dbAttachedTable**

Aby uzyskać powiązane informacje zobacz temat "Atrybuty właściwości" w Pomocy programu DAO.

##  <a name="setconnect"></a>  CDaoTableDef::SetConnect

Aby uzyskać `CDaoTableDef` obiekt, który reprezentuje dołączonej tabeli, z obiektem ciągu, który składa się z jednego lub dwóch części (Specyfikator typu bazy danych i ścieżka do bazy danych).

```
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Parametry

*lpszConnect*<br/>
Wskaźnik do wyrażenia ciągu, który określa dodatkowe parametry do przekazania do ODBC lub zainstalowania sterowników ISAM.

### <a name="remarks"></a>Uwagi

Ścieżka, jak pokazano w poniższej tabeli jest pełną ścieżką do katalogu zawierającego pliki bazy danych i muszą być poprzedzone identyfikator "bazy danych =". W niektórych przypadkach (zgodnie z bazy danych Microsoft Jet i programu Microsoft Excel) nazwa_pliku określonych znajduje się w argumencie ścieżki bazy danych.

> [!NOTE]
>  Nie dołączaj odstęp wokół znaku równości w instrukcji ścieżki, w postaci "bazy danych = dysk:\\\path". To spowoduje wyjątek i niepowodzenie połączenia.

W poniższej tabeli przedstawiono typy możliwe bazy danych i ich odpowiednich specyfikatory bazy danych i ścieżki:

|Typ bazy danych|Specyfikator|Ścieżka|
|-------------------|---------------|----------|
|Bazy danych przy użyciu aparatu bazy danych Jet|"[ `database`];"|" `drive`:\\\ *ścieżki*\\\ *filename*. MDB"|
|dBASE III|"dBASE III;"|" `drive`:\\\ *ścieżki*"|
|dBASE IV|"dBASE IV;"|" `drive`:\\\ *ścieżki*"|
|dBASE 5|"dBASE 5.0."|" `drive`:\\\ *ścieżki*"|
|Paradox 3.x|"Paradox 3.x;"|" `drive`:\\\ *ścieżki*"|
|Paradox 4.x|"Paradox 4.x;"|" `drive`:\\\ *ścieżki*"|
|Paradox 5.x|"Paradox 5.x;"|" `drive`:\\\ *ścieżki*"|
|Excel 3.0|"Programu Excel 3.0;"|" `drive`:\\\ *ścieżki*\\\ *filename*. XLS"|
|4.0 programu Excel|"4.0 programu Excel;"|" `drive`:\\\ *ścieżki*\\\ *filename*. XLS"|
|Excel w wersji 5.0 lub Excel 95|"Programu Excel 5.0".|" `drive`:\\\ *ścieżki*\\\ *filename*. XLS"|
|Programu Excel 97|"Excel 8.0;"|" `drive`:\\\ *ścieżki*\ *filename*. XLS"|
|HTML Import|"HTML Import;"|" `drive`:\\\ *ścieżki*\ *filename*"|
|Eksportowanie kodu HTML|"HTML Export;"|" `drive`:\\\ *ścieżki*"|
|Tekst|"Text";|"dysk:\\\path"|
|ODBC|"ODBC; Bazy danych = `database`; Identyfikator UID = *użytkownika*; PWD = *hasło*; Nazwa DSN = *datasourcename;* LOGINTIMEOUT = *(w sekundach);*" (To może nie być pełne parametry połączenia dla wszystkich serwerów; jest przykładowe. Jest bardzo ważne nie spacje widoczne między parametrami.)|Brak|
|Program Exchange|"Do programu Exchange;<br /><br /> MAPILEVEL = *folderpath*;<br /><br /> [TYPEM = {0 &AMP;#124; 1};]<br /><br /> [Profil = *profilu*;]<br /><br /> [PWD = *hasło*;]<br /><br /> [BAZA DANYCH = `database`;] "|*"dysku*:\\\ *ścieżki*\\\ *filename*. MDB"|

> [!NOTE]
>  Btrieve nie jest już obsługiwany począwszy od DAO 3.5.

Należy użyć podwójny ukośnik odwrotny (\\\\) w parametrach połączenia. Jeśli zmodyfikowano właściwości istniejącego połączenia przy użyciu `SetConnect`, następnie należy wywołać [RefreshLink](#refreshlink). Jeśli są inicjowanie przy użyciu właściwości połączenia `SetConnect`, należy nie wywołanie `RefreshLink`, ale najpierw należy wybrać to zrobić, Dodaj tabledef.

Jeśli hasło jest wymagana, ale nie podano, sterownik ODBC wyświetla logowania okna dialogowego po raz pierwszy uzyskano dostęp do tabeli i ponownie, jeśli połączenie jest zamknięte i otwarte ponownie.

Można ustawić parametry połączenia dla `CDaoTableDef` obiektu, podając źródło argument `Create` funkcja elementu członkowskiego. Możesz sprawdzić ustawienie, aby określić typ, ścieżki, identyfikator użytkownika, hasło lub źródła danych ODBC dla bazy danych. Aby uzyskać więcej informacji zobacz dokumentację dla określonego sterownika.

Aby uzyskać powiązane informacje zobacz temat "Connect Property" w Pomocy programu DAO.

##  <a name="setname"></a>  CDaoTableDef::SetName

Wywołaj tę funkcję elementu członkowskiego, aby ustawić nazwę użytkownika dla tabeli.

```
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Wskaźnik do wyrażenia ciągu, który określa nazwę tabeli.

### <a name="remarks"></a>Uwagi

Nazwa musi rozpoczynać się od litery i może zawierać maksymalnie 64 znaki. Może zawierać cyfry i znaki podkreślenia, ale nie może zawierać znaków interpunkcyjnych lub miejsca do magazynowania.

Aby uzyskać powiązane informacje zobacz temat "Nazwa właściwości" w Pomocy programu DAO.

##  <a name="setsourcetablename"></a>  CDaoTableDef::SetSourceTableName

Wywołaj tę funkcję elementu członkowskiego, aby określić nazwę dołączonej tabeli lub nazwę tabeli podstawowej, na którym `CDaoTableDef` obiektu jest oparta, zgodnie z jego lokalizacją w oryginalnym źródle danych.

```
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```

### <a name="parameters"></a>Parametry

*lpszSrcTableName*<br/>
Wskaźnik do wyrażenia ciągu, który określa nazwę tabeli w zewnętrznej bazie danych. Dla tabeli podstawowej, ustawienie to ciąg pusty ("").

### <a name="remarks"></a>Uwagi

Następnie należy wywołać [RefreshLink](#refreshlink). Ustawienie tej właściwości jest pusta dla tabeli podstawowej i odczytu/zapisu dla dołączonej tabeli lub obiektu, nie są dołączane do kolekcji.

Aby uzyskać powiązane informacje zobacz temat "SourceTableName Property" w Pomocy programu DAO.

##  <a name="setvalidationrule"></a>  CDaoTableDef::SetValidationRule

Wywołaj tę funkcję elementu członkowskiego, aby ustawić regułę sprawdzania poprawności dla tabledef.

```
void SetValidationRule(LPCTSTR lpszValidationRule);
```

### <a name="parameters"></a>Parametry

*lpszValidationRule*<br/>
Wskaźnik do wyrażenia ciągu, która weryfikuje operacji.

### <a name="remarks"></a>Uwagi

Reguły sprawdzania poprawności są używane w operacji aktualizowania. Jeśli tabledef zawiera reguły sprawdzania poprawności, aktualizacje tego tabledef musi odpowiadać wstępnie zdefiniowanych kryteriów, przed zmianą danych. Jeśli zmiana niezgodny z kryteriami, wyjątek zawierający tekst [GetValidationText](#getvalidationtext) jest wyświetlana.

Walidacja jest obsługiwana tylko dla baz danych, które używają aparatu bazy danych Microsoft Jet. Wyrażenie nie może odwoływać się do funkcji zdefiniowanych przez użytkownika, domeny funkcje agregujące, funkcje agregacji lub zapytań. Reguły sprawdzania poprawności `CDaoTableDef` obiektu może odwoływać się do wielu pól, w tym obiekcie.

Na przykład dla pola o nazwie *hire_date* i *termination_date*, może być reguły sprawdzania poprawności:

[!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]

Aby uzyskać powiązane informacje zobacz temat "ValidationRule Property" w Pomocy programu DAO.

##  <a name="setvalidationtext"></a>  CDaoTableDef::SetValidationText

Wywołaj tę funkcję elementu członkowskiego, aby ustawić tekst wyjątku reguły sprawdzania poprawności `CDaoTableDef` obiektu z podstawowej tabeli obsługiwane przez aparat bazy danych Microsoft Jet.

```
void SetValidationText(LPCTSTR lpszValidationText);
```

### <a name="parameters"></a>Parametry

*lpszValidationText*<br/>
Wskaźnik do wyrażenia ciągu, który określa tekst wyświetlany, jeśli dane wprowadzone jest nieprawidłowy.

### <a name="remarks"></a>Uwagi

Nie można ustawić tekst sprawdzania poprawności dołączonej tabeli.

Aby uzyskać powiązane informacje zobacz temat "Property komunikat" w Pomocy programu DAO.

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)<br/>
[Klasa CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)
