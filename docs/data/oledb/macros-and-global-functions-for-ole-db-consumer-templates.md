---
title: Makra i funkcje globalne dla szablonów konsumentów OLE DB
ms.date: 02/11/2019
f1_keywords:
- ATL.AtlTraceErrorRecords
- ATL::AtlTraceErrorRecords
- AtlTraceErrorRecords
- BEGIN_ACCESSOR
- BEGIN_ACCESSOR_MAP
- END_ACCESSOR
- END_ACCESSOR_MAP
- BEGIN_COLUMN_MAP
- BLOB_ENTRY
- BLOB_ENTRY_LENGTH
- BLOB_ENTRY_LENGTH_STATUS
- BLOB_ENTRY_STATUS
- BLOB_NAME
- BLOB_NAME_LENGTH
- BLOB_NAME_LENGTH_STATUS
- BLOB_NAME_STATUS
- BOOKMARK_ENTRY
- COLUMN_ENTRY
- COLUMN_ENTRY_EX
- COLUMN_ENTRY_LENGTH
- COLUMN_ENTRY_LENGTH_STATUS
- COLUMN_ENTRY_PS
- COLUMN_ENTRY_PS_LENGTH
- COLUMN_ENTRY_PS_LENGTH_STATUS
- COLUMN_ENTRY_PS_STATUS
- COLUMN_ENTRY_STATUS
- COLUMN_ENTRY_TYPE
- COLUMN_ENTRY_TYPE_SIZE
- COLUMN_NAME
- COLUMN_NAME_EX
- COLUMN_NAME_LENGTH
- COLUMN_NAME_LENGTH_STATUS
- COLUMN_NAME_PS
- COLUMN_NAME_PS_LENGTH
- COLUMN_NAME_PS_LENGTH_STATUS
- COLUMN_NAME_PS_STATUS
- COLUMN_NAME_STATUS
- COLUMN_NAME_TYPE
- COLUMN_NAME_TYPE_PS
- COLUMN_NAME_TYPE_SIZE
- COLUMN_NAME_TYPE_STATUS
- END_COLUMN_MAP
- DEFINE_COMMAND
- DEFINE_COMMAND_EX
- BEGIN_PARAM_MAP
- END_PARAM_MAP
- SET_PARAM_TYPE
helpviewer_keywords:
- OLE DB consumer templates, macros
- macros, OLE DB consumer template
- AtlTraceErrorRecords function
- BEGIN_ACCESSOR macro, syntax
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR_MAP macro
- END_ACCESSOR macro
- END_ACCESSOR_MAP macro
- BEGIN_COLUMN_MAP macro
- BLOB_ENTRY macro
- BLOB_ENTRY_LENGTH macro
- BLOB_ENTRY_LENGTH_STATUS macro
- BLOB_ENTRY_STATUS macro
- BLOB_NAME macro
- BLOB_NAME_LENGTH macro
- BLOB_NAME_LENGTH_STATUS macro
- BLOB_NAME_STATUS macro
- BOOKMARK_ENTRY macro
- COLUMN_ENTRY macro
- COLUMN_ENTRY_EX macro
- COLUMN_ENTRY_LENGTH macro
- COLUMN_ENTRY_LENGTH_STATUS macro
- COLUMN_ENTRY_PS macro
- COLUMN_ENTRY_PS_LENGTH macro
- COLUMN_ENTRY_PS_LENGTH_STATUS macro
- COLUMN_ENTRY_PS_STATUS macro
- COLUMN_ENTRY_STATUS macro
- COLUMN_ENTRY_TYPE macro
- COLUMN_ENTRY_TYPE_SIZE macro
- COLUMN_NAME macro
- COLUMN_NAME_EX macro
- COLUMN_NAME_LENGTH macro
- COLUMN_NAME_LENGTH_STATUS macro
- COLUMN_NAME_PS macro
- COLUMN_NAME_PS_LENGTH macro
- COLUMN_NAME_PS_LENGTH_STATUS macro
- COLUMN_NAME_PS_STATUS macro
- COLUMN_NAME_STATUS macro
- COLUMN_NAME_TYPE macro
- COLUMN_NAME_TYPE_PS macro
- COLUMN_NAME_TYPE_SIZE macro
- COLUMN_NAME_TYPE_STATUS macro
- END_COLUMN_MAP macro
- DEFINE_COMMAND macro
- DEFINE_COMMAND_EX macro
- BEGIN_PARAM_MAP macro
- END_PARAM_MAP macro
- SET_PARAM_TYPE macro
ms.assetid: 8765eb7b-32dd-407c-bacf-8890ef959837
ms.openlocfilehash: 8b898990672f590f6047eef6fdfd1ed7eecb3f92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369827"
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>Makra i funkcje globalne dla szablonów konsumentów OLE DB

Szablony konsumentów OLE DB obejmują następujące makra i funkcje globalne:

## <a name="global-functions"></a>Funkcje globalne

|||
|-|-|
|[AtlTraceErrorRecords](#atltraceerrorrecords)|Zrzuca informacje o rekordzie błędu OLE DB do urządzenia zrzutu, jeśli zostanie zwrócony błąd.|

## <a name="accessor-map-macros"></a>Makra map programu Accessor

|||
|-|-|
|[BEGIN_ACCESSOR](#begin_accessor)|Oznacza początek wpisu akcesora.|
|[BEGIN_ACCESSOR_MAP](#begin_accessor_map)|Oznacza początek wpisów mapy akcesora.|
|[END_ACCESSOR](#end_accessor)|Oznacza koniec wpisu akcesora.|
|[END_ACCESSOR_MAP](#end_accessor_map)|Oznacza koniec wpisów mapy akcesora.|

## <a name="column-map-macros"></a>Makra mapy kolumn

|||
|-|-|
|[BEGIN_COLUMN_MAP](#begin_column_map)|Oznacza początek wpisów mapy kolumn w klasie rekordów użytkownika.|
|[BLOB_ENTRY](#blob_entry)|Służy do wiązania dużego obiektu binarnego (BLOB).|
|[BLOB_ENTRY_LENGTH](#blob_entry_length)|Raportuje długość kolumny danych obiektu BLOB.|
|[BLOB_ENTRY_LENGTH_STATUS](#blob_entry_length_status)|Raportuje długość i stan kolumny danych obiektu BLOB.|
|[BLOB_ENTRY_STATUS](#blob_entry_status)|Raportuje stan kolumny danych obiektu BLOB.|
|[BLOB_NAME](#blob_name)|Służy do wiązania dużego obiektu binarnego według nazwy kolumny.|
|[BLOB_NAME_LENGTH](#blob_name_length)|Raportuje długość kolumny danych obiektu BLOB.|
|[BLOB_NAME_LENGTH_STATUS](#blob_name_length_status)|Raportuje długość i stan kolumny danych obiektu BLOB.|
|[BLOB_NAME_STATUS](#blob_name_status)|Raportuje stan kolumny danych obiektu BLOB.|
|[BOOKMARK_ENTRY](#bookmark_entry)|Reprezentuje wpis zakładki w zestawie wierszy. Wpis zakładki jest specjalnym rodzajem wpisu kolumny.|
|[COLUMN_ENTRY](#column_entry)|Reprezentuje powiązanie z określonej kolumny w bazie danych.|
|[COLUMN_ENTRY_EX](#column_entry_ex)|Reprezentuje powiązanie z określonej kolumny w bazie danych. Obsługuje *parametry typu,* *długości,* *precyzji,* *skali*i *stanu.*|
|[COLUMN_ENTRY_LENGTH](#column_entry_length)|Reprezentuje powiązanie z określonej kolumny w bazie danych. Obsługuje zmienną *długości.*|
|[COLUMN_ENTRY_LENGTH_STATUS](#column_entry_length_status)|Reprezentuje powiązanie z określonej kolumny w bazie danych. Obsługuje parametry *stanu* i *długości.*|
|[COLUMN_ENTRY_PS](#column_entry_ps)|Reprezentuje powiązanie z określonej kolumny w bazie danych. Obsługuje *parametry precyzji* i *skali.*|
|[COLUMN_ENTRY_PS_LENGTH](#column_entry_ps_length)|Reprezentuje powiązanie z określonej kolumny w bazie danych. Obsługuje zmienną *długość,* *dokładność* i parametry *skali.*|
|[COLUMN_ENTRY_PS_LENGTH_STATUS](#column_entry_ps_length_status)|Reprezentuje powiązanie z określonej kolumny w bazie danych. Obsługuje zmienne *stanu* i *długości,* *dokładność* i parametry *skali.*|
|[COLUMN_ENTRY_PS_STATUS](#column_entry_ps_status)|Reprezentuje powiązanie z określonej kolumny w bazie danych. Obsługuje zmienną *stanu,* *dokładność* i parametry *skali.*|
|[COLUMN_ENTRY_STATUS](#column_entry_status)|Reprezentuje powiązanie z określonej kolumny w bazie danych. Obsługuje zmienną *stanu.*|
|[COLUMN_ENTRY_TYPE](#column_entry_type)|Reprezentuje powiązanie z określonej kolumny w bazie danych. Obsługuje parametr *typu.*|
|[COLUMN_ENTRY_TYPE_SIZE](#column_entry_type_size)|Reprezentuje powiązanie z określonej kolumny w bazie danych. Obsługuje parametry *typu* i *rozmiaru.*|
|[COLUMN_NAME](#column_name)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy.|
|[COLUMN_NAME_EX](#column_name_ex)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację typu danych, rozmiaru, precyzji, skali, długości kolumny i stanu kolumny.|
|[COLUMN_NAME_LENGTH](#column_name_length)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację długości kolumny.|
|[COLUMN_NAME_LENGTH_STATUS](#column_name_length_status)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację długości i stanu kolumny.|
|[COLUMN_NAME_PS](#column_name_ps)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację precyzji i skali.|
|[COLUMN_NAME_PS_LENGTH](#column_name_ps_length)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację precyzji, skali i długości kolumny.|
|[COLUMN_NAME_PS_LENGTH_STATUS](#column_name_ps_length_status)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację precyzji, skali, długości kolumny i stanu kolumny.|
|[COLUMN_NAME_PS_STATUS](#column_name_ps_status)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację dokładności, skali i stanu kolumny.|
|[COLUMN_NAME_STATUS](#column_name_status)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację stanu kolumny.|
|[COLUMN_NAME_TYPE](#column_name_type)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację typu danych.|
|[COLUMN_NAME_TYPE_PS](#column_name_type_ps)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację typu danych, precyzji i skali.|
|[COLUMN_NAME_TYPE_SIZE](#column_name_type_size)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację typu i rozmiaru danych.|
|[COLUMN_NAME_TYPE_STATUS](#column_name_type_status)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację typu danych i stanu kolumny.|
|[END_COLUMN_MAP](#end_column_map)|Oznacza koniec wpisów mapy kolumn.|

## <a name="command-macros"></a>Makra poleceń

|||
|-|-|
|[DEFINE_COMMAND](#define_command)|Określa polecenie, które będzie używane do tworzenia zestawu wierszy podczas korzystania z klasy [CCommand.](../../data/oledb/ccommand-class.md) Akceptuje tylko typy ciągów pasujące do określonego typu aplikacji (ANSI lub Unicode). Zaleca się stosowanie [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) zamiast DEFINE_COMMAND.|
|[DEFINE_COMMAND_EX](#define_command_ex)|Określa polecenie, które będzie używane do tworzenia zestawu wierszy podczas korzystania z klasy [CCommand.](../../data/oledb/ccommand-class.md) Obsługuje aplikacje ANSI i Unicode.|

## <a name="parameter-map-macros"></a>Makra mapy parametrów

|||
|-|-|
|[BEGIN_PARAM_MAP](#begin_param_map)|Oznacza początek wpisów mapy parametrów w klasie rekordów użytkownika.|
|[END_PARAM_MAP](#end_param_map)|Oznacza koniec wpisów mapy parametrów.|
|[SET_PARAM_TYPE](#set_param_type)|Określa COLUMN_ENTRY makra, które podążają za makra SET_PARAM_TYPE jako wejście, wyjście lub wejście/wyjście.|

### <a name="atltraceerrorrecords"></a><a name="atltraceerrorrecords"></a>AtlTraceErrorRecords (Rekordy AtlTraceError)

Zrzuca informacje o rekordzie błędu OLE DB do urządzenia zrzutu, jeśli zostanie zwrócony błąd.

#### <a name="syntax"></a>Składnia

```cpp
inline void AtlTraceErrorRecords(HRESULT hrErr = S_OK);
```

#### <a name="parameters"></a>Parametry

*Herr*<br/>
[w] HRESULT zwrócony przez funkcję członkowską szablonu konsumenta OLE DB.

#### <a name="remarks"></a>Uwagi

Jeśli *hErr* nie jest `AtlTraceErrorRecords` S_OK, zrzuca informacje o rekordzie błędu OLE DB do urządzenia zrzutu (karta **Debugowanie** okna dane wyjściowe lub pliku). Informacje o rekordzie błędu, które są uzyskiwane od dostawcy, obejmują numer wiersza, źródło, opis, plik pomocy, kontekst i identyfikator GUID dla każdego wpisu rekordu błędu. `AtlTraceErrorRecords`zrzuca te informacje tylko w kompilacjach debugowania. W kompilacjach wydania jest pusty skrót, który jest zoptymalizowany. Aby uzyskać więcej informacji, zobacz [CDBErrorInfo Class](../../data/oledb/cdberrorinfo-class.md).

### <a name="begin_accessor"></a><a name="begin_accessor"></a>BEGIN_ACCESSOR

Oznacza początek wpisu akcesora.

#### <a name="syntax"></a>Składnia

```cpp
BEGIN_ACCESSOR(num, bAuto)
```

#### <a name="parameters"></a>Parametry

*num*<br/>
[w] Liczba odsunięcia zerowego dla akcesora na tej mapie akcesora.

*bUto*<br/>
[w] Określa, czy ten akcesor jest automatycznym akcesorem, czy ręcznym akcesorem. Jeśli **true**, akcesor jest auto; jeśli **false**, akcesor jest ręczny. Automatyczny akcesor oznacza, że dane są pobierane dla Ciebie podczas operacji w ruchu.

#### <a name="remarks"></a>Uwagi

W przypadku wielu akcesorów w zestawie wierszy należy określić BEGIN_ACCESSOR_MAP i użyć makra BEGIN_ACCESSOR dla każdego akcesora. Makro BEGIN_ACCESSOR zostanie uzupełniony makro END_ACCESSOR. Makro BEGIN_ACCESSOR_MAP zostanie uzupełniony makro END_ACCESSOR_MAP.

#### <a name="example"></a>Przykład

Zobacz [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="begin_accessor_map"></a><a name="begin_accessor_map"></a>BEGIN_ACCESSOR_MAP

Oznacza początek wpisów mapy akcesora.

#### <a name="syntax"></a>Składnia

```cpp
BEGIN_ACCESSOR_MAP(x, num)
```

#### <a name="parameters"></a>Parametry

*X*<br/>
[w] Nazwa klasy rekordu użytkownika.

*num*<br/>
[w] Liczba akcesorów na tej mapie akcesorowej.

#### <a name="remarks"></a>Uwagi

W przypadku wielu akcesorów w zestawie wierszy należy określić BEGIN_ACCESSOR_MAP na początku i użyć makra BEGIN_ACCESSOR dla każdego akcesora. Makro BEGIN_ACCESSOR zostanie uzupełniony makro END_ACCESSOR. Mapa akcesora zostanie uzupełniona END_ACCESSOR_MAP makra.

Jeśli w rekordzie użytkownika jest tylko jeden akcesor, użyj [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)makra .

#### <a name="example"></a>Przykład

```cpp
class CArtistsAccessor
{
public:
// Data Elements
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];
   short m_nAge;

// Output binding map
BEGIN_ACCESSOR_MAP(CArtistsAccessor, 2)
   BEGIN_ACCESSOR(0, true)
      COLUMN_ENTRY(1, m_szFirstName)
      COLUMN_ENTRY(2, m_szLastName)
   END_ACCESSOR()
   BEGIN_ACCESSOR(1, false) // Not an auto accessor
      COLUMN_ENTRY(3, m_nAge)
   END_ACCESSOR()
END_ACCESSOR_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsAccessor, L" \
   SELECT \
      FirstName, \
      LastName, \
      Age \
      FROM Artists")
};
```

### <a name="end_accessor"></a><a name="end_accessor"></a>END_ACCESSOR

Oznacza koniec wpisu akcesora.

#### <a name="syntax"></a>Składnia

```cpp
END_ACCESSOR()
```

#### <a name="remarks"></a>Uwagi

W przypadku wielu akcesorów w zestawie wierszy należy określić BEGIN_ACCESSOR_MAP i użyć makra BEGIN_ACCESSOR dla każdego akcesora. Makro BEGIN_ACCESSOR zostanie uzupełniony makro END_ACCESSOR. Makro BEGIN_ACCESSOR_MAP zostanie uzupełniony makro END_ACCESSOR_MAP.

#### <a name="example"></a>Przykład

Zobacz [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="end_accessor_map"></a><a name="end_accessor_map"></a>END_ACCESSOR_MAP

Oznacza koniec wpisów mapy akcesora.

#### <a name="syntax"></a>Składnia

```cpp
END_ACCESSOR_MAP()
```

#### <a name="remarks"></a>Uwagi

W przypadku wielu akcesorów w zestawie wierszy należy określić BEGIN_ACCESSOR_MAP i użyć makra BEGIN_ACCESSOR dla każdego akcesora. Makro BEGIN_ACCESSOR zostanie uzupełniony makro END_ACCESSOR. Makro BEGIN_ACCESSOR_MAP zostanie uzupełniony makro END_ACCESSOR_MAP.

#### <a name="example"></a>Przykład

Zobacz [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="begin_column_map"></a><a name="begin_column_map"></a>BEGIN_COLUMN_MAP

Oznacza początek wpisu mapy kolumny.

#### <a name="syntax"></a>Składnia

```cpp
BEGIN_COLUMN_MAP(x)
```

#### <a name="parameters"></a>Parametry

*X*<br/>
[w] Nazwa klasy rekordu użytkownika pochodząca `CAccessor`od .

#### <a name="remarks"></a>Uwagi

To makro jest używane w przypadku pojedynczego akcesora w zestawie wierszy. Jeśli masz wiele akcesorów w zestawie wierszy, użyj [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

Makro BEGIN_COLUMN_MAP zostanie uzupełniony makro END_COLUMN_MAP. To makro jest używane, gdy w rekordzie użytkownika jest wymagany tylko jeden akcesor.

Kolumny odpowiadają polom w zestawie wierszy, które chcesz powiązać.

#### <a name="example"></a>Przykład

Oto przykładowa kolumna i mapa parametrów:

<!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->

### <a name="blob_entry"></a><a name="blob_entry"></a>BLOB_ENTRY

Używany z BEGIN_COLUMN_MAP i END_COLUMN_MAP do powiązania dużego obiektu binarnego ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))).

#### <a name="syntax"></a>Składnia

```cpp
BLOB_ENTRY(nOrdinal, IID, flags, data)
```

#### <a name="parameters"></a>Parametry

*nOrminalne*<br/>
[w] Numer kolumny.

*Iid*<br/>
[w] Identyfikator GUID interfejsu, taki jak `IDD_ISequentialStream`, używany do pobierania obiektu BLOB.

*flagi*<br/>
[w] Flagi trybu magazynowania zdefiniowane przez model przechowywania strukturalnego OLE (na przykład `STGM_READ`).

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="example"></a>Przykład

Zobacz [Jak pobrać obiekt BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_length"></a><a name="blob_entry_length"></a>BLOB_ENTRY_LENGTH

Używany z BEGIN_COLUMN_MAP i END_COLUMN_MAP do powiązania dużego obiektu binarnego ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobnie [jak BLOB_ENTRY](../../data/oledb/blob-entry.md), z tą różnicą, że to makro pobiera również długość w bajtach kolumny BLOB.

#### <a name="syntax"></a>Składnia

```cpp
BLOB_ENTRY_LENGTH(nOrdinal, IID, flags, data, length)
```

#### <a name="parameters"></a>Parametry

*nOrminalne*<br/>
[w] Numer kolumny.

*Iid*<br/>
[w] Identyfikator GUID interfejsu, taki jak `IDD_ISequentialStream`, używany do pobierania obiektu BLOB.

*flagi*<br/>
[w] Flagi trybu magazynowania zdefiniowane przez model przechowywania strukturalnego OLE (na przykład `STGM_READ`).

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[na zewnątrz] Długość (rzeczywista) w bajtach kolumny BLOB.

#### <a name="example"></a>Przykład

Zobacz [Jak pobrać obiekt BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_length_status"></a><a name="blob_entry_length_status"></a>BLOB_ENTRY_LENGTH_STATUS

Używany z BEGIN_COLUMN_MAP i END_COLUMN_MAP do powiązania dużego obiektu binarnego ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobnie [jak BLOB_ENTRY](../../data/oledb/blob-entry.md), z tą różnicą, że to makro pobiera również długość i stan kolumny blob.

#### <a name="syntax"></a>Składnia

```cpp
BLOB_ENTRY_LENGTH_STATUS(
    nOrdinal,
    IID,
    flags,
    data,
    length,
    status )
```

#### <a name="parameters"></a>Parametry

*nOrminalne*<br/>
[w] Numer kolumny.

*Iid*<br/>
[w] Identyfikator GUID interfejsu, taki jak `IDD_ISequentialStream`, używany do pobierania obiektu BLOB.

*flagi*<br/>
[w] Flagi trybu magazynowania zdefiniowane przez model przechowywania strukturalnego OLE (na przykład `STGM_READ`).

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[na zewnątrz] Długość (rzeczywista) w bajtach kolumny BLOB.

*Stan*<br/>
[na zewnątrz] Stan kolumny danych obiektu BLOB.

#### <a name="example"></a>Przykład

Zobacz [Jak pobrać obiekt BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_status"></a><a name="blob_entry_status"></a>BLOB_ENTRY_STATUS

Używany z BEGIN_COLUMN_MAP lub BEGIN_ACCESSOR_MAP do powiązania dużego obiektu binarnego ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobnie [jak BLOB_ENTRY](../../data/oledb/blob-entry.md), z tą różnicą, że to makro pobiera również stan kolumny blob.

#### <a name="syntax"></a>Składnia

```cpp
BLOB_ENTRY_STATUS(nOrdinal, IID, flags, data, status)
```

#### <a name="parameters"></a>Parametry

*nOrminalne*<br/>
[w] Numer kolumny.

*Iid*<br/>
[w] Identyfikator GUID interfejsu, taki jak `IDD_ISequentialStream`, używany do pobierania obiektu BLOB.

*flagi*<br/>
[w] Flagi trybu magazynowania zdefiniowane przez model przechowywania strukturalnego OLE (na przykład `STGM_READ`).

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Stan*<br/>
[na zewnątrz] Stan pola BLOB.

#### <a name="example"></a>Przykład

Zobacz [Jak pobrać obiekt BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_name"></a><a name="blob_name"></a>BLOB_NAME

Używany z BEGIN_COLUMN_MAP i END_COLUMN_MAP do powiązania dużego obiektu binarnego ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobnie [jak BLOB_ENTRY](../../data/oledb/blob-entry.md), z tą różnicą, że to makro przyjmuje nazwę kolumny zamiast numeru kolumny.

#### <a name="syntax"></a>Składnia

```cpp
BLOB_NAME(pszName, IID, flags, data )
```

#### <a name="parameters"></a>Parametry

*pszName (Nazwa psz)*<br/>
[w] Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć, umieszczając "L" przed nazwą, na `L"MyColumn"`przykład: .

*Iid*<br/>
[w] Identyfikator GUID interfejsu, taki jak `IDD_ISequentialStream`, używany do pobierania obiektu BLOB.

*flagi*<br/>
[w] Flagi trybu magazynowania zdefiniowane przez model przechowywania strukturalnego OLE (na przykład `STGM_READ`).

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="example"></a>Przykład

Zobacz [Jak pobrać obiekt BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_name_length"></a><a name="blob_name_length"></a>BLOB_NAME_LENGTH

Używany z BEGIN_COLUMN_MAP i END_COLUMN_MAP do powiązania dużego obiektu binarnego ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobnie [jak BLOB_NAME](../../data/oledb/blob-name.md), z tą różnicą, że to makro pobiera również długość w bajtach kolumny danych obiektu BLOB.

#### <a name="syntax"></a>Składnia

```cpp
BLOB_NAME_LENGTH(pszName, IID, flags, data, length )
```

#### <a name="parameters"></a>Parametry

*pszName (Nazwa psz)*<br/>
[w] Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć, umieszczając "L" przed nazwą, na `L"MyColumn"`przykład: .

*Iid*<br/>
[w] Identyfikator GUID interfejsu, taki jak `IDD_ISequentialStream`, używany do pobierania obiektu BLOB.

*flagi*<br/>
[w] Flagi trybu magazynowania zdefiniowane przez model przechowywania strukturalnego OLE (na przykład `STGM_READ`).

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[na zewnątrz] Długość (rzeczywista) w bajtach kolumny BLOB.

### <a name="blob_name_length_status"></a><a name="blob_name_length_status"></a>BLOB_NAME_LENGTH_STATUS

Używany z BEGIN_COLUMN_MAP i END_COLUMN_MAP do powiązania dużego obiektu binarnego ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobnie [jak BLOB_NAME](../../data/oledb/blob-name.md), z tą różnicą, że to makro pobiera również długość i stan kolumny danych obiektu BLOB.

#### <a name="syntax"></a>Składnia

```cpp
BLOB_NAME_LENGTH_STATUS(pszName, IID, flags, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName (Nazwa psz)*<br/>
[w] Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć, umieszczając "L" przed nazwą, na `L"MyColumn"`przykład: .

*Iid*<br/>
[w] Identyfikator GUID interfejsu, taki jak `IDD_ISequentialStream`, używany do pobierania obiektu BLOB.

*flagi*<br/>
[w] Flagi trybu magazynowania zdefiniowane przez model przechowywania strukturalnego OLE (na przykład `STGM_READ`).

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[na zewnątrz] Długość (rzeczywista) w bajtach kolumny BLOB.

*Stan*<br/>
[na zewnątrz] Stan pola BLOB.

### <a name="blob_name_status"></a><a name="blob_name_status"></a>BLOB_NAME_STATUS

Używany z BEGIN_COLUMN_MAP i END_COLUMN_MAP do powiązania dużego obiektu binarnego ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobnie [jak BLOB_NAME](../../data/oledb/blob-name.md), z tą różnicą, że to makro pobiera również stan kolumny danych obiektu BLOB.

#### <a name="syntax"></a>Składnia

```cpp
BLOB_NAME_STATUS(pszName, IID, flags, data, status )
```

#### <a name="parameters"></a>Parametry

*pszName (Nazwa psz)*<br/>
[w] Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć, umieszczając "L" przed nazwą, na `L"MyColumn"`przykład: .

*Iid*<br/>
[w] Identyfikator GUID interfejsu, taki jak `IDD_ISequentialStream`, używany do pobierania obiektu BLOB.

*flagi*<br/>
[w] Flagi trybu magazynowania zdefiniowane przez model przechowywania strukturalnego OLE (na przykład `STGM_READ`).

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Stan*<br/>
[na zewnątrz] Stan pola BLOB.

### <a name="bookmark_entry"></a><a name="bookmark_entry"></a>BOOKMARK_ENTRY

Wiąże kolumnę zakładki.

#### <a name="syntax"></a>Składnia

```cpp
BOOKMARK_ENTRY(variable)
```

#### <a name="parameters"></a>Parametry

*Zmiennej*<br/>
[w] Zmienna, która ma być powiązana z kolumną zakładki.

#### <a name="example"></a>Przykład

```cpp
class CArtistsBookmark
{
public:
// Data Elements
   CBookmark<4> m_bookmark;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

// Output binding map
BEGIN_COLUMN_MAP(CArtistsBookmark)
   BOOKMARK_ENTRY(m_bookmark)
   COLUMN_ENTRY(1, m_nAge)
   COLUMN_ENTRY(2, m_szFirstName)
   COLUMN_ENTRY(3, m_szLastName)
END_COLUMN_MAP()

   void GetRowsetProperties(CDBPropSet* pPropSet)
   {
      pPropSet->AddProperty(DBPROP_BOOKMARKS, true);
   }

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsBookmark, L" \
   SELECT \
      Age, \
      FirstName, \
      LastName \
      FROM Artists")
};
```

Aby uzyskać więcej informacji, zobacz [Korzystanie z zakładek](using-bookmarks.md) i [CBookmark Class](../../data/oledb/cbookmark-class.md).

### <a name="column_entry"></a><a name="column_entry"></a>COLUMN_ENTRY

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY(nOrdinal, data)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *referencje programisty OLE DB*.

*nOrminalne*<br/>
[w] Numer kolumny.

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

Makro COLUMN_ENTRY jest używane w następujących miejscach:

- Między [makrami BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Między [makrami BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Między [makrami BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP.](../../data/oledb/end-param-map.md)

#### <a name="example"></a>Przykład

Zobacz przykłady w tematach makr, [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="column_entry_ex"></a><a name="column_entry_ex"></a>COLUMN_ENTRY_EX

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w bazie danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_EX(nOrdinal, wType, nLength, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *referencje programisty OLE DB*.

*nOrminalne*<br/>
[w] Numer kolumny.

*Wtype*<br/>
[w] Typ danych.

*nLength (nLength)*<br/>
[w] Rozmiar danych w bajtach.

*nPrecision (precision )*<br/>
[w] Maksymalna precyzja używana podczas uzyskiwania `DBTYPE_NUMERIC`danych i *wType* to . W przeciwnym razie ten parametr jest ignorowany.

*nSkada*<br/>
[w] Skala do użycia podczas uzyskiwania `DBTYPE_NUMERIC` `DBTYPE_DECIMAL`danych i *wType* jest lub .

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[w] Zmienna, która ma być powiązana z długością kolumny.

*Stan*<br/>
[w] Zmienna, która ma być powiązana ze stanem kolumny.

#### <a name="remarks"></a>Uwagi

Makro COLUMN_ENTRY_EX jest używane w następujących miejscach:

- Między [makrami BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Między [makrami BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Między [makrami BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP.](../../data/oledb/end-param-map.md)

#### <a name="example"></a>Przykład

Zobacz [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="column_entry_length"></a><a name="column_entry_length"></a>COLUMN_ENTRY_LENGTH

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w bazie danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_LENGTH(nOrdinal, data, length)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *referencje programisty OLE DB*.

*nOrminalne*<br/>
[w] Numer kolumny, zaczynając od jednego. Zakładka odpowiada kolumnie zero.

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[w] Zmienna, która ma być powiązana z długością kolumny.

#### <a name="remarks"></a>Uwagi

To makro obsługuje zmienną *długości.* Jest on stosowany w następujących miejscach:

- Między [makrami BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Między [makrami BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Między [makrami BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP.](../../data/oledb/end-param-map.md)

### <a name="column_entry_length_status"></a><a name="column_entry_length_status"></a>COLUMN_ENTRY_LENGTH_STATUS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w bazie danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_LENGTH_STATUS(nOrdinal, data, length, status)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *referencje programisty OLE DB*.

*nOrminalne*<br/>
[w] Numer kolumny.

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[w] Zmienna, która ma być powiązana z długością kolumny.

*Stan*<br/>
[w] Zmienna, która ma być powiązana ze stanem kolumny.

#### <a name="remarks"></a>Uwagi

To makro służy do obsługi zmiennych długości i stanu. Jest on stosowany w następujących miejscach:

- Między [makrami BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Między [makrami BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Między [makrami BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP.](../../data/oledb/end-param-map.md)

### <a name="column_entry_ps"></a><a name="column_entry_ps"></a>COLUMN_ENTRY_PS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_PS(nOrdinal, nPrecision, nScale, data)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *referencje programisty OLE DB*.

*nOrminalne*<br/>
[w] Numer kolumny.

*nPrecision (precision )*<br/>
[w] Maksymalna dokładność kolumny, którą chcesz powiązać.

*nSkada*<br/>
[w] Skala kolumny, którą chcesz powiązać.

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

Umożliwia określenie precyzji i skali kolumny, którą chcesz powiązać. Jest on stosowany w następujących miejscach:

- Między [makrami BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Między [makrami BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Między [makrami BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP.](../../data/oledb/end-param-map.md)

### <a name="column_entry_ps_length"></a><a name="column_entry_ps_length"></a>COLUMN_ENTRY_PS_LENGTH

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w bazie danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_PS_LENGTH(nOrdinal, nPrecision, nScale, data, length)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *referencje programisty OLE DB*.

*nOrminalne*<br/>
[w] Numer kolumny, zaczynając od jednego. Zakładka odpowiada kolumnie zero.

*nPrecision (precision )*<br/>
[w] Maksymalna dokładność kolumny, którą chcesz powiązać.

*nSkada*<br/>
[w] Skala kolumny, którą chcesz powiązać.

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[w] Zmienna, która ma być powiązana z długością kolumny.

#### <a name="remarks"></a>Uwagi

Umożliwia określenie precyzji i skali kolumny, którą chcesz powiązać. To makro obsługuje zmienną *długości.* Jest on stosowany w następujących miejscach:

- Między [makrami BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Między [makrami BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Między [makrami BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP.](../../data/oledb/end-param-map.md)

### <a name="column_entry_ps_length_status"></a><a name="column_entry_ps_length_status"></a>COLUMN_ENTRY_PS_LENGTH_STATUS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w bazie danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_PS_LENGTH_STATUS(nOrdinal, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *referencje programisty OLE DB*.

*nOrminalne*<br/>
[w] Numer kolumny.

*nPrecision (precision )*<br/>
[w] Maksymalna dokładność kolumny, którą chcesz powiązać.

*nSkada*<br/>
[w] Skala kolumny, którą chcesz powiązać.

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[w] Zmienna, która ma być powiązana z długością kolumny.

*Stan*<br/>
[w] Zmienna, która ma być powiązana ze stanem kolumny.

#### <a name="remarks"></a>Uwagi

Umożliwia określenie precyzji i skali kolumny, którą chcesz powiązać. To makro służy do obsługi zmiennych długości i stanu. Jest on stosowany w następujących miejscach:

- Między [makrami BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Między [makrami BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Między [makrami BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP.](../../data/oledb/end-param-map.md)

### <a name="column_entry_ps_status"></a><a name="column_entry_ps_status"></a>COLUMN_ENTRY_PS_STATUS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w bazie danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_PS_STATUS(nOrdinal, nPrecision, nScale, data, status)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *referencje programisty OLE DB*.

*nOrminalne*<br/>
[w] Numer kolumny.

*nPrecision (precision )*<br/>
[w] Maksymalna dokładność kolumny, którą chcesz powiązać.

*nSkada*<br/>
[w] Skala kolumny, którą chcesz powiązać.

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Stan*<br/>
[w] Zmienna, która ma być powiązana ze stanem kolumny.

#### <a name="remarks"></a>Uwagi

Umożliwia określenie precyzji i skali kolumny, którą chcesz powiązać. To makro obsługuje zmienną *stanu.* Jest on stosowany w następujących miejscach:

- Między [makrami BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Między [makrami BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Między [makrami BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP.](../../data/oledb/end-param-map.md)

### <a name="column_entry_status"></a><a name="column_entry_status"></a>COLUMN_ENTRY_STATUS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w bazie danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_STATUS(nOrdinal, data, status)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *referencje programisty OLE DB*.

*nOrminalne*<br/>
[w] Numer kolumny.

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Stan*<br/>
[w] Zmienna, która ma być powiązana ze stanem kolumny.

#### <a name="remarks"></a>Uwagi

To makro obsługuje zmienną *stanu.* Jest on stosowany w następujących miejscach:

- Między [makrami BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Między [makrami BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Między [makrami BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP.](../../data/oledb/end-param-map.md)

### <a name="column_entry_type"></a><a name="column_entry_type"></a>COLUMN_ENTRY_TYPE

Reprezentuje powiązanie z określonej kolumny w bazie danych. Obsługuje parametr *typu.*

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_TYPE (nOrdinal, wType, data)
```

#### <a name="parameters"></a>Parametry

*nOrminalne*<br/>
[w] Numer kolumny.

*Wtype*<br/>
[w] Typ danych wpisu kolumny.

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

To makro jest wyspecjalizowanym wariantem [makra COLUMN_ENTRY,](../../data/oledb/column-entry.md) który zapewnia sposób określania typu danych.

### <a name="column_entry_type_size"></a><a name="column_entry_type_size"></a>COLUMN_ENTRY_TYPE_SIZE

Reprezentuje powiązanie z określonej kolumny w bazie danych. Obsługuje parametry *typu* i *rozmiaru.*

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)
```

#### <a name="parameters"></a>Parametry

*nOrminalne*<br/>
[w] Numer kolumny.

*Wtype*<br/>
[w] Typ danych wpisu kolumny.

*nLength (nLength)*<br/>
[w] Rozmiar wpisu kolumny w bajtach.

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

To makro jest wyspecjalizowanym wariantem [makra COLUMN_ENTRY,](../../data/oledb/column-entry.md) który zapewnia sposób określania rozmiaru i typu danych.

### <a name="column_name"></a><a name="column_name"></a>Column_name

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie [jak COLUMN_ENTRY](../../data/oledb/column-entry.md), z tą różnicą, że to makro przyjmuje nazwę kolumny zamiast numeru kolumny.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME(pszName, data)
```

#### <a name="parameters"></a>Parametry

*pszName (Nazwa psz)*<br/>
[w] Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć, umieszczając "L" przed nazwą, na `L"MyColumn"`przykład: .

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

Makra COLUMN_NAME_* są używane w tych samych miejscach, [w COLUMN_ENTRY:](../../data/oledb/column-entry.md)

- Między [makrami BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Między [makrami BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR.](../../data/oledb/end-accessor.md)

- Między [makrami BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP.](../../data/oledb/end-param-map.md)

### <a name="column_name_ex"></a><a name="column_name_ex"></a>COLUMN_NAME_EX

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie [jak COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że to makro przyjmuje również typ danych, rozmiar, dokładność, skalę, długość kolumny i stan kolumny.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_EX(pszName, wType, nLength, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName (Nazwa psz)*<br/>
[w] Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć, umieszczając "L" przed nazwą, na `L"MyColumn"`przykład: .

*Wtype*<br/>
[w] Typ danych.

*nLength (nLength)*<br/>
[w] Rozmiar danych w bajtach.

*nPrecision (precision )*<br/>
[w] Maksymalna precyzja używana podczas uzyskiwania `DBTYPE_NUMERIC`danych i *wType* to . W przeciwnym razie ten parametr jest ignorowany.

*nSkada*<br/>
[w] Skala do użycia podczas uzyskiwania `DBTYPE_NUMERIC` `DBTYPE_DECIMAL`danych i *wType* jest lub .

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[w] Zmienna, która ma być powiązana z długością kolumny.

*Stan*<br/>
[w] Zmienna, która ma być powiązana ze stanem kolumny.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME,](../../data/oledb/column-name.md) aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_*.

### <a name="column_name_length"></a><a name="column_name_length"></a>COLUMN_NAME_LENGTH

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie [jak COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że to makro ma również długość kolumny.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_LENGTH(pszName, data, length)
```

#### <a name="parameters"></a>Parametry

*pszName (Nazwa psz)*<br/>
[w] Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć, umieszczając "L" przed nazwą, na `L"MyColumn"`przykład: .

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[w] Zmienna, która ma być powiązana z długością kolumny.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME,](../../data/oledb/column-name.md) aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_*.

### <a name="column_name_length_status"></a><a name="column_name_length_status"></a>COLUMN_NAME_LENGTH_STATUS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie [jak COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że to makro ma również długość kolumny i stan kolumny.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_LENGTH_STATUS(pszName, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName (Nazwa psz)*<br/>
[w] Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć, umieszczając "L" przed nazwą, na `L"MyColumn"`przykład: .

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[w] Zmienna, która ma być powiązana z długością kolumny.

*Stan*<br/>
[w] Zmienna, która ma być powiązana ze stanem kolumny.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME,](../../data/oledb/column-name.md) aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_*.

### <a name="column_name_ps"></a><a name="column_name_ps"></a>COLUMN_NAME_PS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie [jak COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że makro ma również precyzję i skalę.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_PS(pszName, nPrecision, nScale, data )
```

#### <a name="parameters"></a>Parametry

*pszName (Nazwa psz)*<br/>
[w] Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć, umieszczając "L" przed nazwą, na `L"MyColumn"`przykład: .

*nPrecision (precision )*<br/>
[w] Maksymalna dokładność kolumny, którą chcesz powiązać.

*nSkada*<br/>
[w] Skala kolumny, którą chcesz powiązać.

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME,](../../data/oledb/column-name.md) aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_*.

### <a name="column_name_ps_length"></a><a name="column_name_ps_length"></a>COLUMN_NAME_PS_LENGTH

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie [jak COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że makro ma również dokładność, skalę i długość kolumny.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_PS_LENGTH(pszName, nPrecision, nScale, data, length )
```

#### <a name="parameters"></a>Parametry

*pszName (Nazwa psz)*<br/>
[w] Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć, umieszczając "L" przed nazwą, na `L"MyColumn"`przykład: .

*nPrecision (precision )*<br/>
[w] Maksymalna dokładność kolumny, którą chcesz powiązać.

*nSkada*<br/>
[w] Skala kolumny, którą chcesz powiązać.

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[w] Zmienna, która ma być powiązana z długością kolumny.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME,](../../data/oledb/column-name.md) aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_*.

### <a name="column_name_ps_length_status"></a><a name="column_name_ps_length_status"></a>COLUMN_NAME_PS_LENGTH_STATUS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie [jak COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że to makro ma również dokładność, skalę, długość kolumny i stan kolumny.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_PS_LENGTH_STATUS(pszName, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName (Nazwa psz)*<br/>
[w] Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć, umieszczając "L" przed nazwą, na `L"MyColumn"`przykład: .

*nPrecision (precision )*<br/>
[w] Maksymalna dokładność kolumny, którą chcesz powiązać.

*nSkada*<br/>
[w] Skala kolumny, którą chcesz powiązać.

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[w] Zmienna, która ma być powiązana z długością kolumny.

*Stan*<br/>
[w] Zmienna, która ma być powiązana ze stanem kolumny.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME,](../../data/oledb/column-name.md) aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_*.

### <a name="column_name_ps_status"></a><a name="column_name_ps_status"></a>COLUMN_NAME_PS_STATUS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie [jak COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że to makro ma również stan precyzji, skali i kolumny.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_PS_STATUS(pszName, nPrecision, nScale, data, status )
```

#### <a name="parameters"></a>Parametry

*pszName (Nazwa psz)*<br/>
[w] Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć, umieszczając "L" przed nazwą, na `L"MyColumn"`przykład: .

*nPrecision (precision )*<br/>
[w] Maksymalna dokładność kolumny, którą chcesz powiązać.

*nSkada*<br/>
[w] Skala kolumny, którą chcesz powiązać.

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Stan*<br/>
[w] Zmienna, która ma być powiązana ze stanem kolumny.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME,](../../data/oledb/column-name.md) aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_*.

### <a name="column_name_status"></a><a name="column_name_status"></a>COLUMN_NAME_STATUS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie [jak COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że to makro ma również stan kolumny.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_STATUS(pszName, data, status )
```

#### <a name="parameters"></a>Parametry

*pszName (Nazwa psz)*<br/>
[w] Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć, umieszczając "L" przed nazwą, na `L"MyColumn"`przykład: .

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Stan*<br/>
[w] Zmienna, która ma być powiązana ze stanem kolumny.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME,](../../data/oledb/column-name.md) aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_*.

### <a name="column_name_type"></a><a name="column_name_type"></a>COLUMN_NAME_TYPE

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie [jak COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że to makro przyjmuje również typ danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_TYPE(pszName, wType, data)
```

#### <a name="parameters"></a>Parametry

*pszName (Nazwa psz)*<br/>
[w] Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć, umieszczając "L" przed nazwą, na `L"MyColumn"`przykład: .

*Wtype*<br/>
[w] Typ danych.

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME,](../../data/oledb/column-name.md) aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_*.

### <a name="column_name_type_ps"></a><a name="column_name_type_ps"></a>COLUMN_NAME_TYPE_PS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie [jak COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że to makro przyjmuje również typ danych, precyzję i skalę.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_TYPE_PS(pszName, wType, nPrecision, nScale, data)
```

#### <a name="parameters"></a>Parametry

*pszName (Nazwa psz)*<br/>
[w] Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć, umieszczając "L" przed nazwą, na `L"MyColumn"`przykład: .

*Wtype*<br/>
[w] Typ danych.

*nPrecision (precision )*<br/>
[w] Maksymalna precyzja używana podczas uzyskiwania `DBTYPE_NUMERIC`danych i *wType* to . W przeciwnym razie ten parametr jest ignorowany.

*nSkada*<br/>
[w] Skala do użycia podczas uzyskiwania `DBTYPE_NUMERIC` `DBTYPE_DECIMAL`danych i *wType* jest lub .

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME,](../../data/oledb/column-name.md) aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_*.

### <a name="column_name_type_size"></a><a name="column_name_type_size"></a>COLUMN_NAME_TYPE_SIZE

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie [jak COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że to makro przyjmuje również typ i rozmiar danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_TYPE_SIZE(pszName, wType, nLength, data)
```

#### <a name="parameters"></a>Parametry

*pszName (Nazwa psz)*<br/>
[w] Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć, umieszczając "L" przed nazwą, na `L"MyColumn"`przykład: .

*Wtype*<br/>
[w] Typ danych.

*nLength (nLength)*<br/>
[w] Rozmiar danych w bajtach.

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME,](../../data/oledb/column-name.md) aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_*.

### <a name="column_name_type_status"></a><a name="column_name_type_status"></a>COLUMN_NAME_TYPE_STATUS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie [jak COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że to makro przyjmuje również typ danych i stan kolumny.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_TYPE_STATUS(pszName, wType, status, data)
```

#### <a name="parameters"></a>Parametry

*pszName (Nazwa psz)*<br/>
[w] Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć, umieszczając "L" przed nazwą, na `L"MyColumn"`przykład: .

*Wtype*<br/>
[w] Typ danych.

*Stan*<br/>
[w] Zmienna, która ma być powiązana ze stanem kolumny.

*Danych*<br/>
[w] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME,](../../data/oledb/column-name.md) aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_*.

### <a name="end_column_map"></a><a name="end_column_map"></a>END_COLUMN_MAP

Oznacza koniec wpisów mapy kolumn.

#### <a name="syntax"></a>Składnia

```cpp
END_COLUMN_MAP()
```

#### <a name="remarks"></a>Uwagi

Jest on używany z jednym akcesorem na zestawie wierszy. Makro BEGIN_COLUMN_MAP zostanie uzupełniony makro END_COLUMN_MAP.

#### <a name="example"></a>Przykład

Zobacz [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md).

### <a name="define_command"></a><a name="define_command"></a>DEFINE_COMMAND

Określa polecenie, które będzie używane do tworzenia zestawu wierszy podczas korzystania z klasy [CCommand.](../../data/oledb/ccommand-class.md) Akceptuje tylko typy ciągów pasujące do określonego typu aplikacji (ANSI lub Unicode).

> [!NOTE]
> Zaleca się stosowanie [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) zamiast DEFINE_COMMAND.

#### <a name="syntax"></a>Składnia

```cpp
DEFINE_COMMAND(x, szCommand)
```

#### <a name="parameters"></a>Parametry

*X*<br/>
[w] Nazwa klasy rekordu użytkownika (polecenia).

*szCommand ( szCommand )*<br/>
[w] Ciąg polecenia, który będzie używany do tworzenia zestawu wierszy podczas korzystania z [CCommand](../../data/oledb/ccommand-class.md).

#### <a name="remarks"></a>Uwagi

Określony ciąg poleceń będzie używany jako domyślny, jeśli tekst polecenia nie zostanie określony w [metodzie CCommand::Open.](../../data/oledb/ccommand-open.md)

To makro akceptuje ciągi ANSI, jeśli tworzysz aplikację jako ANSI lub ciągi Unicode, jeśli tworzysz aplikację jako Unicode. Zaleca się używanie [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) zamiast DEFINE_COMMAND, ponieważ pierwszy akceptuje ciągi Unicode, niezależnie od typu aplikacji ANSI lub Unicode.

#### <a name="example"></a>Przykład

Zobacz [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="define_command_ex"></a><a name="define_command_ex"></a>DEFINE_COMMAND_EX

Określa polecenie, które będzie używane do tworzenia zestawu wierszy podczas korzystania z klasy [CCommand.](../../data/oledb/ccommand-class.md) Obsługuje aplikacje Unicode i ANSI.

#### <a name="syntax"></a>Składnia

```cpp
DEFINE_COMMAND_EX(x, wszCommand)
```

#### <a name="parameters"></a>Parametry

*X*<br/>
[w] Nazwa klasy rekordu użytkownika (polecenia).

*wszCommand*<br/>
[w] Ciąg polecenia, który będzie używany do tworzenia zestawu wierszy podczas korzystania z [CCommand](../../data/oledb/ccommand-class.md).

#### <a name="remarks"></a>Uwagi

Określony ciąg poleceń będzie używany jako domyślny, jeśli tekst polecenia nie zostanie określony w [metodzie CCommand::Open.](../../data/oledb/ccommand-open.md)

To makro akceptuje ciągi Unicode, niezależnie od typu aplikacji. To makro jest preferowane niż [DEFINE_COMMAND,](../../data/oledb/define-command.md) ponieważ obsługuje unicode, a także aplikacje ANSI.

#### <a name="example"></a>Przykład

Zobacz [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="begin_param_map"></a><a name="begin_param_map"></a>BEGIN_PARAM_MAP

Oznacza początek wpisów mapy parametrów.

#### <a name="syntax"></a>Składnia

```cpp
BEGIN_PARAM_MAP(x)
```

#### <a name="parameters"></a>Parametry

*X*<br/>
[w] Nazwa klasy rekordu użytkownika.

#### <a name="remarks"></a>Uwagi

Parametry są używane przez [polecenia](/previous-versions/windows/desktop/ms724608(v=vs.85)).

#### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) makra.

### <a name="end_param_map"></a><a name="end_param_map"></a>END_PARAM_MAP

Oznacza koniec wpisów mapy parametrów.

#### <a name="syntax"></a>Składnia

```cpp
END_PARAM_MAP()
```

#### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) makra.

### <a name="set_param_type"></a><a name="set_param_type"></a>SET_PARAM_TYPE

Określa COLUMN_ENTRY makra, które podążają za SET_PARAM_TYPE wejście makra, wyjście lub wejście/wyjście.

#### <a name="syntax"></a>Składnia

```cpp
SET_PARAM_TYPE(type)
```

#### <a name="parameters"></a>Parametry

*Typu*<br/>
[w] Typ, który ma być ustawiony dla parametru.

#### <a name="remarks"></a>Uwagi

Dostawcy obsługują tylko typy wejściowych/wyjściowych parametrów, które są obsługiwane przez bazowe źródło danych. Typ jest kombinacją jednej `DBPARAMIO` lub więcej wartości (patrz [Struktura DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *referencji programisty OLE DB):*

- `DBPARAMIO_NOTPARAM`Akcesor nie ma parametrów. Zazwyczaj można ustawić `eParamIO` tę wartość w akcesorach wierszy, aby przypomnieć użytkownikowi, że parametry są ignorowane.

- `DBPARAMIO_INPUT`Parametr wejściowy.

- `DBPARAMIO_OUTPUT`Parametr wyjściowy.

- `DBPARAMIO_INPUT | DBPARAMIO_OUTPUT`Parametr jest zarówno parametrem wejściowym, jak i wyjściowym.

#### <a name="example"></a>Przykład

```cpp
class CArtistsProperty
{
public:
   short m_nReturn;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

BEGIN_PARAM_MAP(CArtistsProperty)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_nReturn)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_nAge)
END_PARAM_MAP()

BEGIN_COLUMN_MAP(CArtistsProperty)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
END_COLUMN_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsProperty, L" \
      { ? = SELECT Age FROM Artists WHERE Age < ? }")
};
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli.h

## <a name="see-also"></a>Zobacz też

[Makra i funkcje globalne dla szablonów dla odbiorców OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
[Szablony dla konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Dokumentacja szablonów dla konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
