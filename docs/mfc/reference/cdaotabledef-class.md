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
ms.openlocfilehash: 61e16ef2998f2b807e96368973711dfdb31dcc45
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223125"
---
# <a name="cdaotabledef-class"></a>Klasa CDaoTableDef

Reprezentuje przechowywaną definicję tabeli bazowej lub dołączonej tabeli.

## <a name="syntax"></a>Składnia

```
class CDaoTableDef : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoTableDef::CDaoTableDef](#cdaotabledef)|Konstruuje `CDaoTableDef` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDaoTableDef:: Append](#append)|Dodaje nową tabelę do bazy danych.|
|[CDaoTableDef:: Update](#canupdate)|Zwraca wartość różną od zera, jeśli tabela może zostać zaktualizowana (definicje pól lub właściwości tabeli można modyfikować).|
|[CDaoTableDef:: Close](#close)|Zamyka otwarty tabledef.|
|[CDaoTableDef:: Create](#create)|Tworzy tabelę, którą można dodać do bazy danych przy użyciu funkcji [Dołącz](#append).|
|[CDaoTableDef:: onfield](#createfield)|Wywołuje się, by utworzyć pole dla tabeli.|
|[CDaoTableDef:: isindex](#createindex)|Wywołuje się, by utworzyć indeks dla tabeli.|
|[CDaoTableDef::D eleteField](#deletefield)|Wywołuje się, by usunąć pole z tabeli.|
|[CDaoTableDef::D eleteIndex](#deleteindex)|Wywołuje się, by usunąć indeks z tabeli.|
|[CDaoTableDef:: GetAttributes](#getattributes)|Zwraca wartość, która wskazuje co najmniej jedną charakterystykę `CDaoTableDef` obiektu.|
|[CDaoTableDef:: GetConnect](#getconnect)|Zwraca wartość, która zawiera informacje o źródle tabeli.|
|[CDaoTableDef::GetDateCreated](#getdatecreated)|Zwraca datę i godzinę utworzenia bazowej tabeli bazowej `CDaoTableDef` obiektu.|
|[CDaoTableDef::GetDateLastUpdated](#getdatelastupdated)|Zwraca datę i godzinę ostatniej zmiany dokonanej w projekcie tabeli podstawowej.|
|[CDaoTableDef::GetFieldCount](#getfieldcount)|Zwraca wartość reprezentującą liczbę pól w tabeli.|
|[CDaoTableDef:: GetFieldInfo](#getfieldinfo)|Zwraca określone rodzaje informacji o polach w tabeli.|
|[CDaoTableDef::GetIndexCount](#getindexcount)|Zwraca liczbę indeksów dla tabeli.|
|[CDaoTableDef::GetIndexInfo](#getindexinfo)|Zwraca określone rodzaje informacji o indeksach tabeli.|
|[CDaoTableDef:: GetName](#getname)|Zwraca zdefiniowaną przez użytkownika nazwę tabeli.|
|[CDaoTableDef::GetRecordCount](#getrecordcount)|Zwraca liczbę rekordów w tabeli.|
|[CDaoTableDef::GetSourceTableName](#getsourcetablename)|Zwraca wartość określającą nazwę dołączonej tabeli w źródłowej bazie danych.|
|[CDaoTableDef:: GetValidationRule](#getvalidationrule)|Zwraca wartość, która sprawdza poprawność danych w polu w miarę ich zmiany lub dodania do tabeli.|
|[CDaoTableDef::GetValidationText](#getvalidationtext)|Zwraca wartość określającą tekst komunikatu wyświetlanego przez aplikację, jeśli wartość obiektu Field nie spełnia określonej reguły walidacji.|
|[CDaoTableDef:: IsOpen](#isopen)|Zwraca wartość różną od zera, jeśli tabela jest otwarta.|
|[CDaoTableDef:: Open](#open)|Otwiera istniejące tabledef przechowywane w kolekcji TableDef's bazy danych.|
|[CDaoTableDef::RefreshLink](#refreshlink)|Aktualizuje informacje o połączeniu dla dołączonej tabeli.|
|[CDaoTableDef:: SetAttributes](#setattributes)|Ustawia wartość wskazującą co najmniej jedną charakterystykę `CDaoTableDef` obiektu.|
|[CDaoTableDef:: SetConnect](#setconnect)|Ustawia wartość, która zawiera informacje o źródle tabeli.|
|[CDaoTableDef:: SetName](#setname)|Ustawia nazwę tabeli.|
|[CDaoTableDef::SetSourceTableName](#setsourcetablename)|Ustawia wartość określającą nazwę dołączonej tabeli w źródłowej bazie danych.|
|[CDaoTableDef:: setvalidationrule](#setvalidationrule)|Ustawia wartość, która sprawdza poprawność danych w polu w miarę ich zmiany lub dodania do tabeli.|
|[CDaoTableDef::SetValidationText](#setvalidationtext)|Ustawia wartość określającą tekst komunikatu wyświetlanego przez aplikację, jeśli wartość obiektu Field nie spełnia określonej reguły walidacji.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDaoTableDef:: m_pDAOTableDef](#m_pdaotabledef)|Wskaźnik do interfejsu DAO bazowego obiektu tabledef.|
|[CDaoTableDef:: m_pDatabase](#m_pdatabase)|Źródłowa baza danych dla tej tabeli.|

## <a name="remarks"></a>Uwagi

Każdy obiekt bazy danych DAO utrzymuje kolekcję o nazwie TableDefs, która zawiera wszystkie zapisane obiekty DAO tabledef.

Będziesz manipulować definicją tabeli przy użyciu `CDaoTableDef` obiektu. Możesz na przykład:

- Przejrzyj strukturę pól i indeksów każdej lokalnej, dołączonej lub zewnętrznej tabeli w bazie danych.

- Wywołaj `SetConnect` `SetSourceTableName` funkcje i dla dołączonych tabel i Użyj `RefreshLink` funkcji składowej do aktualizowania połączeń z dołączonymi tabelami.

- Wywołaj `CanUpdate` funkcję członkowską, aby określić, czy można edytować definicje pól w tabeli.

- Pobieranie lub Ustawianie warunków walidacji przy `GetValidationRule` użyciu `SetValidationRule` funkcji i i `GetValidationText` `SetValidationText` .

- Użyj `Open` funkcji członkowskiej, aby utworzyć obiekt Table-, dynamiczny lub typu Snapshot `CDaoRecordset` .

    > [!NOTE]
    >  Klasy bazy danych DAO różnią się od klas baz danych MFC opartych na Open Database Connectivity (ODBC). Wszystkie nazwy klas baz danych DAO mają prefiks "CDao". Nadal można uzyskać dostęp do źródeł danych ODBC przy użyciu klas DAO; klasy DAO zazwyczaj oferują znakomite możliwości, ponieważ są specyficzne dla aparatu bazy danych Microsoft Jet.

### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>Aby użyć obiektów tabledef do pracy z istniejącą tabelą lub utworzyć nową tabelę

1. We wszystkich przypadkach najpierw konstruuje `CDaoTableDef` obiekt, dostarczając wskaźnik do obiektu [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) , do którego należy tabela.

1. Następnie wykonaj następujące czynności, w zależności od tego, co chcesz zrobić:

   - Aby użyć istniejącej zapisanej tabeli, wywołaj funkcję [otwierającego](#open) elementu członkowskiego obiektu tabledef, podając nazwę zapisanej tabeli.

   - Aby utworzyć nową tabelę, wywołaj funkcję [tworzenia](#create) elementu członkowskiego obiektu tabledef, podając nazwę tabeli. Wywołaj metody [onfield](#createfield) i [onindex](#createindex) , aby dodać pola i indeksy do tabeli.

   - Zadzwoń do [dołączenia](#append) , aby zapisać tabelę przez dołączenie jej do kolekcji TableDefs bazy danych. `Create`umieszcza tabledef w stanie otwartym, dlatego po wywołaniu `Create` nie jest wywoływana `Open` .

        > [!TIP]
        >  Najprostszym sposobem tworzenia zapisanych tabel jest ich utworzenie i zapisanie ich w bazie danych przy użyciu programu Microsoft Access. Następnie możesz otworzyć i używać ich w kodzie MFC.

Aby użyć obiektu tabledef, który został otwarty lub utworzony, Utwórz i Otwórz `CDaoRecordset` obiekt, określając nazwę tabledef z `dbOpenTable` wartością w parametrze *nOpenType* .

Aby użyć obiektu tabledef do utworzenia `CDaoRecordset` obiektu, zazwyczaj tworzy się lub otwiera tabledef, jak opisano powyżej, a następnie konstruuje obiekt zestawu rekordów, przekazując wskaźnik do obiektu tabledef podczas wywoływania [CDaoRecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open). Tabledef musi być w stanie otwartym. Aby uzyskać więcej informacji, zobacz Klasa [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Po zakończeniu korzystania z obiektu tabledef należy wywołać jego funkcję [zamykającego](../../mfc/reference/cdaorecordset-class.md#close) elementu członkowskiego. następnie Zniszcz obiekt tabledef.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CDaoTableDef`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

## <a name="cdaotabledefappend"></a><a name="append"></a>CDaoTableDef:: Append

Wywołaj tę funkcję elementu członkowskiego po wywołaniu metody [Create](#create) , aby utworzyć nowy obiekt tabledef, aby zapisać tabledef w bazie danych.

```
virtual void Append();
```

### <a name="remarks"></a>Uwagi

Funkcja dołącza obiekt do kolekcji TableDefs bazy danych. Można użyć tabledef jako obiektu tymczasowego podczas definiowania go bez dołączania, ale jeśli chcesz go zapisać i użyć, musisz wywołać metodę `Append` .

> [!NOTE]
> Jeśli podjęto próbę dołączenia nienazwanego tabledef (zawierającego ciąg o wartości null lub pusty), MFC zgłasza wyjątek.

Aby uzyskać powiązane informacje, zobacz temat "Metoda dołączania" w pomocy DAO.

## <a name="cdaotabledefcanupdate"></a><a name="canupdate"></a>CDaoTableDef:: Update

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy definicja tabeli bazowej `CDaoTableDef` obiektu może zostać zmieniona.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli struktura tabeli (schemat) może być modyfikowana (Dodawanie lub usuwanie pól i indeksów), w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślnie nowo utworzona tabela źródłowa `CDaoTableDef` obiektu może zostać zaktualizowana i nie można zaktualizować dołączonej tabeli powiązanej z `CDaoTableDef` obiektem. `CDaoTableDef`Obiekt może być aktualizowalny, nawet jeśli zestaw rekordów nie zostanie aktualizowalny.

Aby uzyskać powiązane informacje, zobacz temat "Aktualizowalna właściwość" w pomocy DAO.

## <a name="cdaotabledefcdaotabledef"></a><a name="cdaotabledef"></a>CDaoTableDef::CDaoTableDef

Konstruuje `CDaoTableDef` obiekt.

```
CDaoTableDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Parametry

*pDatabase*<br/>
Wskaźnik do obiektu [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) .

### <a name="remarks"></a>Uwagi

Po utworzeniu obiektu należy wywołać funkcję [tworzenia](#create) lub [otwierania](#open) elementu członkowskiego. Po zakończeniu pracy z obiektem należy wywołać jego funkcję [zamykającego](#close) elementu członkowskiego i zniszczyć `CDaoTableDef` obiekt.

## <a name="cdaotabledefclose"></a><a name="close"></a>CDaoTableDef:: Close

Wywołaj tę funkcję elementu członkowskiego, aby zamknąć i zwolnić obiekt tabledef.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Zwykle po wywołaniu należy `Close` usunąć obiekt tabledef, jeśli został on przydzielony przy użyciu **`new`** .

Możesz wywołać operację [Otwórz](#open) ponownie po wywołaniu `Close` . Umożliwia to ponowne użycie obiektu tabledef.

Aby uzyskać powiązane informacje, zobacz temat "metoda Close" w pomocy DAO.

## <a name="cdaotabledefcreate"></a><a name="create"></a>CDaoTableDef:: Create

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć nową zapisaną tabelę.

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
Wartość odpowiadająca charakterystyce tabeli reprezentowanej przez obiekt tabledef. Można użyć bitowego lub do łączenia dowolnej z następujących stałych:

|Stały|Opis|
|--------------|-----------------|
|`dbAttachExclusive`|W przypadku baz danych korzystających z aparatu bazy danych Microsoft Jet wskazuje, że tabela jest dołączoną tabelą otwartą do wyłącznego użytku.|
|`dbAttachSavePWD`|W przypadku baz danych korzystających z aparatu bazy danych Microsoft Jet wskazuje, że identyfikator użytkownika i hasło do dołączonej tabeli są zapisywane wraz z informacjami o połączeniu.|
|`dbSystemObject`|Wskazuje, że tabela jest tabelą systemową dostarczoną przez aparat bazy danych Microsoft Jet.|
|`dbHiddenObject`|Wskazuje, że tabela jest ukrytą tabelą dostarczoną przez aparat bazy danych Microsoft Jet.|

*lpszSrcTable*<br/>
Wskaźnik do ciągu zawierającego nazwę tabeli źródłowej. Domyślnie ta wartość jest inicjowana jako wartość NULL.

*lpszConnect*<br/>
Wskaźnik do ciągu zawierającego domyślne parametry połączenia. Domyślnie ta wartość jest inicjowana jako wartość NULL.

### <a name="remarks"></a>Uwagi

Po nazwie tabledef można następnie wywołać [dołączenie](#append) w celu zapisania tabledef w kolekcji TableDefs bazy danych. Po wywołaniu `Append` tabledef jest w stanie otwartym i można go użyć do utworzenia obiektu [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) .

Aby uzyskać powiązane informacje, zobacz temat "Metoda CreateTableDef" w pomocy DAO.

## <a name="cdaotabledefcreatefield"></a><a name="createfield"></a>CDaoTableDef:: onfield

Wywołaj tę funkcję elementu członkowskiego, aby dodać pole do tabeli.

```cpp
void CreateField(
    LPCTSTR lpszName,
    short nType,
    long lSize,
    long lAttributes = 0);

void CreateField(CDaoFieldInfo& fieldinfo);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Wskaźnik do wyrażenia ciągu, który określa nazwę tego pola.

*Npowiadomienia*<br/>
Wartość wskazująca typ danych pola. Ustawienie może być jedną z następujących wartości:

|Typ|Rozmiar (w bajtach)|Opis|
|----------|--------------------|-----------------|
|`dbBoolean`|1 bajt|LOGICZNA|
|`dbByte`|BYTE|
|`dbInteger`|2|int|
|`dbLong`|4|długi|
|`dbCurrency`|8|Waluta ( [COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|float|
|`dbDouble`|8|double|
|`dbDate`|8|Data/godzina ( [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Tekst ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Long Binary (obiekt OLE), [CLongBinary](../../mfc/reference/clongbinary-class.md) lub [CByteArray](../../mfc/reference/cbytearray-class.md)|
|`dbMemo`|0|Memo ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|

*lSize*<br/>
Wartość wskazująca maksymalny rozmiar (w bajtach) pola, które zawiera tekst, lub ustalony rozmiar pola, który zawiera wartości tekstowe lub liczbowe. Parametr *lSize* jest ignorowany dla wszystkich pól tekstowych i.

*lAttributes*<br/>
Wartość odpowiadająca charakterystyce pola i, która może być łączona przy użyciu bitowej lub.

|Stały|Opis|
|--------------|-----------------|
|`dbFixedField`|Rozmiar pola jest stały (domyślnie dla pól liczbowych).|
|`dbVariableField`|Rozmiar pola to zmienna (tylko pola tekstowe).|
|`dbAutoIncrField`|Wartość pola dla nowych rekordów jest automatycznie zwiększana do unikatowej długiej liczby całkowitej, której nie można zmienić. Obsługiwane tylko w przypadku tabel bazy danych Microsoft Jet.|
|`dbUpdatableField`|Wartość pola można zmienić.|
|`dbDescending`|Pole jest sortowane w kolejności malejącej (Z-A lub 100-0) (dotyczy tylko obiektu Field w kolekcji Fields obiektu index). Jeśli ta stała zostanie pominięta, pole jest sortowane w kolejności rosnącej (A-Z lub 0-100) (wartość domyślna).|

*FieldInfo*<br/>
Odwołanie do struktury [CDaoFieldInfo —](../../mfc/reference/cdaofieldinfo-structure.md) .

### <a name="remarks"></a>Uwagi

`DAOField`Obiekt (OLE) jest tworzony i dołączany do kolekcji Fields `DAOTableDef` obiektu (OLE). Oprócz użycia do badania właściwości obiektu, można również użyć `CDaoFieldInfo` do konstruowania parametru wejściowego do tworzenia nowych pól w tabledef. Pierwsza wersja `CreateField` jest prostsza do użycia, ale jeśli potrzebujesz bardziej precyzyjnej kontroli, możesz użyć drugiej wersji `CreateField` , która przyjmuje `CDaoFieldInfo` parametr.

Jeśli używasz wersji, `CreateField` która przyjmuje `CDaoFieldInfo` parametr, należy starannie ustawić każdy z następujących elementów członkowskich `CDaoFieldInfo` struktury:

- `m_strName`

- `m_nType`

- `m_lSize`

- `m_lAttributes`

- `m_bAllowZeroLength`

Pozostałe elementy członkowskie elementu `CDaoFieldInfo` powinny mieć wartość **0**, false lub być pustym ciągiem odpowiednio dla elementu członkowskiego lub `CDaoException` mogą wystąpić.

Aby uzyskać powiązane informacje, zobacz temat "Metoda onfield" w pomocy DAO.

## <a name="cdaotabledefcreateindex"></a><a name="createindex"></a>CDaoTableDef:: isindex

Wywołaj tę funkcję, aby dodać indeks do tabeli.

```cpp
void CreateIndex(CDaoIndexInfo& indexinfo);
```

### <a name="parameters"></a>Parametry

*indexinfo*<br/>
Odwołanie do struktury [CDaoIndexInfo —](../../mfc/reference/cdaoindexinfo-structure.md) .

### <a name="remarks"></a>Uwagi

Indeksy określają kolejność rekordów, do których można uzyskać dostęp z tabel bazy danych i czy rekordy są akceptowane. Indeksy zapewniają również wydajny dostęp do danych.

Nie ma potrzeby tworzenia indeksów dla tabel, ale w dużych, nieindeksowanych tabelach, uzyskiwania dostępu do określonego rekordu lub tworzenia zestawu rekordów może zająć dużo czasu. Z drugiej strony Tworzenie zbyt wielu indeksów spowalnia operacje aktualizacji, dołączania i usuwania, ponieważ wszystkie indeksy są automatycznie aktualizowane. Należy wziąć pod uwagę te czynniki podczas decydowania o tworzeniu indeksów.

Należy ustawić następujące elementy członkowskie `CDaoIndexInfo` struktury:

- `m_strName`Należy podać nazwę.

- `m_pFieldInfos`Musi wskazywać na tablicę `CDaoIndexFieldInfo` struktur.

- `m_nFields`Należy określić liczbę pól w tablicy `CDaoFieldInfo` struktur.

Pozostałe elementy członkowskie zostaną zignorowane, jeśli ustawiono wartość FALSE. Ponadto `m_lDistinctCount` element członkowski jest ignorowany podczas tworzenia indeksu.

## <a name="cdaotabledefdeletefield"></a><a name="deletefield"></a>CDaoTableDef::D eleteField

Wywołaj tę funkcję elementu członkowskiego, aby usunąć pole i uniemożliwić dostęp do niego.

```cpp
void DeleteField(LPCTSTR lpszName);
void DeleteField(int nIndex);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Wskaźnik do wyrażenia ciągu, który jest nazwą istniejącego pola.

*nIndex*<br/>
Indeks pola w kolekcji pól (zero) tabeli dla wyszukiwania według indeksu.

### <a name="remarks"></a>Uwagi

Można użyć tej funkcji elementu członkowskiego na nowym obiekcie, który nie został dołączony do bazy danych lub gdy [Aktualizacja](#canupdate) zwraca wartość różną od zera.

Aby uzyskać powiązane informacje, zobacz temat "Delete Method" w pomocy DAO.

## <a name="cdaotabledefdeleteindex"></a><a name="deleteindex"></a>CDaoTableDef::D eleteIndex

Wywołaj tę funkcję elementu członkowskiego, aby usunąć indeks w źródłowej tabeli.

```cpp
void DeleteIndex(LPCTSTR lpszName);
void DeleteIndex(int nIndex);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Wskaźnik do wyrażenia ciągu, który jest nazwą istniejącego indeksu.

*nIndex*<br/>
Indeks tablicy obiektu index w kolekcji TableDefs na podstawie zera w bazie danych dla wyszukiwania według indeksu.

### <a name="remarks"></a>Uwagi

Można użyć tej funkcji elementu członkowskiego na nowym obiekcie, który nie został dołączony do bazy danych lub gdy [Aktualizacja](#canupdate) zwraca wartość różną od zera.

Aby uzyskać powiązane informacje, zobacz temat "Delete Method" w pomocy DAO.

## <a name="cdaotabledefgetattributes"></a><a name="getattributes"></a>CDaoTableDef:: GetAttributes

Dla `CDaoTableDef` obiektu zwracana wartość określa charakterystykę tabeli reprezentowanej przez `CDaoTableDef` obiekt i może być sumą tych stałych:

```
long GetAttributes();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość, która wskazuje co najmniej jedną charakterystykę `CDaoTableDef` obiektu.

### <a name="remarks"></a>Uwagi

|Stały|Opis|
|--------------|-----------------|
|`dbAttachExclusive`|W przypadku baz danych korzystających z aparatu bazy danych Microsoft Jet wskazuje, że tabela jest dołączoną tabelą otwartą do wyłącznego użytku.|
|`dbAttachSavePWD`|W przypadku baz danych korzystających z aparatu bazy danych Microsoft Jet wskazuje, że identyfikator użytkownika i hasło do dołączonej tabeli są zapisywane wraz z informacjami o połączeniu.|
|`dbSystemObject`|Wskazuje, że tabela jest tabelą systemową dostarczoną przez aparat bazy danych Microsoft Jet.|
|`dbHiddenObject`|Wskazuje, że tabela jest ukrytą tabelą dostarczoną przez aparat bazy danych Microsoft Jet.|
|`dbAttachedTable`|Wskazuje, że tabela jest dołączoną tabelą z bazy danych innej niż ODBC, takiej jak baza danych programu Paradox.|
|`dbAttachedODBC`|Wskazuje, że tabela jest dołączoną tabelą z bazy danych ODBC, takiej jak Microsoft SQL Server.|

Tabela systemowa jest tabelą utworzoną przez aparat bazy danych Microsoft Jet, aby zawierała różne informacje wewnętrzne.

Ukryta tabela jest tabelą utworzoną do tymczasowego użytku przez aparat bazy danych Microsoft Jet.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość Attributes" w pomocy DAO.

## <a name="cdaotabledefgetconnect"></a><a name="getconnect"></a>CDaoTableDef:: GetConnect

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać parametry połączenia dla źródła danych.

```
CString GetConnect();
```

### <a name="return-value"></a>Wartość zwracana

`CString`Obiekt zawierający ścieżkę i typ bazy danych dla tabeli.

### <a name="remarks"></a>Uwagi

Dla `CDaoTableDef` obiektu, który reprezentuje załączoną tabelę, `CString` obiekt składa się z jednej lub dwóch części (specyfikatora typu bazy danych i ścieżki do bazy danych).

Ścieżka, jak pokazano w poniższej tabeli, to pełna ścieżka do katalogu zawierającego pliki bazy danych i musi być poprzedzona identyfikatorem "DATABASE =". W niektórych przypadkach (podobnie jak w przypadku baz danych Microsoft Jet i Microsoft Excel) określona nazwa pliku jest uwzględniona w argumencie ścieżki bazy danych.

Tabela w [CDaoTableDef:: SetConnect](#setconnect) pokazuje możliwe typy baz danych i ich odpowiednie specyfikatory i ścieżki bazy danych:

W przypadku tabel bazowych bazy danych Microsoft Jet specyfikator jest pustym ciągiem ("").

Jeśli hasło jest wymagane, ale nie podano, sterownik ODBC wyświetla okno dialogowe logowania przy pierwszym dostępie do tabeli, a następnie ponownie, jeśli połączenie zostanie zamknięte i otwarte. Jeśli dołączona tabela ma `dbAttachSavePWD` atrybut, monit logowania nie będzie wyświetlany, gdy tabela zostanie ponownie otwarta.

Aby uzyskać powiązane informacje, zobacz temat "Connect Property" w pomocy DAO.

## <a name="cdaotabledefgetdatecreated"></a><a name="getdatecreated"></a>CDaoTableDef::GetDateCreated

Wywołaj tę funkcję, aby określić datę i godzinę utworzenia tabeli powiązanej z `CDaoTableDef` obiektem.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Wartość zwracana

Wartość zawierająca datę i godzinę utworzenia tabeli bazowej `CDaoTableDef` obiektu.

### <a name="remarks"></a>Uwagi

Ustawienia daty i godziny są wyprowadzane z komputera, na którym utworzono lub ostatnio Zaktualizowano tabelę bazową. W środowisku wielodostępnym użytkownicy powinni uzyskać te ustawienia bezpośrednio z serwera plików, aby uniknąć rozbieżności; oznacza to, że wszyscy klienci powinni używać "standardowego" czasu źródła (np. z jednego serwera).

Aby uzyskać powiązane informacje, zobacz temat "DateCreated, LastUpdated Properties" w pomocy DAO.

## <a name="cdaotabledefgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoTableDef::GetDateLastUpdated

Wywołaj tę funkcję, aby określić datę i godzinę `CDaoTableDef` ostatniej aktualizacji tabeli.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Wartość zwracana

Wartość, która zawiera datę i godzinę ostatniej aktualizacji tabeli źródłowej `CDaoTableDef` obiektu.

### <a name="remarks"></a>Uwagi

Ustawienia daty i godziny są wyprowadzane z komputera, na którym utworzono lub ostatnio Zaktualizowano tabelę bazową. W środowisku wielodostępnym użytkownicy powinni uzyskać te ustawienia bezpośrednio z serwera plików, aby uniknąć rozbieżności; oznacza to, że wszyscy klienci powinni używać "standardowego" czasu źródła (np. z jednego serwera).

Aby uzyskać powiązane informacje, zobacz temat "DateCreated, LastUpdated Properties" w pomocy DAO.

## <a name="cdaotabledefgetfieldcount"></a><a name="getfieldcount"></a>CDaoTableDef::GetFieldCount

Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę pól zdefiniowanych w tabeli.

```
short GetFieldCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba pól w tabeli.

### <a name="remarks"></a>Uwagi

Jeśli wartość wynosi 0, w kolekcji nie ma żadnych obiektów.

Aby uzyskać powiązane informacje, zobacz temat "Count Property" w pomocy DAO.

## <a name="cdaotabledefgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoTableDef:: GetFieldInfo

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać różne rodzaje informacji dotyczących pola zdefiniowanego w tabledef.

```cpp
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
Indeks obiektu Field w kolekcji pól na podstawie zerowej tabeli dla wyszukiwania według indeksu.

*FieldInfo*<br/>
Odwołanie do struktury [CDaoFieldInfo —](../../mfc/reference/cdaofieldinfo-structure.md) .

*dwInfoOptions*<br/>
Opcje określające, które informacje o polu pobrać. Dostępne opcje są wymienione tutaj wraz z tym, co powodują, że funkcja zwraca:

- `AFX_DAO_PRIMARY_INFO`Wartooć Nazwa, typ, rozmiar, atrybuty. Użyj tej opcji, aby uzyskać najszybszą wydajność.

- `AFX_DAO_SECONDARY_INFO`Informacje podstawowe, plus: pozycja porządkowa, wymagane, Zezwalaj na zerową długość, kolejność sortowania, Nazwa obca, pole źródłowe, tabela źródłowa

- `AFX_DAO_ALL_INFO`Informacje podstawowe i pomocnicze oraz: reguła walidacji, tekst walidacji, wartość domyślna

*lpszName*<br/>
Wskaźnik do nazwy obiektu pola, dla wyszukiwania według nazwy. Nazwa jest ciągiem z maksymalnie 64 znaków, które jednoznacznie nazywają pole.

### <a name="remarks"></a>Uwagi

Jedna wersja funkcji pozwala wyszukiwać pola według indeksu. Inna wersja pozwala wyszukiwać pola według nazwy.

Aby uzyskać opis zwracanych informacji, zobacz strukturę [CDaoFieldInfo —](../../mfc/reference/cdaofieldinfo-structure.md) . Ta struktura zawiera elementy członkowskie, które odpowiadają elementom informacji wymienionych powyżej w opisie *dwInfoOptions*. Jeśli zażądasz informacji na jednym poziomie, uzyskasz również informacje na temat wszystkich wcześniejszych poziomów.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość Attributes" w pomocy DAO.

## <a name="cdaotabledefgetindexcount"></a><a name="getindexcount"></a>CDaoTableDef::GetIndexCount

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać liczbę indeksów dla tabeli.

```
short GetIndexCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba indeksów dla tabeli.

### <a name="remarks"></a>Uwagi

Jeśli wartość wynosi 0, w kolekcji nie ma indeksów.

Aby uzyskać powiązane informacje, zobacz temat "Count Property" w pomocy DAO.

## <a name="cdaotabledefgetindexinfo"></a><a name="getindexinfo"></a>CDaoTableDef::GetIndexInfo

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać różne rodzaje informacji o indeksie zdefiniowanym w tabledef.

```cpp
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
Indeks liczbowy obiektu index w kolekcji indeksów opartych na zero tabeli dla wyszukiwania według jego pozycji w kolekcji.

*indexinfo*<br/>
Odwołanie do struktury [CDaoIndexInfo —](../../mfc/reference/cdaoindexinfo-structure.md) .

*dwInfoOptions*<br/>
Opcje określające, które informacje o indeksie mają zostać pobrane. Dostępne opcje są wymienione tutaj wraz z tym, co powodują, że funkcja zwraca:

- `AFX_DAO_PRIMARY_INFO`Nazwa, informacje o polu, pola. Użyj tej opcji, aby uzyskać najszybszą wydajność.

- `AFX_DAO_SECONDARY_INFO`Informacje podstawowe oraz: podstawowe, unikatowe, klastrowane, Ignoruj wartości null, wymagane, obce

- `AFX_DAO_ALL_INFO`Informacje podstawowe i pomocnicze oraz: liczność unikatowych

*lpszName*<br/>
Wskaźnik do nazwy obiektu indeksu dla wyszukiwania według nazwy.

### <a name="remarks"></a>Uwagi

Jedna wersja funkcji pozwala wyszukiwać indeks według pozycji w kolekcji. Inna wersja pozwala wyszukiwać indeks według nazwy.

Aby uzyskać opis zwracanych informacji, zobacz strukturę [CDaoIndexInfo —](../../mfc/reference/cdaoindexinfo-structure.md) . Ta struktura zawiera elementy członkowskie, które odpowiadają elementom informacji wymienionych powyżej w opisie *dwInfoOptions*. Jeśli zażądasz informacji na jednym poziomie, uzyskasz również informacje na temat wszystkich wcześniejszych poziomów.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość Attributes" w pomocy DAO.

## <a name="cdaotabledefgetname"></a><a name="getname"></a>CDaoTableDef:: GetName

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać zdefiniowaną przez użytkownika nazwę tabeli źródłowej.

```
CString GetName();
```

### <a name="return-value"></a>Wartość zwracana

Zdefiniowana przez użytkownika nazwa tabeli.

### <a name="remarks"></a>Uwagi

Ta nazwa rozpoczyna się od litery i może zawierać maksymalnie 64 znaków. Może zawierać cyfry i znaki podkreślenia, ale nie może zawierać znaków interpunkcyjnych ani spacji.

Aby uzyskać powiązane informacje, zobacz temat "Nazwa właściwości" w pomocy DAO.

## <a name="cdaotabledefgetrecordcount"></a><a name="getrecordcount"></a>CDaoTableDef::GetRecordCount

Wywołaj tę funkcję elementu członkowskiego, aby dowiedzieć się, ile rekordów znajduje się w `CDaoTableDef` obiekcie.

```
long GetRecordCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba rekordów, do których można uzyskać dostęp w obiekcie tabledef.

### <a name="remarks"></a>Uwagi

Wywołanie `GetRecordCount` dla obiektu typu tabeli `CDaoTableDef` odzwierciedla przybliżoną liczbę rekordów w tabeli i jest modyfikowane natychmiast po dodaniu i usunięciu rekordów tabeli. Wycofane transakcje będą wyświetlane jako część liczby rekordów do momentu wywołania [CDaoWorkspace:: CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase). `CDaoTableDef`Obiekt bez rekordów ma ustawienie właściwości liczba rekordów równą 0. Podczas pracy z dołączonymi tabelami lub bazami danych ODBC `GetRecordCount` zawsze zwraca-1.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość RecordCount" w pomocy DAO.

## <a name="cdaotabledefgetsourcetablename"></a><a name="getsourcetablename"></a>CDaoTableDef::GetSourceTableName

Wywołaj tę funkcję elementu członkowskiego, aby pobrać nazwę dołączonej tabeli w źródłowej bazie danych.

```
CString GetSourceTableName();
```

### <a name="return-value"></a>Wartość zwracana

`CString`Obiekt, który określa nazwę źródła dołączonej tabeli lub pusty ciąg, jeśli natywna tabela danych.

### <a name="remarks"></a>Uwagi

Dołączona tabela jest tabelą w innej bazie danych połączonej z bazą danych programu Microsoft Jet. Dane dla dołączonych tabel pozostają w zewnętrznej bazie danych, gdzie mogą być przetwarzane przez inne aplikacje.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość SourceTableName" w pomocy DAO.

## <a name="cdaotabledefgetvalidationrule"></a><a name="getvalidationrule"></a>CDaoTableDef:: GetValidationRule

Wywołaj tę funkcję elementu członkowskiego, aby pobrać regułę walidacji dla elementu tabledef.

```
CString GetValidationRule();
```

### <a name="return-value"></a>Wartość zwracana

`CString`Obiekt, który sprawdza poprawność danych w polu w miarę ich zmiany lub dodania do tabeli.

### <a name="remarks"></a>Uwagi

Reguły walidacji są używane w połączeniu z operacjami aktualizacji. Jeśli tabledef zawiera regułę walidacji, aktualizacje tego tabledef muszą pasować do wstępnie określonych kryteriów przed zmianą danych. Jeśli zmiana nie jest zgodna z kryteriami, zgłaszany jest wyjątek zawierający wartość [GetValidationText](#getvalidationtext) . Dla `CDaoTableDef` obiektu `CString` jest to tylko do odczytu dla dołączonej tabeli i odczytu/zapisu dla tabeli podstawowej.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość ValidationRule" w pomocy DAO.

## <a name="cdaotabledefgetvalidationtext"></a><a name="getvalidationtext"></a>CDaoTableDef::GetValidationText

Wywołaj tę funkcję, aby pobrać ciąg, który ma być wyświetlany, gdy użytkownik wprowadzi dane, które nie pasują do reguły walidacji.

```
CString GetValidationText();
```

### <a name="return-value"></a>Wartość zwracana

`CString`Obiekt, który określa tekst wyświetlany, gdy użytkownik wprowadzi dane, które nie pasują do reguły walidacji.

### <a name="remarks"></a>Uwagi

Dla `CDaoTableDef` obiektu `CString` jest to tylko do odczytu dla dołączonej tabeli i odczytu/zapisu dla tabeli podstawowej.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość ValidationText" w pomocy DAO.

## <a name="cdaotabledefisopen"></a><a name="isopen"></a>CDaoTableDef:: IsOpen

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy `CDaoTableDef` obiekt jest aktualnie otwarty.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli `CDaoTableDef` obiekt jest otwarty; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

## <a name="cdaotabledefm_pdatabase"></a><a name="m_pdatabase"></a>CDaoTableDef:: m_pDatabase

Zawiera wskaźnik do obiektu [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) dla tej tabeli.

### <a name="remarks"></a>Uwagi

## <a name="cdaotabledefm_pdaotabledef"></a><a name="m_pdaotabledef"></a>CDaoTableDef:: m_pDAOTableDef

Zawiera wskaźnik do interfejsu OLE dla obiektu DAO tabledef, który jest `CDaoTableDef` obiektem.

### <a name="remarks"></a>Uwagi

Użyj tego wskaźnika, jeśli musisz bezpośrednio uzyskać dostęp do interfejsu DAO.

## <a name="cdaotabledefopen"></a><a name="open"></a>CDaoTableDef:: Open

Wywołaj tę funkcję elementu członkowskiego, aby otworzyć tabledef poprzednio zapisane w kolekcji TableDef's bazy danych.

```
virtual void Open(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Wskaźnik do ciągu, który określa nazwę tabeli.

### <a name="remarks"></a>Uwagi

## <a name="cdaotabledefrefreshlink"></a><a name="refreshlink"></a>CDaoTableDef::RefreshLink

Wywołaj tę funkcję elementu członkowskiego, aby zaktualizować informacje o połączeniu dla dołączonej tabeli.

```cpp
void RefreshLink();
```

### <a name="remarks"></a>Uwagi

Informacje o połączeniu dla dołączonej tabeli są zmieniane przez wywołanie metody [SetConnect](#setconnect) dla odpowiedniego `CDaoTableDef` obiektu, a następnie `RefreshLink` zaktualizowanie informacji przy użyciu funkcji członkowskiej. Po wywołaniu `RefreshLink` Właściwości dołączonej tabeli nie są zmieniane.

Aby wymusić modyfikację zmodyfikowanych informacji dotyczących połączenia, należy zamknąć wszystkie otwarte obiekty [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) oparte na tym tabledef.

Aby uzyskać powiązane informacje, zobacz temat "Metoda RefreshLink" w pomocy DAO.

## <a name="cdaotabledefsetattributes"></a><a name="setattributes"></a>CDaoTableDef:: SetAttributes

Ustawia wartość wskazującą co najmniej jedną charakterystykę `CDaoTableDef` obiektu.

```cpp
void SetAttributes(long lAttributes);
```

### <a name="parameters"></a>Parametry

*lAttributes*<br/>
Charakterystyki tabeli reprezentowanej przez `CDaoTableDef` obiekt i mogą być sumą tych stałych:

|Stały|Opis|
|--------------|-----------------|
|`dbAttachExclusive`|W przypadku baz danych korzystających z aparatu bazy danych Microsoft Jet wskazuje, że tabela jest dołączoną tabelą otwartą do wyłącznego użytku.|
|`dbAttachSavePWD`|W przypadku baz danych korzystających z aparatu bazy danych Microsoft Jet wskazuje, że identyfikator użytkownika i hasło do dołączonej tabeli są zapisywane wraz z informacjami o połączeniu.|
|`dbSystemObject`|Wskazuje, że tabela jest tabelą systemową dostarczoną przez aparat bazy danych Microsoft Jet.|
|`dbHiddenObject`|Wskazuje, że tabela jest ukrytą tabelą dostarczoną przez aparat bazy danych Microsoft Jet.|

### <a name="remarks"></a>Uwagi

Podczas ustawiania wielu atrybutów, można połączyć je, sumując odpowiednie stałe przy użyciu operatora bitowego lub. Ustawienie `dbAttachExclusive` dla niedołączonej tabeli powoduje utworzenie wyjątku. Łączenie następujących wartości powoduje także utworzenie wyjątku:

- **dbAttachExclusive &#124; dbAttachedODBC**

- **dbAttachSavePWD &#124; dołączona**

Aby uzyskać powiązane informacje, zobacz temat "Właściwość Attributes" w pomocy DAO.

## <a name="cdaotabledefsetconnect"></a><a name="setconnect"></a>CDaoTableDef:: SetConnect

Dla `CDaoTableDef` obiektu, który reprezentuje załączoną tabelę, obiekt String składa się z jednej lub dwóch części (specyfikatora typu bazy danych i ścieżki do bazy danych).

```cpp
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Parametry

*lpszConnect*<br/>
Wskaźnik do wyrażenia ciągu, który określa dodatkowe parametry do przekazania do ODBC lub instalowalnych sterowników ISAM.

### <a name="remarks"></a>Uwagi

Ścieżka, jak pokazano w poniższej tabeli, to pełna ścieżka do katalogu zawierającego pliki bazy danych i musi być poprzedzona identyfikatorem "DATABASE =". W niektórych przypadkach (podobnie jak w przypadku baz danych Microsoft Jet i Microsoft Excel) określona nazwa pliku jest uwzględniona w argumencie ścieżki bazy danych.

> [!NOTE]
> Nie uwzględniaj odstępów między znakami równości w instrukcji Path w postaci "DATABASE = Drive: \\ \path". Spowoduje to wyrzucanie wyjątku i Niepowodzenie połączenia.

W poniższej tabeli przedstawiono możliwe typy baz danych oraz ich odpowiednie specyfikatory i ścieżki bazy danych:

|Typ bazy danych|Specyfikator|Ścieżka|
|-------------------|---------------|----------|
|Baza danych przy użyciu aparatu bazy danych Jet|"[ `database`];"|" `drive` : \\ \  *Path* \\ \  *filename*. MDB|
|dBASE III|"dBASE III;"|" `drive` : \\ \  *ścieżka*"|
|dBASE IV|"dBASE IV;"|" `drive` : \\ \  *ścieżka*"|
|dBASE 5|"dBASE 5,0;"|" `drive` : \\ \  *ścieżka*"|
|Paradox 3. x|"Paradox 3. x;"|" `drive` : \\ \  *ścieżka*"|
|Paradox 4. x|"Paradox 4. x;"|" `drive` : \\ \  *ścieżka*"|
|Paradox 5. x|"Paradox 5. x;"|" `drive` : \\ \  *ścieżka*"|
|Excel 3,0|"Excel 3,0;"|" `drive` : \\ \  *Path* \\ \  *filename*. XLS|
|Excel 4,0|"Excel 4,0;"|" `drive` : \\ \  *Path* \\ \  *filename*. XLS|
|Excel 5,0 lub Excel 95|"Excel 5,0;"|" `drive` : \\ \  *Path* \\ \  *filename*. XLS|
|Excel 97|"Excel 8,0;"|" `drive` : \\ \  *Path* \  *filename*. XLS|
|Import HTML|"Import HTML;"|" `drive` : \\ \  *ścieżka* \  *filename*"|
|Eksport HTML|"Eksport HTML;"|" `drive` : \\ \  *ścieżka*"|
|Tekst|"Text;"|"dysk: \\ \path"|
|ODBC|Database Baza danych = `database` ; UID = *użytkownik*; PWD = *hasło*; DSN = *DataSourceName;* LOGINTIMEOUT = *s;*" (Mogą to nie być kompletne parametry połączenia dla wszystkich serwerów; jest to tylko przykład. Bardzo ważne jest, aby nie mieć spacji między parametrami.)|Brak|
|Exchange|Zamian<br /><br /> MAPILEVEL = *FolderPath*;<br /><br /> [TABLETYPE = {0 &#124; 1};]<br /><br /> [Profil = *profil*;]<br /><br /> [PWD = *Password*;]<br /><br /> [Baza danych = `database` ;] "|*"dysk*: \\ \  *ścieżka* \\ \  *filename*. MDB|

> [!NOTE]
> Btrieve nie jest już obsługiwany w przypadku obiektów DAO 3,5.

W parametrach połączenia należy użyć podwójnego ukośnika odwrotnego ( \\ \\ ). Jeśli zmodyfikowano właściwości istniejącego połączenia przy użyciu `SetConnect` , musisz następnie wywołać [RefreshLink](#refreshlink). W przypadku inicjowania właściwości połączenia przy użyciu usługi `SetConnect` nie trzeba wywoływać `RefreshLink` , ale należy wybrać tę opcję, najpierw Dołącz tabledef.

Jeśli hasło jest wymagane, ale nie podano, sterownik ODBC wyświetla okno dialogowe logowania przy pierwszym dostępie do tabeli, a następnie ponownie, jeśli połączenie zostanie zamknięte i otwarte.

Parametry połączenia dla obiektu można ustawić `CDaoTableDef` , dostarczając argument źródłowy do `Create` funkcji składowej. Możesz sprawdzić ustawienie, aby określić typ, ścieżkę, identyfikator użytkownika, hasło lub źródło danych ODBC bazy danych. Aby uzyskać więcej informacji, zapoznaj się z dokumentacją dla określonego sterownika.

Aby uzyskać powiązane informacje, zobacz temat "Connect Property" w pomocy DAO.

## <a name="cdaotabledefsetname"></a><a name="setname"></a>CDaoTableDef:: SetName

Wywołaj tę funkcję elementu członkowskiego, aby ustawić zdefiniowaną przez użytkownika nazwę tabeli.

```cpp
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
Wskaźnik do wyrażenia ciągu, który określa nazwę tabeli.

### <a name="remarks"></a>Uwagi

Nazwa musi zaczynać się od litery i może zawierać maksymalnie 64 znaków. Może zawierać cyfry i znaki podkreślenia, ale nie może zawierać znaków interpunkcyjnych ani spacji.

Aby uzyskać powiązane informacje, zobacz temat "Nazwa właściwości" w pomocy DAO.

## <a name="cdaotabledefsetsourcetablename"></a><a name="setsourcetablename"></a>CDaoTableDef::SetSourceTableName

Wywołaj tę funkcję elementu członkowskiego, aby określić nazwę dołączonej tabeli lub nazwę tabeli podstawowej, na której `CDaoTableDef` bazuje obiekt, jak istnieje w oryginalnym źródle danych.

```cpp
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```

### <a name="parameters"></a>Parametry

*lpszSrcTableName*<br/>
Wskaźnik do wyrażenia ciągu, który określa nazwę tabeli w zewnętrznej bazie danych. W przypadku tabeli podstawowej ustawienie jest ciągiem pustym ("").

### <a name="remarks"></a>Uwagi

Następnie należy wywołać [RefreshLink](#refreshlink). To ustawienie właściwości jest puste dla tabeli podstawowej i odczytu/zapisu dla dołączonej tabeli lub obiektu, który nie jest dołączony do kolekcji.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość SourceTableName" w pomocy DAO.

## <a name="cdaotabledefsetvalidationrule"></a><a name="setvalidationrule"></a>CDaoTableDef:: setvalidationrule

Wywołaj tę funkcję elementu członkowskiego, aby ustawić regułę walidacji dla tabledef.

```cpp
void SetValidationRule(LPCTSTR lpszValidationRule);
```

### <a name="parameters"></a>Parametry

*lpszValidationRule*<br/>
Wskaźnik do wyrażenia ciągu, który sprawdza poprawność operacji.

### <a name="remarks"></a>Uwagi

Reguły walidacji są używane w połączeniu z operacjami aktualizacji. Jeśli tabledef zawiera regułę walidacji, aktualizacje tego tabledef muszą pasować do wstępnie określonych kryteriów przed zmianą danych. Jeśli zmiana nie jest zgodna z kryteriami, zostanie wyświetlony wyjątek zawierający tekst [GetValidationText](#getvalidationtext) .

Walidacja jest obsługiwana tylko w przypadku baz danych korzystających z aparatu bazy danych Microsoft Jet. Wyrażenie nie może odwoływać się do funkcji zdefiniowanych przez użytkownika, funkcji agregujących domeny, funkcji agregujących SQL ani zapytań. Reguła walidacji `CDaoTableDef` obiektu może odwoływać się do wielu pól w tym obiekcie.

Na przykład w przypadku pól o nazwach *hire_date* i *termination_date*może być stosowana reguła walidacji:

[!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]

Aby uzyskać powiązane informacje, zobacz temat "Właściwość ValidationRule" w pomocy DAO.

## <a name="cdaotabledefsetvalidationtext"></a><a name="setvalidationtext"></a>CDaoTableDef::SetValidationText

Wywołaj tę funkcję elementu członkowskiego, aby ustawić tekst wyjątku reguły walidacji dla `CDaoTableDef` obiektu z podstawową tabelą obsługiwaną przez aparat bazy danych Microsoft Jet.

```cpp
void SetValidationText(LPCTSTR lpszValidationText);
```

### <a name="parameters"></a>Parametry

*lpszValidationText*<br/>
Wskaźnik do wyrażenia ciągu, który określa tekst wyświetlany, jeśli wprowadzone dane są nieprawidłowe.

### <a name="remarks"></a>Uwagi

Nie można ustawić tekstu walidacji dołączonej tabeli.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość ValidationText" w pomocy DAO.

## <a name="see-also"></a>Zobacz także

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)<br/>
[Klasa CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)
