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
ms.openlocfilehash: adc31ccbf2be34aa1df1fa56111d1990701a6329
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754688"
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
|[CDaoTableDef::Dołącz](#append)|Dodaje nową tabelę do bazy danych.|
|[CDaoTableDef::CanUpdate](#canupdate)|Zwraca wartość niezerowa, jeśli tabela może zostać zaktualizowana (można zmodyfikować definicję pól lub właściwości tabeli).|
|[CDaoTableDef::Zamknij](#close)|Zamyka otwartą definicję tabeli.|
|[CDaoTableDef::Utwórz](#create)|Tworzy tabelę, którą można dodać do bazy danych za pomocą [funkcji Dołącz](#append).|
|[CDaoTableDef::CreateField](#createfield)|Wywoływane, aby utworzyć pole dla tabeli.|
|[CDaoTableDef::CreateIndex](#createindex)|Wywołano, aby utworzyć indeks dla tabeli.|
|[CDaoTableDef::DeleteField](#deletefield)|Wywoływana w celu usunięcia pola z tabeli.|
|[CDaoTableDef::DeleteIndex](#deleteindex)|Wywołany wobec usunąć aneks z an tabela.|
|[CDaoTableDef::GetAttributes](#getattributes)|Zwraca wartość, która wskazuje jedną lub `CDaoTableDef` więcej cech obiektu.|
|[CDaoTableDef::GetConnect](#getconnect)|Zwraca wartość zawierającą informacje o źródle tabeli.|
|[CDaoTableDef::GetDateTworzone](#getdatecreated)|Zwraca datę i godzinę utworzenia `CDaoTableDef` tabeli bazowej leżącej u podstaw obiektu.|
|[CDaoTableDef::GetDateLastUpdated](#getdatelastupdated)|Zwraca datę i godzinę ostatniej zmiany wprowadzonej do projektu tabeli bazowej.|
|[CDaoTableDef::GetFieldCount](#getfieldcount)|Zwraca wartość reprezentującą liczbę pól w tabeli.|
|[CDaoTableDef::GetFieldInfo](#getfieldinfo)|Zwraca określone rodzaje informacji o polach w tabeli.|
|[CDaoTableDef::GetIndexCount](#getindexcount)|Zwraca liczbę indeksów dla tabeli.|
|[CDaoTableDef::GetIndexInfo](#getindexinfo)|Zwraca określone rodzaje informacji o indeksach dla tabeli.|
|[CDaoTableDef::GetName](#getname)|Zwraca zdefiniowaną przez użytkownika nazwę tabeli.|
|[CDaoTableDef::GetRecordCount](#getrecordcount)|Zwraca liczbę rekordów w tabeli.|
|[CDaoTableDef::GetSourceTableName](#getsourcetablename)|Zwraca wartość określającą nazwę dołączonej tabeli w źródłowej bazie danych.|
|[CDaoTableDef::GetValidationRule](#getvalidationrule)|Zwraca wartość, która sprawdza poprawność danych w polu, ponieważ są zmieniane lub dodawane do tabeli.|
|[CDaoTableDef::GetValidationText](#getvalidationtext)|Zwraca wartość określającą tekst komunikatu wyświetlanego przez aplikację, jeśli wartość obiektu Field nie spełnia określonej reguły sprawdzania poprawności.|
|[CDaoTableDef::IsOpen](#isopen)|Zwraca wartość niezerowa, jeśli tabela jest otwarta.|
|[CDaoTableDef::Otwórz](#open)|Otwiera istniejącą tabledef przechowywane w kolekcji TableDef bazy danych.|
|[CDaoTableDef::RefreshLink](#refreshlink)|Aktualizuje informacje o połączeniu dołączonej tabeli.|
|[CDaoTableDef::SetAttributes](#setattributes)|Ustawia wartość, która wskazuje jedną lub `CDaoTableDef` więcej cech obiektu.|
|[CDaoTableDef::SetConnect](#setconnect)|Ustawia wartość, która zawiera informacje o źródle tabeli.|
|[CDaoTableDef::Nazwa zestawu](#setname)|Ustawia nazwę tabeli.|
|[CDaoTableDef::SetSourceTableName](#setsourcetablename)|Ustawia wartość określającą nazwę dołączonej tabeli w źródłowej bazie danych.|
|[CDaoTableDef::SetValidationRule](#setvalidationrule)|Ustawia wartość, która sprawdza poprawność danych w polu, ponieważ są zmieniane lub dodawane do tabeli.|
|[CDaoTableDef::SetValidationText](#setvalidationtext)|Ustawia wartość określającą tekst komunikatu wyświetlanego przez aplikację, jeśli wartość obiektu Field nie spełnia określonej reguły sprawdzania poprawności.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDaoTableDef::m_pDAOTableDef](#m_pdaotabledef)|Wskaźnik do interfejsu DAO leżącego u podstaw obiektu tabledef.|
|[CDaoTableDef::m_pDatabase](#m_pdatabase)|Źródłowa baza danych dla tej tabeli.|

## <a name="remarks"></a>Uwagi

Każdy obiekt bazy danych DAO przechowuje kolekcję o nazwie TableDefs, która zawiera wszystkie zapisane obiekty DAO tabledef.

Można manipulować definicją `CDaoTableDef` tabeli za pomocą obiektu. Można na przykład:

- Sprawdź strukturę pól i indeksów dowolnej tabeli lokalnej, dołączonej lub zewnętrznej w bazie danych.

- Wywołanie `SetConnect` `SetSourceTableName` funkcji i element członkowski dla `RefreshLink` dołączonych tabel i użyj funkcji elementu członkowskiego, aby zaktualizować połączenia do dołączonych tabel.

- Wywołanie `CanUpdate` funkcji elementu członkowskiego w celu ustalenia, czy można edytować definicje pól w tabeli.

- Pobierz lub ustaw warunki `GetValidationRule` `SetValidationRule`sprawdzania poprawności `GetValidationText` `SetValidationText` przy użyciu funkcji i , i i element członkowski.

- Funkcja `Open` elementu członkowskiego służy do tworzenia obiektu typu `CDaoRecordset` tabela, dynaset lub migawka.

    > [!NOTE]
    >  Klasy bazy danych DAO różnią się od klas bazy danych MFC na podstawie łączności otwartej bazy danych (ODBC). Wszystkie nazwy klas bazy danych DAO mają prefiks "CDao". Nadal można uzyskać dostęp do źródeł danych ODBC z klasami DAO; klasy DAO zazwyczaj oferują doskonałe możliwości, ponieważ są one specyficzne dla aparatu bazy danych Microsoft Jet.

### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>Aby użyć obiektów tabledef do pracy z istniejącą tabelą lub do utworzenia nowej tabeli

1. We wszystkich przypadkach najpierw `CDaoTableDef` skonstruować obiekt, dostarczając wskaźnik do [obiektu CDaoDatabase,](../../mfc/reference/cdaodatabase-class.md) do którego należy tabela.

1. Następnie wykonaj następujące czynności, w zależności od tego, co chcesz:

   - Aby użyć istniejącej zapisanej tabeli, należy wywołać funkcję [otwórz](#open) element członkowski obiektu tabledef, podając nazwę zapisanej tabeli.

   - Aby utworzyć nową tabelę, wywołaj funkcję Utwórz element [członkowski](#create) obiektu tabledef, podając nazwę tabeli. Wywołanie [CreateField](#createfield) i [CreateIndex,](#createindex) aby dodać pola i indeksy do tabeli.

   - Wywołanie [Dołącz,](#append) aby zapisać tabelę, dołączając ją do kolekcji TableDefs bazy danych. `Create`stawia tabledef w stanie otwartym, `Create` więc po `Open`wywołaniu nie wywołać .

        > [!TIP]
        >  Najprostszym sposobem tworzenia zapisanych tabel jest utworzenie ich i przechowywanie ich w bazie danych przy użyciu programu Microsoft Access. Następnie można otworzyć i używać ich w kodzie MFC.

Aby użyć obiektu tabledef, który został otwarty `CDaoRecordset` lub utworzony, utwórz i otwórz `dbOpenTable` obiekt, określając nazwę tabledef z wartością w parametrze *nOpenType.*

Aby użyć obiektu tabledef `CDaoRecordset` do utworzenia obiektu, zazwyczaj tworzysz lub otwierasz tabledef, jak opisano powyżej, a następnie konstruujesz obiekt zestawu rekordów, przekazując wskaźnik do obiektu tabledef podczas wywoływania [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open). Tabledef przekazać musi być w stanie otwartym. Aby uzyskać więcej informacji, zobacz klasę [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Po zakończeniu przy użyciu objectdef table, wywołać jego [Close](../../mfc/reference/cdaorecordset-class.md#close) funkcji elementu członkowskiego; następnie zniszczyć tabledef obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CDaoTableDef`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="cdaotabledefappend"></a><a name="append"></a>CDaoTableDef::Dołącz

Wywołanie tej funkcji elementu członkowskiego po [wywołaniu Create,](#create) aby utworzyć nowy obiekt tabledef, aby zapisać tabledef w bazie danych.

```
virtual void Append();
```

### <a name="remarks"></a>Uwagi

Funkcja dołącza obiekt do kolekcji TableDefs bazy danych. Tabledef można używać jako obiektu tymczasowego podczas definiowania go, nie dołączając go, ale jeśli chcesz `Append`go zapisać i używać, musisz wywołać program .

> [!NOTE]
> Jeśli spróbujesz dołączyć bez nazwy tabledef (zawierający ciąg null lub pusty), MFC zgłasza wyjątek.

Aby uzyskać powiązane informacje, zobacz temat "Dołącz metodę" w Pomocy DAO.

## <a name="cdaotabledefcanupdate"></a><a name="canupdate"></a>CDaoTableDef::CanUpdate

Wywołanie tej funkcji elementu członkowskiego, aby `CDaoTableDef` ustalić, czy można zmienić definicję tabeli leżącej u podstaw obiektu.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli struktura tabeli (schemat) mogą być modyfikowane (dodać lub usunąć pola i indeksy), w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślnie można zaktualizować nowo `CDaoTableDef` utworzoną tabelę leżącą u `CDaoTableDef` podstaw obiektu i nie można zaktualizować dołączonej tabeli leżącej u podstaw obiektu. Obiekt `CDaoTableDef` może być aktualizowany, nawet jeśli wynikowy zestaw rekordów nie jest aktualizowany.

Aby uzyskać powiązane informacje, zobacz temat "Aktualizacja właściwości" w Pomocy DAO.

## <a name="cdaotabledefcdaotabledef"></a><a name="cdaotabledef"></a>CDaoTableDef::CDaoTableDef

Konstruuje `CDaoTableDef` obiekt.

```
CDaoTableDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Parametry

*pDatabase (baza danych)*<br/>
Wskaźnik do obiektu [CDaoDatabase.](../../mfc/reference/cdaodatabase-class.md)

### <a name="remarks"></a>Uwagi

Po skonstruowaniu obiektu należy wywołać funkcję [Utwórz](#create) lub [Otwórz](#open) element członkowski. Po zakończeniu z obiektu, należy [Close](#close) wywołać jego Close `CDaoTableDef` funkcji elementu członkowskiego i zniszczyć obiekt.

## <a name="cdaotabledefclose"></a><a name="close"></a>CDaoTableDef::Zamknij

Wywołanie tej funkcji elementu członkowskiego, aby zamknąć i zwolnić obiekt tabledef.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Zwykle po `Close`wywołaniu , usunąć tabledef obiektu, jeśli został przydzielony z **nowym**.

Możesz wywołać [Open](#open) `Close`ponownie po wywołaniu . Dzięki temu można ponownie użyć tabledef obiektu.

Aby uzyskać powiązane informacje, zobacz temat "Zamknij metodę" w Pomocy DAO.

## <a name="cdaotabledefcreate"></a><a name="create"></a>CDaoTableDef::Utwórz

Wywołanie tej funkcji elementu członkowskiego, aby utworzyć nową zapisaną tabelę.

```
virtual void Create(
    LPCTSTR lpszName,
    long lAttributes = 0,
    LPCTSTR lpszSrcTable = NULL,
    LPCTSTR lpszConnect = NULL);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Wskaźnik do ciągu zawierającego nazwę tabeli.

*lPrzyszłądki*<br/>
Wartość odpowiadająca właściwości tabeli reprezentowanej przez obiekt tabledef. Można użyć bitowego OR do połączenia dowolnej z następujących stałych:

|Stały|Opis|
|--------------|-----------------|
|`dbAttachExclusive`|W przypadku baz danych korzystających z aparatu bazy danych Microsoft Jet wskazuje, że tabela jest dołączoną tabelą otwartą do wyłącznego użytku.|
|`dbAttachSavePWD`|W przypadku baz danych korzystających z aparatu bazy danych Microsoft Jet wskazuje, że identyfikator użytkownika i hasło dołączonej tabeli są zapisywane wraz z informacjami o połączeniu.|
|`dbSystemObject`|Wskazuje, że tabela jest tabelą systemową dostarczoną przez aparat bazy danych Microsoft Jet.|
|`dbHiddenObject`|Wskazuje, że tabela jest ukrytą tabelą dostarczoną przez aparat bazy danych Microsoft Jet.|

*lpszsrcTable*<br/>
Wskaźnik do ciągu zawierającego nazwę tabeli źródłowej. Domyślnie ta wartość jest inicjowana jako NULL.

*lpszConnect*<br/>
Wskaźnik do ciągu zawierającego domyślny ciąg połączenia. Domyślnie ta wartość jest inicjowana jako NULL.

### <a name="remarks"></a>Uwagi

Po nazwie tabledef, można następnie [wywołać Dołącz,](#append) aby zapisać tabledef w bazie danych TableDefs kolekcji. Po `Append`wywołaniu , tabledef jest w stanie otwartym i można go użyć do [utworzenia obiektu CDaoRecordset.](../../mfc/reference/cdaorecordset-class.md)

Aby uzyskać powiązane informacje, zobacz temat "CreateTableDef Method" w Pomocy DAO.

## <a name="cdaotabledefcreatefield"></a><a name="createfield"></a>CDaoTableDef::CreateField

Wywołanie tej funkcji elementu członkowskiego, aby dodać pole do tabeli.

```cpp
void CreateField(
    LPCTSTR lpszName,
    short nType,
    long lSize,
    long lAttributes = 0);

void CreateField(CDaoFieldInfo& fieldinfo);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Wskaźnik do wyrażenia ciągu określający nazwę tego pola.

*nTyp*<br/>
Wartość wskazująca typ danych pola. Ustawienie może być jedną z następujących wartości:

|Typ|Rozmiar (bajty)|Opis|
|----------|--------------------|-----------------|
|`dbBoolean`|1 bajt|Bool|
|`dbByte`|BYTE|
|`dbInteger`|2|int|
|`dbLong`|4|długi|
|`dbCurrency`|8|Waluta ( [COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|float|
|`dbDouble`|8|double|
|`dbDate`|8|Data/godzina ( [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Tekst [(CString)](../../atl-mfc-shared/reference/cstringt-class.md)|
|`dbLongBinary`|0|Long Binary (OBIEKT OLE), [CLongBinary](../../mfc/reference/clongbinary-class.md) lub [CByteArray](../../mfc/reference/cbytearray-class.md)|
|`dbMemo`|0|Notatka [(CString](../../atl-mfc-shared/reference/cstringt-class.md))|

*lSize (rozmiar)*<br/>
Wartość wskazująca maksymalny rozmiar pola zawierającego tekst lub stały rozmiar pola zawierającego tekst lub wartości liczbowe. Parametr *lSize* jest ignorowany dla wszystkich pól tekstowych poza tekstem.

*lPrzyszłądki*<br/>
Wartość odpowiadająca właściwościom pola i która może być łączona za pomocą bitowego OR.

|Stały|Opis|
|--------------|-----------------|
|`dbFixedField`|Rozmiar pola jest stały (domyślnie dla pól liczbowych).|
|`dbVariableField`|Rozmiar pola jest zmienny (tylko pola tekstowe).|
|`dbAutoIncrField`|Wartość pola dla nowych rekordów jest automatycznie zwiększana do unikatowej długiej liczby całkowitej, których nie można zmienić. Obsługiwane tylko dla tabel bazy danych microsoft jet.|
|`dbUpdatableField`|Wartość pola można zmienić.|
|`dbDescending`|Pole jest sortowane w kolejności malejącej (Z - A lub 100 - 0) (dotyczy tylko obiektu Field w kolekcji Pola obiektu Index). Jeśli ta stała zostanie pominięta, pole zostanie posortowane w kolejności rosnącej (A - Z lub 0 - 100) (domyślnie).|

*Fieldinfo*<br/>
Odwołanie do struktury [CDaoFieldInfo.](../../mfc/reference/cdaofieldinfo-structure.md)

### <a name="remarks"></a>Uwagi

Obiekt `DAOField` (OLE) jest tworzony i dołączany do `DAOTableDef` kolekcji Fields obiektu (OLE). Oprócz jego zastosowania do badania właściwości obiektu, `CDaoFieldInfo` można również użyć do konstruowania parametru wejściowego do tworzenia nowych pól w tabledef. Pierwsza wersja `CreateField` jest prostsza w użyciu, ale jeśli chcesz uzyskać lepszą `CreateField`kontrolę, możesz `CDaoFieldInfo` użyć drugiej wersji programu , która przyjmuje parametr.

Jeśli używasz `CreateField` wersji, która `CDaoFieldInfo` przyjmuje parametr, należy dokładnie ustawić każdy `CDaoFieldInfo` z następujących elementów członkowskich struktury:

- `m_strName`

- `m_nType`

- `m_lSize`

- `m_lAttributes`

- `m_bAllowZeroLength`

Pozostałe elementy `CDaoFieldInfo` członkowskie powinny być ustawione na **0,** FALSE lub pusty ciąg, `CDaoException` odpowiednio dla elementu członkowskiego lub może wystąpić.

Aby uzyskać powiązane informacje, zobacz temat "CreateField Method" w Pomocy DAO.

## <a name="cdaotabledefcreateindex"></a><a name="createindex"></a>CDaoTableDef::CreateIndex

Wywołanie tej funkcji, aby dodać indeks do tabeli.

```cpp
void CreateIndex(CDaoIndexInfo& indexinfo);
```

### <a name="parameters"></a>Parametry

*indexinfo*<br/>
Odwołanie do struktury [CDaoIndexInfo.](../../mfc/reference/cdaoindexinfo-structure.md)

### <a name="remarks"></a>Uwagi

Indeksy określają kolejność rekordów dostępnych z tabel bazy danych oraz to, czy zduplikowane rekordy są akceptowane. Indeksy zapewniają również efektywny dostęp do danych.

Nie trzeba tworzyć indeksów dla tabel, ale w dużych, unindexed tabel, uzyskiwanie dostępu do określonego rekordu lub tworzenie zestaw rekordów może zająć dużo czasu. Z drugiej strony tworzenie zbyt wielu indeksów spowalnia operacje aktualizacji, dołączania i usuwania, ponieważ wszystkie indeksy są automatycznie aktualizowane. Należy wziąć pod uwagę te czynniki, jak zdecydować, które indeksy do utworzenia.

Należy ustawić następujące `CDaoIndexInfo` elementy składowe:

- `m_strName`Należy podać nazwę.

- `m_pFieldInfos`Musi wskazywać na `CDaoIndexFieldInfo` tablicę struktur.

- `m_nFields`Należy określić liczbę pól w `CDaoFieldInfo` tablicy struktur.

Pozostałe elementy członkowskie zostaną zignorowane, jeśli ustawiono wartość FAŁSZ. Ponadto element `m_lDistinctCount` członkowski jest ignorowany podczas tworzenia indeksu.

## <a name="cdaotabledefdeletefield"></a><a name="deletefield"></a>CDaoTableDef::DeleteField

Wywołanie tej funkcji elementu członkowskiego, aby usunąć pole i uczynić go niedostępnym.

```cpp
void DeleteField(LPCTSTR lpszName);
void DeleteField(int nIndex);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Wskaźnik do wyrażenia ciągu, który jest nazwą istniejącego pola.

*Nindex*<br/>
Indeks pola w kolekcji Pola oparte na wartości zero tabeli, do wyszukiwania według indeksu.

### <a name="remarks"></a>Uwagi

Tej funkcji elementu członkowskiego można użyć w nowym obiekcie, który nie został dołączona do bazy danych lub gdy [Funkcja CanUpdate](#canupdate) zwraca wartość niezerową.

Aby uzyskać powiązane informacje, zobacz temat "Metoda usuwania" w Pomocy DAO.

## <a name="cdaotabledefdeleteindex"></a><a name="deleteindex"></a>CDaoTableDef::DeleteIndex

Wywołanie tej funkcji elementu członkowskiego, aby usunąć indeks w tabeli podstawowej.

```cpp
void DeleteIndex(LPCTSTR lpszName);
void DeleteIndex(int nIndex);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Wskaźnik do wyrażenia ciągu, który jest nazwą istniejącego indeksu.

*Nindex*<br/>
Indeks tablicy obiektu indeksu w bazie danych zero-based TableDefs kolekcji, dla wyszukiwania według indeksu.

### <a name="remarks"></a>Uwagi

Tej funkcji elementu członkowskiego można użyć na nowy obiekt, który nie został dołączona do bazy danych lub gdy [CanUpdate](#canupdate) zwraca nonzero.

Aby uzyskać powiązane informacje, zobacz temat "Metoda usuwania" w Pomocy DAO.

## <a name="cdaotabledefgetattributes"></a><a name="getattributes"></a>CDaoTableDef::GetAttributes

Dla `CDaoTableDef` obiektu zwracana wartość określa właściwości tabeli reprezentowanej przez `CDaoTableDef` obiekt i może być sumą tych stałych:

```
long GetAttributes();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość, która wskazuje jedną lub `CDaoTableDef` więcej cech obiektu.

### <a name="remarks"></a>Uwagi

|Stały|Opis|
|--------------|-----------------|
|`dbAttachExclusive`|W przypadku baz danych korzystających z aparatu bazy danych Microsoft Jet wskazuje, że tabela jest dołączoną tabelą otwartą do wyłącznego użytku.|
|`dbAttachSavePWD`|W przypadku baz danych korzystających z aparatu bazy danych Microsoft Jet wskazuje, że identyfikator użytkownika i hasło dołączonej tabeli są zapisywane wraz z informacjami o połączeniu.|
|`dbSystemObject`|Wskazuje, że tabela jest tabelą systemową dostarczoną przez aparat bazy danych Microsoft Jet.|
|`dbHiddenObject`|Wskazuje, że tabela jest ukrytą tabelą dostarczoną przez aparat bazy danych Microsoft Jet.|
|`dbAttachedTable`|Wskazuje, że tabela jest dołączoną tabelą z bazy danych innych niż ODBC, takiej jak baza danych Paradox.|
|`dbAttachedODBC`|Wskazuje, że tabela jest dołączoną tabelą z bazy danych ODBC, takiej jak Microsoft SQL Server.|

Tabela systemowa to tabela utworzona przez aparat bazy danych Microsoft Jet zawierająca różne informacje wewnętrzne.

Tabela ukryta to tabela utworzona do tymczasowego użytku przez aparat bazy danych Microsoft Jet.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość atrybutów" w Pomocy DAO.

## <a name="cdaotabledefgetconnect"></a><a name="getconnect"></a>CDaoTableDef::GetConnect

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać parametry połączenia dla źródła danych.

```
CString GetConnect();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt `CString` zawierający ścieżkę i typ bazy danych dla tabeli.

### <a name="remarks"></a>Uwagi

Dla `CDaoTableDef` obiektu, który reprezentuje dołączoną tabelę, `CString` obiekt składa się z jednej lub dwóch części (specyfikatora typu bazy danych i ścieżki do bazy danych).

Ścieżka, jak pokazano w poniższej tabeli, jest pełną ścieżką dla katalogu zawierającego pliki bazy danych i musi być poprzedzona identyfikatorem "DATABASE=". W niektórych przypadkach (podobnie jak w przypadku baz danych Microsoft Jet i Microsoft Excel) określona nazwa pliku jest uwzględniona w argurze ścieżki bazy danych.

Tabela w [CDaoTableDef::SetConnect](#setconnect) pokazuje możliwe typy baz danych i odpowiadające im specyfikatory i ścieżki bazy danych:

W przypadku tabel bazowych bazy danych microsoft jet specyfikator jest pustym ciągiem ("").

Jeśli hasło jest wymagane, ale nie podano, sterownik ODBC wyświetla okno dialogowe logowania przy pierwszym dostępie do tabeli i ponownie, jeśli połączenie jest zamknięte i ponownie otwarte. Jeśli dołączona tabela `dbAttachSavePWD` ma atrybut, monit logowania nie pojawi się po ponownym otwarciu tabeli.

Aby uzyskać powiązane informacje, zobacz temat "Połącz właściwość" w Pomocy DAO.

## <a name="cdaotabledefgetdatecreated"></a><a name="getdatecreated"></a>CDaoTableDef::GetDateTworzone

Wywołanie tej funkcji, aby określić `CDaoTableDef` datę i godzinę tabeli leżącej u podstaw obiektu został utworzony.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Wartość zwracana

Wartość zawierająca datę i godzinę utworzenia tabeli `CDaoTableDef` leżącej u podstaw obiektu.

### <a name="remarks"></a>Uwagi

Ustawienia daty i godziny są uzyskiwane z komputera, na którym utworzono lub ostatnio zaktualizowano tabelę bazową. W środowisku dla wielu użytkowników użytkownicy powinni uzyskać te ustawienia bezpośrednio z serwera plików, aby uniknąć rozbieżności; oznacza to, że wszyscy klienci powinni używać "standardowego" źródła czasu — być może z jednego serwera.

Aby uzyskać powiązane informacje, zobacz temat "DateCreated, LastUpdated Properties" w Pomocy DAO.

## <a name="cdaotabledefgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoTableDef::GetDateLastUpdated

Wywołanie tej funkcji, aby określić `CDaoTableDef` datę i godzinę tabeli leżącej u podstaw obiektu został ostatnio zaktualizowany.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Wartość zwracana

Wartość zawierająca datę i godzinę ostatniej `CDaoTableDef` aktualizacji tabeli leżącej u podstaw obiektu.

### <a name="remarks"></a>Uwagi

Ustawienia daty i godziny są uzyskiwane z komputera, na którym utworzono lub ostatnio zaktualizowano tabelę bazową. W środowisku dla wielu użytkowników użytkownicy powinni uzyskać te ustawienia bezpośrednio z serwera plików, aby uniknąć rozbieżności; oznacza to, że wszyscy klienci powinni używać "standardowego" źródła czasu — być może z jednego serwera.

Aby uzyskać powiązane informacje, zobacz temat "DateCreated, LastUpdated Properties" w Pomocy DAO.

## <a name="cdaotabledefgetfieldcount"></a><a name="getfieldcount"></a>CDaoTableDef::GetFieldCount

Wywołanie tej funkcji elementu członkowskiego, aby pobrać liczbę pól zdefiniowanych w tabeli.

```
short GetFieldCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba pól w tabeli.

### <a name="remarks"></a>Uwagi

Jeśli jego wartość wynosi 0, nie ma żadnych obiektów w kolekcji.

Aby uzyskać powiązane informacje, zobacz temat "Count Property" w Pomocy DAO.

## <a name="cdaotabledefgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoTableDef::GetFieldInfo

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać różne rodzaje informacji o polu zdefiniowanym w tabledef.

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

*Nindex*<br/>
Indeks obiektu pola w kolekcji Pola oparte na wartości zero tabeli, do wyszukiwania według indeksu.

*Fieldinfo*<br/>
Odwołanie do struktury [CDaoFieldInfo.](../../mfc/reference/cdaofieldinfo-structure.md)

*dwInfoOptions (NpfoOptions)*<br/>
Opcje określające informacje o polu do pobrania. Dostępne opcje są wymienione tutaj wraz z tym, co powodują, że funkcja do powrotu:

- `AFX_DAO_PRIMARY_INFO`(Domyślnie) Nazwa, typ, rozmiar, atrybuty. Użyj tej opcji, aby uzyskać najwyższą wydajność.

- `AFX_DAO_SECONDARY_INFO`Informacje podstawowe, plus: Pozycja porządkowa, wymagane, Zezwalaj na długość zerową, Kolejność sortowania, Nazwa obca, Pole źródłowe, Tabela źródłowa

- `AFX_DAO_ALL_INFO`Informacje podstawowe i pomocnicze, a także: Reguła sprawdzania poprawności, Tekst sprawdzania poprawności, Wartość domyślna

*Lpszname*<br/>
Wskaźnik do nazwy obiektu pola, do wyszukiwania według nazwy. Nazwa jest ciągiem z maksymalnie 64 znakami, który jednoznacznie nazywa to pole.

### <a name="remarks"></a>Uwagi

Jedna wersja funkcji umożliwia wyszukywę pola według indeksu. Druga wersja umożliwia wyszukywanie pola według nazwy.

Aby uzyskać opis zwróconych informacji, zobacz [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) struktury. Ta struktura ma elementy, które odpowiadają elementom informacji wymienionych powyżej w opisie *dwInfoOptions*. Gdy poprosisz o informacje na jednym poziomie, otrzymujesz informacje o wcześniejszych poziomach.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość atrybutów" w Pomocy DAO.

## <a name="cdaotabledefgetindexcount"></a><a name="getindexcount"></a>CDaoTableDef::GetIndexCount

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać liczbę indeksów dla tabeli.

```
short GetIndexCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba indeksów dla tabeli.

### <a name="remarks"></a>Uwagi

Jeśli jego wartość wynosi 0, nie ma żadnych indeksów w kolekcji.

Aby uzyskać powiązane informacje, zobacz temat "Count Property" w Pomocy DAO.

## <a name="cdaotabledefgetindexinfo"></a><a name="getindexinfo"></a>CDaoTableDef::GetIndexInfo

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać różne rodzaje informacji o indeksie zdefiniowanym w tabledef.

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

*Nindex*<br/>
Indeks numeryczny Index obiektu w tabeli zero oparte indeksy kolekcji, dla wyszukiwania według jego pozycji w kolekcji.

*indexinfo*<br/>
Odwołanie do struktury [CDaoIndexInfo.](../../mfc/reference/cdaoindexinfo-structure.md)

*dwInfoOptions (NpfoOptions)*<br/>
Opcje określające informacje o indeksie do pobrania. Dostępne opcje są wymienione tutaj wraz z tym, co powodują, że funkcja do powrotu:

- `AFX_DAO_PRIMARY_INFO`Nazwa, informacje o polu, pola. Użyj tej opcji, aby uzyskać najwyższą wydajność.

- `AFX_DAO_SECONDARY_INFO`Informacje podstawowe, plus: Podstawowy, Unikatowy, Klastrowany, Ignoruj wartości null, Wymagany, Obcy

- `AFX_DAO_ALL_INFO`Informacje podstawowe i pomocnicze, plus: Liczba odrębnych

*Lpszname*<br/>
Wskaźnik do nazwy obiektu indeksu, do wyszukiwania według nazwy.

### <a name="remarks"></a>Uwagi

Jedna wersja funkcji umożliwia wyszukywę indeksu według jego pozycji w kolekcji. Druga wersja umożliwia wyszukywanie indeksu według nazwy.

Aby uzyskać opis zwróconych informacji, zobacz [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) struktury. Ta struktura ma elementy, które odpowiadają elementom informacji wymienionych powyżej w opisie *dwInfoOptions*. Gdy poprosisz o informacje na jednym poziomie, otrzymujesz informacje o wcześniejszych poziomach.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość atrybutów" w Pomocy DAO.

## <a name="cdaotabledefgetname"></a><a name="getname"></a>CDaoTableDef::GetName

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać nazwę zdefiniowaną przez użytkownika tabeli podstawowej.

```
CString GetName();
```

### <a name="return-value"></a>Wartość zwracana

Zdefiniowana przez użytkownika nazwa tabeli.

### <a name="remarks"></a>Uwagi

Ta nazwa zaczyna się od litery i może zawierać maksymalnie 64 znaki. Może zawierać liczby i znaki podkreślenia, ale nie może zawierać znaków interpunkcyjnych ani spacji.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość nazw" w Pomocy DAO.

## <a name="cdaotabledefgetrecordcount"></a><a name="getrecordcount"></a>CDaoTableDef::GetRecordCount

Wywołanie tej funkcji elementu członkowskiego, aby `CDaoTableDef` dowiedzieć się, ile rekordów znajduje się w obiekcie.

```
long GetRecordCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba rekordów dostępnych w tabledef obiektu.

### <a name="remarks"></a>Uwagi

Wywołanie `GetRecordCount` obiektu typu `CDaoTableDef` tabeli odzwierciedla przybliżoną liczbę rekordów w tabeli i jest natychmiast zmieniane, gdy rekordy tabel są dodawane i usuwane. Wycofane transakcje będą wyświetlane jako część liczby rekordów, dopóki nie zostanie [wywołana CDaoWorkSpace::CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase). Obiekt `CDaoTableDef` bez rekordów ma ustawienie właściwości liczby rekordów 0. Podczas pracy z dołączonymi tabelami `GetRecordCount` lub bazami danych ODBC zawsze zwraca wartość -1.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość RecordCount" w Pomocy DAO.

## <a name="cdaotabledefgetsourcetablename"></a><a name="getsourcetablename"></a>CDaoTableDef::GetSourceTableName

Wywołanie tej funkcji elementu członkowskiego, aby pobrać nazwę dołączonej tabeli w źródłowej bazie danych.

```
CString GetSourceTableName();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt, `CString` który określa nazwę źródła dołączonej tabeli lub pusty ciąg, jeśli tabela danych natywnych.

### <a name="remarks"></a>Uwagi

Załączona tabela to tabela w innej bazie danych połączonej z bazą danych microsoft jet. Dane dla dołączonych tabel pozostaje w zewnętrznej bazie danych, gdzie mogą być manipulowane przez inne aplikacje.

Aby uzyskać powiązane informacje, zobacz temat "SourceTableName Property" w Pomocy DAO.

## <a name="cdaotabledefgetvalidationrule"></a><a name="getvalidationrule"></a>CDaoTableDef::GetValidationRule

Wywołanie tej funkcji elementu członkowskiego, aby pobrać regułę sprawdzania poprawności dla tabledef.

```
CString GetValidationRule();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt, `CString` który sprawdza poprawność danych w polu, ponieważ jest zmieniany lub dodawany do tabeli.

### <a name="remarks"></a>Uwagi

Reguły sprawdzania poprawności są używane w połączeniu z operacjami aktualizacji. Jeśli tabledef zawiera regułę sprawdzania poprawności, aktualizacje tej funkcji tabledef muszą spełniać wstępnie określone kryteria przed zmianą danych. Jeśli zmiana nie spełnia kryteriów, wyjątek zawierający wartość [GetValidationText](#getvalidationtext) jest generowany. W `CDaoTableDef` przypadku obiektu `CString` jest to tylko do odczytu dla dołączonej tabeli i odczytu/zapisu dla tabeli bazowej.

Aby uzyskać powiązane informacje, zobacz temat "ValidationRule Property" w Pomocy DAO.

## <a name="cdaotabledefgetvalidationtext"></a><a name="getvalidationtext"></a>CDaoTableDef::GetValidationText

Wywołanie tej funkcji, aby pobrać ciąg do wyświetlenia, gdy użytkownik wprowadzi dane, które nie są zgodne z regułą sprawdzania poprawności.

```
CString GetValidationText();
```

### <a name="return-value"></a>Wartość zwracana

Obiekt, `CString` który określa wyświetlany tekst, jeśli użytkownik wprowadzi dane, które nie są zgodne z regułą sprawdzania poprawności.

### <a name="remarks"></a>Uwagi

W `CDaoTableDef` przypadku obiektu `CString` jest to tylko do odczytu dla dołączonej tabeli i odczytu/zapisu dla tabeli bazowej.

Aby uzyskać powiązane informacje, zobacz temat "ValidationText Property" w Pomocy DAO.

## <a name="cdaotabledefisopen"></a><a name="isopen"></a>CDaoTableDef::IsOpen

Wywołanie tej funkcji elementu `CDaoTableDef` członkowskiego, aby ustalić, czy obiekt jest aktualnie otwarty.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, `CDaoTableDef` jeśli obiekt jest otwarty; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

## <a name="cdaotabledefm_pdatabase"></a><a name="m_pdatabase"></a>CDaoTableDef::m_pDatabase

Zawiera wskaźnik do obiektu [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) dla tej tabeli.

### <a name="remarks"></a>Uwagi

## <a name="cdaotabledefm_pdaotabledef"></a><a name="m_pdaotabledef"></a>CDaoTableDef::m_pDAOTableDef

Zawiera wskaźnik do interfejsu OLE dla obiektu DAO `CDaoTableDef` tabledef leżącego u podstaw obiektu.

### <a name="remarks"></a>Uwagi

Użyj tego wskaźnika, jeśli chcesz uzyskać bezpośredni dostęp do interfejsu DAO.

## <a name="cdaotabledefopen"></a><a name="open"></a>CDaoTableDef::Otwórz

Wywołanie tej funkcji elementu członkowskiego, aby otworzyć tabledef wcześniej zapisane w kolekcji TableDef bazy danych.

```
virtual void Open(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Wskaźnik do ciągu określający nazwę tabeli.

### <a name="remarks"></a>Uwagi

## <a name="cdaotabledefrefreshlink"></a><a name="refreshlink"></a>CDaoTableDef::RefreshLink

Wywołanie tej funkcji elementu członkowskiego, aby zaktualizować informacje o połączeniu dla dołączonej tabeli.

```cpp
void RefreshLink();
```

### <a name="remarks"></a>Uwagi

Informacje o połączeniu dołączonej tabeli można zmienić, `CDaoTableDef` wywołując funkcję `RefreshLink` [SetConnect](#setconnect) na odpowiednim obiekcie, a następnie używając funkcji elementu członkowskiego do aktualizacji informacji. Podczas wywoływania `RefreshLink`właściwości dołączonej tabeli nie są zmieniane.

Aby wymusić, aby zmodyfikowane informacje o połączeniu zostały zastosowane, wszystkie otwarte obiekty [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) oparte na tej tabledef muszą zostać zamknięte.

Aby uzyskać powiązane informacje, zobacz temat "RefreshLink Method" w Pomocy DAO.

## <a name="cdaotabledefsetattributes"></a><a name="setattributes"></a>CDaoTableDef::SetAttributes

Ustawia wartość, która wskazuje jedną lub `CDaoTableDef` więcej cech obiektu.

```cpp
void SetAttributes(long lAttributes);
```

### <a name="parameters"></a>Parametry

*lPrzyszłądki*<br/>
Charakterystyki tabeli reprezentowane `CDaoTableDef` przez obiekt i może być sumą tych stałych:

|Stały|Opis|
|--------------|-----------------|
|`dbAttachExclusive`|W przypadku baz danych korzystających z aparatu bazy danych Microsoft Jet wskazuje, że tabela jest dołączoną tabelą otwartą do wyłącznego użytku.|
|`dbAttachSavePWD`|W przypadku baz danych korzystających z aparatu bazy danych Microsoft Jet wskazuje, że identyfikator użytkownika i hasło dołączonej tabeli są zapisywane wraz z informacjami o połączeniu.|
|`dbSystemObject`|Wskazuje, że tabela jest tabelą systemową dostarczoną przez aparat bazy danych Microsoft Jet.|
|`dbHiddenObject`|Wskazuje, że tabela jest ukrytą tabelą dostarczoną przez aparat bazy danych Microsoft Jet.|

### <a name="remarks"></a>Uwagi

Podczas ustawiania wielu atrybutów można je łączyć, sumując odpowiednie stałe za pomocą operatora bitowego OR. Ustawienie `dbAttachExclusive` na tabeli bezłącznej tworzy wyjątek. Połączenie następujących wartości również powodować wyjątek:

- **dbAttachWyłączające &#124; dbAttachedODBC**

- **dbAttachSavePWD &#124; dbAttachedTable**

Aby uzyskać powiązane informacje, zobacz temat "Właściwość atrybutów" w Pomocy DAO.

## <a name="cdaotabledefsetconnect"></a><a name="setconnect"></a>CDaoTableDef::SetConnect

Dla `CDaoTableDef` obiektu, który reprezentuje dołączoną tabelę, obiekt ciągu składa się z jednej lub dwóch części (specyfikatora typu bazy danych i ścieżki do bazy danych).

```cpp
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Parametry

*lpszConnect*<br/>
Wskaźnik do wyrażenia ciągu, który określa dodatkowe parametry do przekazania do sterowników ODBC lub instalowalnych isam.

### <a name="remarks"></a>Uwagi

Ścieżka, jak pokazano w poniższej tabeli, jest pełną ścieżką dla katalogu zawierającego pliki bazy danych i musi być poprzedzona identyfikatorem "DATABASE=". W niektórych przypadkach (podobnie jak w przypadku baz danych Microsoft Jet i Microsoft Excel) określona nazwa pliku jest uwzględniona w argurze ścieżki bazy danych.

> [!NOTE]
> Nie należy dołączać odstępów wokół znaku równości w instrukcjach\\ścieżki formularza "DATABASE=drive: \path". Spowoduje to wyjątek i połączenie nie.

W poniższej tabeli przedstawiono możliwe typy baz danych oraz odpowiadające im specyfikatory i ścieżki bazy danych:

|Typ bazy danych|Specyfikator|Ścieżka|
|-------------------|---------------|----------|
|Baza danych przy użyciu aparatu bazy danych Jet|"[ `database`];"|" `drive`\\\ :*nazwa pliku**ścieżki*\\\ . MDB"|
|dBASE III|"dBASE III;"|" `drive`\\\ :*ścieżka*"|
|dBASE IV|"dBASE IV;"|" `drive`\\\ :*ścieżka*"|
|dBASE 5|"dBASE 5.0;"|" `drive`\\\ :*ścieżka*"|
|Paradoks 3.x|"Paradoks 3.x;"|" `drive`\\\ :*ścieżka*"|
|Paradoks 4.x|"Paradoks 4.x;"|" `drive`\\\ :*ścieżka*"|
|Paradoks 5.x|"Paradoks 5.x;"|" `drive`\\\ :*ścieżka*"|
|Program Excel 3.0|"Excel 3.0;"|" `drive`\\\ :*nazwa pliku**ścieżki*\\\ . XLS"|
|Program Excel 4.0|"Excel 4.0;"|" `drive`\\\ :*nazwa pliku**ścieżki*\\\ . XLS"|
|Program Excel 5.0 lub Excel 95|"Excel 5.0;"|" `drive`\\\ :*nazwa pliku**ścieżki*\\\ . XLS"|
|Program Excel 97|"Excel 8.0;"|" `drive`\\\ :*nazwa pliku**ścieżki*\ . XLS"|
|HTML Import|"Import HTML;"|" `drive`\\\ :*nazwa pliku**ścieżki*\ "|
|Eksport HTML|"Eksport HTML;"|" `drive`\\\ :*ścieżka*"|
|Tekst|"Tekst;"|"drive:\\\path"|
|ODBC|"ODBC; BAZA `database`DANYCH= ; UID = *użytkownik*; PWD = *hasło*; DSN = *nazwa źródła danych;* LOGINTIMEOUT = *sekundy;*" (Może to nie być pełny ciąg połączenia dla wszystkich serwerów; jest to tylko przykład. Bardzo ważne jest, aby nie mieć spacji między parametrami.)|Brak|
|Exchange|"Wymiana;<br /><br /> MAPILEVEL = *ścieżka folderów*;<br /><br /> [TABLETYPE={ 0 &#124; 1 };]<br /><br /> [PROFIL= *profil*;]<br /><br /> [PWD= *hasło*;]<br /><br /> [BAZA `database`DANYCH= ;]"|*"drive*\\\ :*path*\\\ *filename*. MDB"|

> [!NOTE]
> Btrieve nie jest już obsługiwany od DAO 3.5.

W ciągach połączeń należy\\\\użyć podwójnego ukośnika odwrotnego ( ) w ciągu połączenia. Jeśli właściwości istniejącego połączenia zostały zmodyfikowane `SetConnect`za pomocą programu , należy następnie wywołać polecenie [RefreshLink](#refreshlink). Jeśli inicjujesz właściwości połączenia `SetConnect`przy użyciu `RefreshLink`, nie trzeba wywoływać , ale należy to zrobić, najpierw dołącz tabledef.

Jeśli hasło jest wymagane, ale nie podano, sterownik ODBC wyświetla okno dialogowe logowania przy pierwszym dostępie do tabeli i ponownie, jeśli połączenie jest zamknięte i ponownie otwarte.

Ciąg połączenia dla `CDaoTableDef` obiektu można ustawić, udostępniając `Create` argument źródłowy funkcji elementu członkowskiego. Można sprawdzić ustawienie, aby określić typ, ścieżkę, identyfikator użytkownika, hasło lub źródło danych ODBC bazy danych. Aby uzyskać więcej informacji, zobacz dokumentację dla określonego sterownika.

Aby uzyskać powiązane informacje, zobacz temat "Połącz właściwość" w Pomocy DAO.

## <a name="cdaotabledefsetname"></a><a name="setname"></a>CDaoTableDef::Nazwa zestawu

Wywołanie tej funkcji elementu członkowskiego, aby ustawić nazwę zdefiniowaną przez użytkownika dla tabeli.

```cpp
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parametry

*Lpszname*<br/>
Wskaźnik do wyrażenia ciągu, który określa nazwę tabeli.

### <a name="remarks"></a>Uwagi

Nazwa musi zaczynać się od litery i może zawierać maksymalnie 64 znaki. Może zawierać liczby i znaki podkreślenia, ale nie może zawierać znaków interpunkcyjnych ani spacji.

Aby uzyskać powiązane informacje, zobacz temat "Właściwość nazw" w Pomocy DAO.

## <a name="cdaotabledefsetsourcetablename"></a><a name="setsourcetablename"></a>CDaoTableDef::SetSourceTableName

Wywołanie tej funkcji elementu członkowskiego, aby określić nazwę dołączonej tabeli lub nazwę tabeli bazowej, na której `CDaoTableDef` obiekt jest oparty, ponieważ istnieje w oryginalnym źródle danych.

```cpp
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```

### <a name="parameters"></a>Parametry

*lpszSrcTableName*<br/>
Wskaźnik do wyrażenia ciągu, który określa nazwę tabeli w zewnętrznej bazie danych. W przypadku tabeli bazowej ustawienie jest pustym ciągiem ("").

### <a name="remarks"></a>Uwagi

Następnie należy [wywołać refreshlink](#refreshlink). To ustawienie właściwości jest puste dla tabeli bazowej i odczytu/zapisu dla dołączonej tabeli lub obiektu, który nie jest dołączany do kolekcji.

Aby uzyskać powiązane informacje, zobacz temat "SourceTableName Property" w Pomocy DAO.

## <a name="cdaotabledefsetvalidationrule"></a><a name="setvalidationrule"></a>CDaoTableDef::SetValidationRule

Wywołanie tej funkcji elementu członkowskiego, aby ustawić regułę sprawdzania poprawności dla tabledef.

```cpp
void SetValidationRule(LPCTSTR lpszValidationRule);
```

### <a name="parameters"></a>Parametry

*lpszValidationRule*<br/>
Wskaźnik do wyrażenia ciągu, który sprawdza poprawność operacji.

### <a name="remarks"></a>Uwagi

Reguły sprawdzania poprawności są używane w połączeniu z operacjami aktualizacji. Jeśli tabledef zawiera regułę sprawdzania poprawności, aktualizacje tej funkcji tabledef muszą spełniać wstępnie określone kryteria przed zmianą danych. Jeśli zmiana nie spełnia kryteriów, wyświetlany jest wyjątek zawierający tekst [GetValidationText.](#getvalidationtext)

Sprawdzanie poprawności jest obsługiwane tylko dla baz danych korzystających z aparatu bazy danych Microsoft Jet. Wyrażenie nie może odwoływać się do funkcji zdefiniowanych przez użytkownika, funkcji agregujących domeny, funkcji agregujących SQL ani zapytań. Reguła `CDaoTableDef` sprawdzania poprawności obiektu może odwoływać się do wielu pól w tym obiekcie.

Na przykład w przypadku pól o nazwach *hire_date* i *termination_date*może być regułą sprawdzania poprawności:

[!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]

Aby uzyskać powiązane informacje, zobacz temat "ValidationRule Property" w Pomocy DAO.

## <a name="cdaotabledefsetvalidationtext"></a><a name="setvalidationtext"></a>CDaoTableDef::SetValidationText

Wywołanie tej funkcji elementu członkowskiego, aby ustawić `CDaoTableDef` tekst wyjątku reguły sprawdzania poprawności dla obiektu z podstawowej tabeli podstawowej obsługiwane przez aparat bazy danych Microsoft Jet.

```cpp
void SetValidationText(LPCTSTR lpszValidationText);
```

### <a name="parameters"></a>Parametry

*lpszValidationText*<br/>
Wskaźnik do wyrażenia ciągu, który określa tekst wyświetlany, jeśli wprowadzone dane są nieprawidłowe.

### <a name="remarks"></a>Uwagi

Nie można ustawić tekstu sprawdzania poprawności dołączonej tabeli.

Aby uzyskać powiązane informacje, zobacz temat "ValidationText Property" w Pomocy DAO.

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)<br/>
[Klasa CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)
