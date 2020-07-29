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
ms.openlocfilehash: 0263289e75dc79ecf0b75e484b4bb97aede87ea7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232134"
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>Makra i funkcje globalne dla szablonów konsumentów OLE DB

Szablony konsumentów OLE DB obejmują następujące makra i funkcje globalne:

## <a name="global-functions"></a>Funkcje globalne

|||
|-|-|
|[AtlTraceErrorRecords](#atltraceerrorrecords)|Zrzuca OLE DB informacje o rekordzie błędu do urządzenia zrzutu w przypadku zwrócenia błędu.|

## <a name="accessor-map-macros"></a>Makra mapy metody dostępu

|||
|-|-|
|[BEGIN_ACCESSOR](#begin_accessor)|Oznacza początek wpisu metody dostępu.|
|[BEGIN_ACCESSOR_MAP](#begin_accessor_map)|Oznacza początek wpisów mapowania metody dostępu.|
|[END_ACCESSOR](#end_accessor)|Oznacza koniec wpisu metody dostępu.|
|[END_ACCESSOR_MAP](#end_accessor_map)|Oznacza koniec wpisów mapowania metody dostępu.|

## <a name="column-map-macros"></a>Makra mapy kolumn

|||
|-|-|
|[BEGIN_COLUMN_MAP](#begin_column_map)|Oznacza początek wpisów mapy kolumn w klasie rekordów użytkowników.|
|[BLOB_ENTRY](#blob_entry)|Służy do powiązania dużego obiektu binarnego (BLOB).|
|[BLOB_ENTRY_LENGTH](#blob_entry_length)|Raportuje długość kolumny danych obiektu BLOB.|
|[BLOB_ENTRY_LENGTH_STATUS](#blob_entry_length_status)|Raportuje długość i stan kolumny danych obiektu BLOB.|
|[BLOB_ENTRY_STATUS](#blob_entry_status)|Raportuje stan kolumny dane obiektu BLOB.|
|[BLOB_NAME](#blob_name)|Służy do powiązania binarnego dużego obiektu według nazwy kolumny.|
|[BLOB_NAME_LENGTH](#blob_name_length)|Raportuje długość kolumny danych obiektu BLOB.|
|[BLOB_NAME_LENGTH_STATUS](#blob_name_length_status)|Raportuje długość i stan kolumny danych obiektu BLOB.|
|[BLOB_NAME_STATUS](#blob_name_status)|Raportuje stan kolumny dane obiektu BLOB.|
|[BOOKMARK_ENTRY](#bookmark_entry)|Reprezentuje wpis zakładki w zestawie wierszy. Wpis zakładki jest specjalnym rodzajem wpisu kolumny.|
|[COLUMN_ENTRY](#column_entry)|Reprezentuje powiązanie z określoną kolumną w bazie danych.|
|[COLUMN_ENTRY_EX](#column_entry_ex)|Reprezentuje powiązanie z określoną kolumną w bazie danych. Obsługuje parametry *typu*, *długości*, *precyzji*, *skali*i *stanu* .|
|[COLUMN_ENTRY_LENGTH](#column_entry_length)|Reprezentuje powiązanie z określoną kolumną w bazie danych. Obsługuje zmienną *długości* .|
|[COLUMN_ENTRY_LENGTH_STATUS](#column_entry_length_status)|Reprezentuje powiązanie z określoną kolumną w bazie danych. Obsługuje parametry *stanu* i *długości* .|
|[COLUMN_ENTRY_PS](#column_entry_ps)|Reprezentuje powiązanie z określoną kolumną w bazie danych. Obsługuje parametry *precyzji* i *skalowania* .|
|[COLUMN_ENTRY_PS_LENGTH](#column_entry_ps_length)|Reprezentuje powiązanie z określoną kolumną w bazie danych. Obsługuje zmienną *długości* , *precyzję* i parametry *skali* .|
|[COLUMN_ENTRY_PS_LENGTH_STATUS](#column_entry_ps_length_status)|Reprezentuje powiązanie z określoną kolumną w bazie danych. Obsługuje zmienne *stanu* i *długości* , *precyzję* i parametry *skali* .|
|[COLUMN_ENTRY_PS_STATUS](#column_entry_ps_status)|Reprezentuje powiązanie z określoną kolumną w bazie danych. Obsługuje zmienną *stanu* , *precyzję* i parametry *skali* .|
|[COLUMN_ENTRY_STATUS](#column_entry_status)|Reprezentuje powiązanie z określoną kolumną w bazie danych. Obsługuje zmienną *stanu* .|
|[COLUMN_ENTRY_TYPE](#column_entry_type)|Reprezentuje powiązanie z określoną kolumną w bazie danych. Obsługuje parametr *typu* .|
|[COLUMN_ENTRY_TYPE_SIZE](#column_entry_type_size)|Reprezentuje powiązanie z określoną kolumną w bazie danych. Obsługuje parametry *typu* i *rozmiaru* .|
|[COLUMN_NAME](#column_name)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy.|
|[COLUMN_NAME_EX](#column_name_ex)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację typu danych, rozmiaru, dokładności, skali, długości kolumny i stanu kolumny.|
|[COLUMN_NAME_LENGTH](#column_name_length)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację długości kolumny.|
|[COLUMN_NAME_LENGTH_STATUS](#column_name_length_status)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację długości kolumny i jej stanu.|
|[COLUMN_NAME_PS](#column_name_ps)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację dokładności i skali.|
|[COLUMN_NAME_PS_LENGTH](#column_name_ps_length)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację dokładności, skali i długości kolumn.|
|[COLUMN_NAME_PS_LENGTH_STATUS](#column_name_ps_length_status)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację dokładności, skalę, długość kolumny i stan kolumny.|
|[COLUMN_NAME_PS_STATUS](#column_name_ps_status)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację stanu precyzji, skali i kolumny.|
|[COLUMN_NAME_STATUS](#column_name_status)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację stanu kolumny.|
|[COLUMN_NAME_TYPE](#column_name_type)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację typu danych.|
|[COLUMN_NAME_TYPE_PS](#column_name_type_ps)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację typu danych, dokładności i skali.|
|[COLUMN_NAME_TYPE_SIZE](#column_name_type_size)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację typu i rozmiaru danych.|
|[COLUMN_NAME_TYPE_STATUS](#column_name_type_status)|Reprezentuje powiązanie z określoną kolumną w bazie danych według nazwy. Obsługuje specyfikację typu danych i stanu kolumny.|
|[END_COLUMN_MAP](#end_column_map)|Oznacza koniec wpisów mapy kolumn.|

## <a name="command-macros"></a>Makra poleceń

|||
|-|-|
|[DEFINE_COMMAND](#define_command)|Określa polecenie, które zostanie użyte do utworzenia zestawu wierszy przy użyciu klasy [CCommand](../../data/oledb/ccommand-class.md) . Akceptuje tylko typy ciągów zgodne z określonym typem aplikacji (ANSI lub Unicode). Zaleca się używanie [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) zamiast DEFINE_COMMAND.|
|[DEFINE_COMMAND_EX](#define_command_ex)|Określa polecenie, które zostanie użyte do utworzenia zestawu wierszy przy użyciu klasy [CCommand](../../data/oledb/ccommand-class.md) . Obsługuje aplikacje ANSI i Unicode.|

## <a name="parameter-map-macros"></a>Makra mapy parametrów

|||
|-|-|
|[BEGIN_PARAM_MAP](#begin_param_map)|Oznacza początek wpisów mapowania parametrów w klasie rekordów użytkownika.|
|[END_PARAM_MAP](#end_param_map)|Oznacza koniec wpisów mapowania parametrów.|
|[SET_PARAM_TYPE](#set_param_type)|Określa COLUMN_ENTRY makra, które obserwują SET_PARAM_TYPE makro jako dane wejściowe, wyjściowe lub wejścia/wyjścia.|

### <a name="atltraceerrorrecords"></a><a name="atltraceerrorrecords"></a>AtlTraceErrorRecords

Zrzuca OLE DB informacje o rekordzie błędu do urządzenia zrzutu w przypadku zwrócenia błędu.

#### <a name="syntax"></a>Składnia

```cpp
inline void AtlTraceErrorRecords(HRESULT hrErr = S_OK);
```

#### <a name="parameters"></a>Parametry

*hErr*<br/>
podczas WYNIK HRESULT zwrócony przez OLE DB funkcję członkowską szablonu klienta.

#### <a name="remarks"></a>Uwagi

Jeśli *Herr* nie jest S_OK, `AtlTraceErrorRecords` zrzuty OLE DB informacji rekordu błędu do urządzenia zrzutu (karta **debugowanie** w oknie danych wyjściowych lub pliku). Informacje o rekordzie błędu uzyskane od dostawcy, w tym numer wiersza, źródło, opis, plik pomocy, kontekst i identyfikator GUID dla każdego wpisu rekordu błędu. `AtlTraceErrorRecords`Zrzuca te informacje tylko w kompilacjach debugowania. W kompilacjach wydania jest to pusta procedura pośrednicząca, która została zoptymalizowana. Aby uzyskać więcej informacji, zobacz [Klasa CDBErrorInfo](../../data/oledb/cdberrorinfo-class.md).

### <a name="begin_accessor"></a><a name="begin_accessor"></a>BEGIN_ACCESSOR

Oznacza początek wpisu metody dostępu.

#### <a name="syntax"></a>Składnia

```cpp
BEGIN_ACCESSOR(num, bAuto)
```

#### <a name="parameters"></a>Parametry

*num*<br/>
podczas Numer przesunięcia zerowego dla metody dostępu w tej mapie metody dostępu.

*bAuto*<br/>
podczas Określa, czy ta metoda dostępu jest autodostępna, czy ręczna metoda dostępu. Jeśli **`true`** , metoda dostępu jest taka sama **`false`** . Jeśli, metoda dostępu jest ręczna. Funkcja autouzupełniania oznacza, że dane są pobierane dla operacji przenoszenia.

#### <a name="remarks"></a>Uwagi

W przypadku wielu metod dostępu w zestawie wierszy należy określić BEGIN_ACCESSOR_MAP i użyć makra BEGIN_ACCESSOR dla poszczególnych metod dostępu. Makro BEGIN_ACCESSOR zostało wykonane z makrem END_ACCESSOR. Makro BEGIN_ACCESSOR_MAP zostało wykonane z makrem END_ACCESSOR_MAP.

#### <a name="example"></a>Przykład

Zobacz [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="begin_accessor_map"></a><a name="begin_accessor_map"></a>BEGIN_ACCESSOR_MAP

Oznacza początek wpisów mapowania metody dostępu.

#### <a name="syntax"></a>Składnia

```cpp
BEGIN_ACCESSOR_MAP(x, num)
```

#### <a name="parameters"></a>Parametry

*x*<br/>
podczas Nazwa klasy rekordu użytkownika.

*num*<br/>
podczas Liczba metod dostępu w tej mapie metody dostępu.

#### <a name="remarks"></a>Uwagi

W przypadku wielu metod dostępu w zestawie wierszy należy określić BEGIN_ACCESSOR_MAP na początku i użyć makra BEGIN_ACCESSOR dla każdego indywidualnego metody dostępu. Makro BEGIN_ACCESSOR zostało wykonane z makrem END_ACCESSOR. Mapa akcesora została zakończona przy użyciu makra END_ACCESSOR_MAP.

Jeśli w rekordzie użytkownika istnieje tylko jedna metoda dostępu, użyj makra [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md).

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

Oznacza koniec wpisu metody dostępu.

#### <a name="syntax"></a>Składnia

```cpp
END_ACCESSOR()
```

#### <a name="remarks"></a>Uwagi

Dla wielu metod dostępu w zestawie wierszy należy określić BEGIN_ACCESSOR_MAP i użyć makra BEGIN_ACCESSOR dla poszczególnych metod dostępu. Makro BEGIN_ACCESSOR zostało wykonane z makrem END_ACCESSOR. Makro BEGIN_ACCESSOR_MAP zostało wykonane z makrem END_ACCESSOR_MAP.

#### <a name="example"></a>Przykład

Zobacz [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="end_accessor_map"></a><a name="end_accessor_map"></a>END_ACCESSOR_MAP

Oznacza koniec wpisów mapowania metody dostępu.

#### <a name="syntax"></a>Składnia

```cpp
END_ACCESSOR_MAP()
```

#### <a name="remarks"></a>Uwagi

Dla wielu metod dostępu w zestawie wierszy należy określić BEGIN_ACCESSOR_MAP i użyć makra BEGIN_ACCESSOR dla poszczególnych metod dostępu. Makro BEGIN_ACCESSOR zostało wykonane z makrem END_ACCESSOR. Makro BEGIN_ACCESSOR_MAP zostało wykonane z makrem END_ACCESSOR_MAP.

#### <a name="example"></a>Przykład

Zobacz [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="begin_column_map"></a><a name="begin_column_map"></a>BEGIN_COLUMN_MAP

Oznacza początek wpisu mapy kolumn.

#### <a name="syntax"></a>Składnia

```cpp
BEGIN_COLUMN_MAP(x)
```

#### <a name="parameters"></a>Parametry

*x*<br/>
podczas Nazwa klasy rekordu użytkownika, która pochodzi od `CAccessor` .

#### <a name="remarks"></a>Uwagi

To makro jest używane w przypadku pojedynczej metody dostępu dla zestawu wierszy. Jeśli masz wiele metod dostępu w zestawie wierszy, użyj [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

Makro BEGIN_COLUMN_MAP zostało wykonane z makrem END_COLUMN_MAP. To makro jest używane, gdy w rekordzie użytkownika jest wymagana tylko jedna metoda dostępu.

Kolumny odpowiadają polom w zestawie wierszy, który ma zostać powiązany.

#### <a name="example"></a>Przykład

Oto przykładowa kolumna i mapa parametrów:

<!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->

### <a name="blob_entry"></a><a name="blob_entry"></a>BLOB_ENTRY

Używane z BEGIN_COLUMN_MAP i END_COLUMN_MAP do powiązania dużego obiektu binarnego ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))).

#### <a name="syntax"></a>Składnia

```cpp
BLOB_ENTRY(nOrdinal, IID, flags, data)
```

#### <a name="parameters"></a>Parametry

*nOrdinal*<br/>
podczas Numer kolumny.

*IID*<br/>
podczas Identyfikator GUID interfejsu, taki jak `IDD_ISequentialStream` , używany do pobierania obiektu BLOB.

*flagi*<br/>
podczas Flagi trybu magazynu zdefiniowane przez model magazynu strukturalnego OLE (na przykład `STGM_READ` ).

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

#### <a name="example"></a>Przykład

Zobacz [Jak mogę pobrać obiekt BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_length"></a><a name="blob_entry_length"></a>BLOB_ENTRY_LENGTH

Używane z BEGIN_COLUMN_MAP i END_COLUMN_MAP do powiązania dużego obiektu binarnego ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobnie jak [BLOB_ENTRY](../../data/oledb/blob-entry.md), z tą różnicą, że to makro pobiera również długość w bajtach kolumny obiektu BLOB.

#### <a name="syntax"></a>Składnia

```cpp
BLOB_ENTRY_LENGTH(nOrdinal, IID, flags, data, length)
```

#### <a name="parameters"></a>Parametry

*nOrdinal*<br/>
podczas Numer kolumny.

*IID*<br/>
podczas Identyfikator GUID interfejsu, taki jak `IDD_ISequentialStream` , używany do pobierania obiektu BLOB.

*flagi*<br/>
podczas Flagi trybu magazynu zdefiniowane przez model magazynu strukturalnego OLE (na przykład `STGM_READ` ).

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
określoną Długość (rzeczywista) w bajtach kolumny obiektu BLOB.

#### <a name="example"></a>Przykład

Zobacz [Jak mogę pobrać obiekt BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_length_status"></a><a name="blob_entry_length_status"></a>BLOB_ENTRY_LENGTH_STATUS

Używane z BEGIN_COLUMN_MAP i END_COLUMN_MAP do powiązania dużego obiektu binarnego ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobnie jak [BLOB_ENTRY](../../data/oledb/blob-entry.md), z tą różnicą, że to makro pobiera również długość i stan kolumny obiektu BLOB.

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

*nOrdinal*<br/>
podczas Numer kolumny.

*IID*<br/>
podczas Identyfikator GUID interfejsu, taki jak `IDD_ISequentialStream` , używany do pobierania obiektu BLOB.

*flagi*<br/>
podczas Flagi trybu magazynu zdefiniowane przez model magazynu strukturalnego OLE (na przykład `STGM_READ` ).

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
określoną Długość (rzeczywista) w bajtach kolumny obiektu BLOB.

*Stany*<br/>
określoną Stan kolumny danych obiektu BLOB.

#### <a name="example"></a>Przykład

Zobacz [Jak mogę pobrać obiekt BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_status"></a><a name="blob_entry_status"></a>BLOB_ENTRY_STATUS

Używane z BEGIN_COLUMN_MAP lub BEGIN_ACCESSOR_MAP do powiązania dużego obiektu binarnego ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobnie jak [BLOB_ENTRY](../../data/oledb/blob-entry.md), z tą różnicą, że to makro pobiera również stan kolumny obiektu BLOB.

#### <a name="syntax"></a>Składnia

```cpp
BLOB_ENTRY_STATUS(nOrdinal, IID, flags, data, status)
```

#### <a name="parameters"></a>Parametry

*nOrdinal*<br/>
podczas Numer kolumny.

*IID*<br/>
podczas Identyfikator GUID interfejsu, taki jak `IDD_ISequentialStream` , używany do pobierania obiektu BLOB.

*flagi*<br/>
podczas Flagi trybu magazynu zdefiniowane przez model magazynu strukturalnego OLE (na przykład `STGM_READ` ).

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

*Stany*<br/>
określoną Stan pola obiektu BLOB.

#### <a name="example"></a>Przykład

Zobacz [Jak mogę pobrać obiekt BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_name"></a><a name="blob_name"></a>BLOB_NAME

Używane z BEGIN_COLUMN_MAP i END_COLUMN_MAP do powiązania dużego obiektu binarnego ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobnie jak [BLOB_ENTRY](../../data/oledb/blob-entry.md), z tą różnicą, że to makro Pobiera nazwę kolumny zamiast numeru kolumny.

#### <a name="syntax"></a>Składnia

```cpp
BLOB_NAME(pszName, IID, flags, data )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
podczas Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć przez umieszczenie znaku "L" przed nazwą, na przykład: `L"MyColumn"` .

*IID*<br/>
podczas Identyfikator GUID interfejsu, taki jak `IDD_ISequentialStream` , używany do pobierania obiektu BLOB.

*flagi*<br/>
podczas Flagi trybu magazynu zdefiniowane przez model magazynu strukturalnego OLE (na przykład `STGM_READ` ).

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

#### <a name="example"></a>Przykład

Zobacz [Jak mogę pobrać obiekt BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_name_length"></a><a name="blob_name_length"></a>BLOB_NAME_LENGTH

Używane z BEGIN_COLUMN_MAP i END_COLUMN_MAP do powiązania dużego obiektu binarnego ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobnie jak [BLOB_NAME](../../data/oledb/blob-name.md), z tą różnicą, że to makro pobiera również długość w bajtach kolumny danych obiektu BLOB.

#### <a name="syntax"></a>Składnia

```cpp
BLOB_NAME_LENGTH(pszName, IID, flags, data, length )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
podczas Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć przez umieszczenie znaku "L" przed nazwą, na przykład: `L"MyColumn"` .

*IID*<br/>
podczas Identyfikator GUID interfejsu, taki jak `IDD_ISequentialStream` , używany do pobierania obiektu BLOB.

*flagi*<br/>
podczas Flagi trybu magazynu zdefiniowane przez model magazynu strukturalnego OLE (na przykład `STGM_READ` ).

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
określoną Długość (rzeczywista) w bajtach kolumny obiektu BLOB.

### <a name="blob_name_length_status"></a><a name="blob_name_length_status"></a>BLOB_NAME_LENGTH_STATUS

Używane z BEGIN_COLUMN_MAP i END_COLUMN_MAP do powiązania dużego obiektu binarnego ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobnie jak [BLOB_NAME](../../data/oledb/blob-name.md), z tą różnicą, że to makro pobiera również długość i stan kolumny dane obiektu BLOB.

#### <a name="syntax"></a>Składnia

```cpp
BLOB_NAME_LENGTH_STATUS(pszName, IID, flags, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
podczas Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć przez umieszczenie znaku "L" przed nazwą, na przykład: `L"MyColumn"` .

*IID*<br/>
podczas Identyfikator GUID interfejsu, taki jak `IDD_ISequentialStream` , używany do pobierania obiektu BLOB.

*flagi*<br/>
podczas Flagi trybu magazynu zdefiniowane przez model magazynu strukturalnego OLE (na przykład `STGM_READ` ).

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
określoną Długość (rzeczywista) w bajtach kolumny obiektu BLOB.

*Stany*<br/>
określoną Stan pola obiektu BLOB.

### <a name="blob_name_status"></a><a name="blob_name_status"></a>BLOB_NAME_STATUS

Używane z BEGIN_COLUMN_MAP i END_COLUMN_MAP do powiązania dużego obiektu binarnego ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobnie jak [BLOB_NAME](../../data/oledb/blob-name.md), z tą różnicą, że to makro pobiera również stan kolumny dane obiektu BLOB.

#### <a name="syntax"></a>Składnia

```cpp
BLOB_NAME_STATUS(pszName, IID, flags, data, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
podczas Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć przez umieszczenie znaku "L" przed nazwą, na przykład: `L"MyColumn"` .

*IID*<br/>
podczas Identyfikator GUID interfejsu, taki jak `IDD_ISequentialStream` , używany do pobierania obiektu BLOB.

*flagi*<br/>
podczas Flagi trybu magazynu zdefiniowane przez model magazynu strukturalnego OLE (na przykład `STGM_READ` ).

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

*Stany*<br/>
określoną Stan pola obiektu BLOB.

### <a name="bookmark_entry"></a><a name="bookmark_entry"></a>BOOKMARK_ENTRY

Tworzy powiązanie z kolumną zakładki.

#### <a name="syntax"></a>Składnia

```cpp
BOOKMARK_ENTRY(variable)
```

#### <a name="parameters"></a>Parametry

*zmiennej*<br/>
podczas Zmienna, która ma zostać powiązana z kolumną zakładki.

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

Aby uzyskać więcej informacji, zobacz [Używanie zakładek](using-bookmarks.md) i [klasy CBookmark](../../data/oledb/cbookmark-class.md).

### <a name="column_entry"></a><a name="column_entry"></a>COLUMN_ENTRY

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY(nOrdinal, data)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *dokumentacji programisty OLE DB*.

*nOrdinal*<br/>
podczas Numer kolumny.

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

Makro COLUMN_ENTRY jest używane w następujących miejscach:

- Między makrami [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP](../../data/oledb/end-column-map.md) .

- Między makrami [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) .

- Między makrami [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP](../../data/oledb/end-param-map.md) .

#### <a name="example"></a>Przykład

Zobacz przykłady w tematach makr, [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="column_entry_ex"></a><a name="column_entry_ex"></a>COLUMN_ENTRY_EX

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w bazie danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_EX(nOrdinal, wType, nLength, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *dokumentacji programisty OLE DB*.

*nOrdinal*<br/>
podczas Numer kolumny.

*wType*<br/>
podczas Typ danych.

*nLength*<br/>
podczas Rozmiar danych w bajtach.

*nPrecision*<br/>
podczas Maksymalna precyzja, która ma być używana podczas pobierania danych i *wType* `DBTYPE_NUMERIC` . W przeciwnym razie ten parametr jest ignorowany.

*nScale*<br/>
podczas Skala do użycia podczas pobierania danych i *wType* jest `DBTYPE_NUMERIC` lub `DBTYPE_DECIMAL` .

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
podczas Zmienna, która ma zostać powiązana z długością kolumny.

*Stany*<br/>
podczas Zmienna, która ma zostać powiązana ze stanem kolumny.

#### <a name="remarks"></a>Uwagi

Makro COLUMN_ENTRY_EX jest używane w następujących miejscach:

- Między makrami [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP](../../data/oledb/end-column-map.md) .

- Między makrami [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) .

- Między makrami [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP](../../data/oledb/end-param-map.md) .

#### <a name="example"></a>Przykład

Zobacz [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="column_entry_length"></a><a name="column_entry_length"></a>COLUMN_ENTRY_LENGTH

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w bazie danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_LENGTH(nOrdinal, data, length)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *dokumentacji programisty OLE DB*.

*nOrdinal*<br/>
podczas Numer kolumny, zaczynając od 1. Zakładka odpowiada zerowej kolumnie.

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
podczas Zmienna, która ma zostać powiązana z długością kolumny.

#### <a name="remarks"></a>Uwagi

To makro obsługuje zmienną *długości* . Jest on używany w następujących miejscach:

- Między makrami [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP](../../data/oledb/end-column-map.md) .

- Między makrami [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) .

- Między makrami [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP](../../data/oledb/end-param-map.md) .

### <a name="column_entry_length_status"></a><a name="column_entry_length_status"></a>COLUMN_ENTRY_LENGTH_STATUS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w bazie danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_LENGTH_STATUS(nOrdinal, data, length, status)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *dokumentacji programisty OLE DB*.

*nOrdinal*<br/>
podczas Numer kolumny.

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
podczas Zmienna, która ma zostać powiązana z długością kolumny.

*Stany*<br/>
podczas Zmienna, która ma zostać powiązana ze stanem kolumny.

#### <a name="remarks"></a>Uwagi

Użyj tego makra, gdy chcesz obsługiwać zmienne długości i stanu. Jest on używany w następujących miejscach:

- Między makrami [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP](../../data/oledb/end-column-map.md) .

- Między makrami [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) .

- Między makrami [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP](../../data/oledb/end-param-map.md) .

### <a name="column_entry_ps"></a><a name="column_entry_ps"></a>COLUMN_ENTRY_PS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_PS(nOrdinal, nPrecision, nScale, data)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *dokumentacji programisty OLE DB*.

*nOrdinal*<br/>
podczas Numer kolumny.

*nPrecision*<br/>
podczas Maksymalna precyzja kolumny, która ma zostać powiązana.

*nScale*<br/>
podczas Skala kolumny, która ma zostać powiązana.

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

Pozwala określić precyzję i skalę kolumny, która ma zostać powiązana. Jest on używany w następujących miejscach:

- Między makrami [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP](../../data/oledb/end-column-map.md) .

- Między makrami [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) .

- Między makrami [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP](../../data/oledb/end-param-map.md) .

### <a name="column_entry_ps_length"></a><a name="column_entry_ps_length"></a>COLUMN_ENTRY_PS_LENGTH

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w bazie danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_PS_LENGTH(nOrdinal, nPrecision, nScale, data, length)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *dokumentacji programisty OLE DB*.

*nOrdinal*<br/>
podczas Numer kolumny, zaczynając od 1. Zakładka odpowiada zerowej kolumnie.

*nPrecision*<br/>
podczas Maksymalna precyzja kolumny, która ma zostać powiązana.

*nScale*<br/>
podczas Skala kolumny, która ma zostać powiązana.

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
podczas Zmienna, która ma zostać powiązana z długością kolumny.

#### <a name="remarks"></a>Uwagi

Pozwala określić precyzję i skalę kolumny, która ma zostać powiązana. To makro obsługuje zmienną *długości* . Jest on używany w następujących miejscach:

- Między makrami [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP](../../data/oledb/end-column-map.md) .

- Między makrami [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) .

- Między makrami [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP](../../data/oledb/end-param-map.md) .

### <a name="column_entry_ps_length_status"></a><a name="column_entry_ps_length_status"></a>COLUMN_ENTRY_PS_LENGTH_STATUS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w bazie danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_PS_LENGTH_STATUS(nOrdinal, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *dokumentacji programisty OLE DB*.

*nOrdinal*<br/>
podczas Numer kolumny.

*nPrecision*<br/>
podczas Maksymalna precyzja kolumny, która ma zostać powiązana.

*nScale*<br/>
podczas Skala kolumny, która ma zostać powiązana.

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
podczas Zmienna, która ma zostać powiązana z długością kolumny.

*Stany*<br/>
podczas Zmienna, która ma zostać powiązana ze stanem kolumny.

#### <a name="remarks"></a>Uwagi

Pozwala określić precyzję i skalę kolumny, która ma zostać powiązana. Użyj tego makra, gdy chcesz obsługiwać zmienne długości i stanu. Jest on używany w następujących miejscach:

- Między makrami [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP](../../data/oledb/end-column-map.md) .

- Między makrami [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) .

- Między makrami [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP](../../data/oledb/end-param-map.md) .

### <a name="column_entry_ps_status"></a><a name="column_entry_ps_status"></a>COLUMN_ENTRY_PS_STATUS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w bazie danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_PS_STATUS(nOrdinal, nPrecision, nScale, data, status)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *dokumentacji programisty OLE DB*.

*nOrdinal*<br/>
podczas Numer kolumny.

*nPrecision*<br/>
podczas Maksymalna precyzja kolumny, która ma zostać powiązana.

*nScale*<br/>
podczas Skala kolumny, która ma zostać powiązana.

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

*Stany*<br/>
podczas Zmienna, która ma zostać powiązana ze stanem kolumny.

#### <a name="remarks"></a>Uwagi

Pozwala określić precyzję i skalę kolumny, która ma zostać powiązana. To makro obsługuje zmienną *stanu* . Jest on używany w następujących miejscach:

- Między makrami [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP](../../data/oledb/end-column-map.md) .

- Między makrami [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) .

- Między makrami [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP](../../data/oledb/end-param-map.md) .

### <a name="column_entry_status"></a><a name="column_entry_status"></a>COLUMN_ENTRY_STATUS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w bazie danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_STATUS(nOrdinal, data, status)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *dokumentacji programisty OLE DB*.

*nOrdinal*<br/>
podczas Numer kolumny.

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

*Stany*<br/>
podczas Zmienna, która ma zostać powiązana ze stanem kolumny.

#### <a name="remarks"></a>Uwagi

To makro obsługuje zmienną *stanu* . Jest on używany w następujących miejscach:

- Między makrami [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP](../../data/oledb/end-column-map.md) .

- Między makrami [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) .

- Między makrami [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP](../../data/oledb/end-param-map.md) .

### <a name="column_entry_type"></a><a name="column_entry_type"></a>COLUMN_ENTRY_TYPE

Reprezentuje powiązanie z określoną kolumną w bazie danych. Obsługuje parametr *typu* .

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_TYPE (nOrdinal, wType, data)
```

#### <a name="parameters"></a>Parametry

*nOrdinal*<br/>
podczas Numer kolumny.

*wType*<br/>
podczas Typ danych wpisu kolumny.

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

To makro jest wyspecjalizowaną odmianą [COLUMN_ENTRY](../../data/oledb/column-entry.md) makro, które zapewnia metodę określania typu danych.

### <a name="column_entry_type_size"></a><a name="column_entry_type_size"></a>COLUMN_ENTRY_TYPE_SIZE

Reprezentuje powiązanie z określoną kolumną w bazie danych. Obsługuje parametry *typu* i *rozmiaru* .

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)
```

#### <a name="parameters"></a>Parametry

*nOrdinal*<br/>
podczas Numer kolumny.

*wType*<br/>
podczas Typ danych wpisu kolumny.

*nLength*<br/>
podczas Rozmiar wpisu kolumny w bajtach.

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

To makro jest wyspecjalizowaną odmianą [COLUMN_ENTRY](../../data/oledb/column-entry.md) makro, które zapewnia metodę określania rozmiaru i typu danych.

### <a name="column_name"></a><a name="column_name"></a>COLUMN_NAME

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie jak [COLUMN_ENTRY](../../data/oledb/column-entry.md), z tą różnicą, że to makro przyjmuje nazwę kolumny zamiast numeru kolumny.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME(pszName, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
podczas Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć przez umieszczenie znaku "L" przed nazwą, na przykład: `L"MyColumn"` .

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

Makra COLUMN_NAME_ * są używane w tych samych miejscach co [COLUMN_ENTRY](../../data/oledb/column-entry.md):

- Między makrami [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP](../../data/oledb/end-column-map.md) .

- Między makrami [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) .

- Między makrami [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP](../../data/oledb/end-param-map.md) .

### <a name="column_name_ex"></a><a name="column_name_ex"></a>COLUMN_NAME_EX

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie jak [column_name](../../data/oledb/column-name.md), z tą różnicą, że to makro pobiera również typ danych, rozmiar, dokładność, skalę, długość kolumny i stan kolumny.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_EX(pszName, wType, nLength, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
podczas Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć przez umieszczenie znaku "L" przed nazwą, na przykład: `L"MyColumn"` .

*wType*<br/>
podczas Typ danych.

*nLength*<br/>
podczas Rozmiar danych w bajtach.

*nPrecision*<br/>
podczas Maksymalna precyzja, która ma być używana podczas pobierania danych i *wType* `DBTYPE_NUMERIC` . W przeciwnym razie ten parametr jest ignorowany.

*nScale*<br/>
podczas Skala do użycia podczas pobierania danych i *wType* jest `DBTYPE_NUMERIC` lub `DBTYPE_DECIMAL` .

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
podczas Zmienna, która ma zostać powiązana z długością kolumny.

*Stany*<br/>
podczas Zmienna, która ma zostać powiązana ze stanem kolumny.

#### <a name="remarks"></a>Uwagi

Aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_ *, zobacz [column_name](../../data/oledb/column-name.md) .

### <a name="column_name_length"></a><a name="column_name_length"></a>COLUMN_NAME_LENGTH

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie jak [column_name](../../data/oledb/column-name.md), z tą różnicą, że to makro również przyjmuje długość kolumny.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_LENGTH(pszName, data, length)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
podczas Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć przez umieszczenie znaku "L" przed nazwą, na przykład: `L"MyColumn"` .

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
podczas Zmienna, która ma zostać powiązana z długością kolumny.

#### <a name="remarks"></a>Uwagi

Aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_ *, zobacz [column_name](../../data/oledb/column-name.md) .

### <a name="column_name_length_status"></a><a name="column_name_length_status"></a>COLUMN_NAME_LENGTH_STATUS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie jak [column_name](../../data/oledb/column-name.md), z tą różnicą, że to makro pobiera również długość kolumny i stan kolumny.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_LENGTH_STATUS(pszName, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
podczas Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć przez umieszczenie znaku "L" przed nazwą, na przykład: `L"MyColumn"` .

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
podczas Zmienna, która ma zostać powiązana z długością kolumny.

*Stany*<br/>
podczas Zmienna, która ma zostać powiązana ze stanem kolumny.

#### <a name="remarks"></a>Uwagi

Aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_ *, zobacz [column_name](../../data/oledb/column-name.md) .

### <a name="column_name_ps"></a><a name="column_name_ps"></a>COLUMN_NAME_PS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie jak [column_name](../../data/oledb/column-name.md), z tą różnicą, że to makro również pobiera precyzję i skalowalność.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_PS(pszName, nPrecision, nScale, data )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
podczas Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć przez umieszczenie znaku "L" przed nazwą, na przykład: `L"MyColumn"` .

*nPrecision*<br/>
podczas Maksymalna precyzja kolumny, która ma zostać powiązana.

*nScale*<br/>
podczas Skala kolumny, która ma zostać powiązana.

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

Aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_ *, zobacz [column_name](../../data/oledb/column-name.md) .

### <a name="column_name_ps_length"></a><a name="column_name_ps_length"></a>COLUMN_NAME_PS_LENGTH

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie jak [column_name](../../data/oledb/column-name.md), z tą różnicą, że to makro również pobiera precyzję, skalę i długość kolumny.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_PS_LENGTH(pszName, nPrecision, nScale, data, length )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
podczas Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć przez umieszczenie znaku "L" przed nazwą, na przykład: `L"MyColumn"` .

*nPrecision*<br/>
podczas Maksymalna precyzja kolumny, która ma zostać powiązana.

*nScale*<br/>
podczas Skala kolumny, która ma zostać powiązana.

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
podczas Zmienna, która ma zostać powiązana z długością kolumny.

#### <a name="remarks"></a>Uwagi

Aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_ *, zobacz [column_name](../../data/oledb/column-name.md) .

### <a name="column_name_ps_length_status"></a><a name="column_name_ps_length_status"></a>COLUMN_NAME_PS_LENGTH_STATUS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie jak [column_name](../../data/oledb/column-name.md), z tą różnicą, że to makro również pobiera precyzję, skalę, długość kolumny i stan kolumny.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_PS_LENGTH_STATUS(pszName, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
podczas Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć przez umieszczenie znaku "L" przed nazwą, na przykład: `L"MyColumn"` .

*nPrecision*<br/>
podczas Maksymalna precyzja kolumny, która ma zostać powiązana.

*nScale*<br/>
podczas Skala kolumny, która ma zostać powiązana.

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
podczas Zmienna, która ma zostać powiązana z długością kolumny.

*Stany*<br/>
podczas Zmienna, która ma zostać powiązana ze stanem kolumny.

#### <a name="remarks"></a>Uwagi

Aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_ *, zobacz [column_name](../../data/oledb/column-name.md) .

### <a name="column_name_ps_status"></a><a name="column_name_ps_status"></a>COLUMN_NAME_PS_STATUS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie jak [column_name](../../data/oledb/column-name.md), z tą różnicą, że to makro również Pobiera stan dokładności, skali i kolumny.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_PS_STATUS(pszName, nPrecision, nScale, data, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
podczas Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć przez umieszczenie znaku "L" przed nazwą, na przykład: `L"MyColumn"` .

*nPrecision*<br/>
podczas Maksymalna precyzja kolumny, która ma zostać powiązana.

*nScale*<br/>
podczas Skala kolumny, która ma zostać powiązana.

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

*Stany*<br/>
podczas Zmienna, która ma zostać powiązana ze stanem kolumny.

#### <a name="remarks"></a>Uwagi

Aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_ *, zobacz [column_name](../../data/oledb/column-name.md) .

### <a name="column_name_status"></a><a name="column_name_status"></a>COLUMN_NAME_STATUS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie jak [column_name](../../data/oledb/column-name.md), z tą różnicą, że to makro również przyjmuje stan kolumny.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_STATUS(pszName, data, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
podczas Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć przez umieszczenie znaku "L" przed nazwą, na przykład: `L"MyColumn"` .

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

*Stany*<br/>
podczas Zmienna, która ma zostać powiązana ze stanem kolumny.

#### <a name="remarks"></a>Uwagi

Aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_ *, zobacz [column_name](../../data/oledb/column-name.md) .

### <a name="column_name_type"></a><a name="column_name_type"></a>COLUMN_NAME_TYPE

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie jak [column_name](../../data/oledb/column-name.md), z tą różnicą, że to makro pobiera również typ danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_TYPE(pszName, wType, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
podczas Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć przez umieszczenie znaku "L" przed nazwą, na przykład: `L"MyColumn"` .

*wType*<br/>
podczas Typ danych.

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

Aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_ *, zobacz [column_name](../../data/oledb/column-name.md) .

### <a name="column_name_type_ps"></a><a name="column_name_type_ps"></a>COLUMN_NAME_TYPE_PS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie jak [column_name](../../data/oledb/column-name.md), z tą różnicą, że to makro pobiera również typ danych, dokładność i skalowanie.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_TYPE_PS(pszName, wType, nPrecision, nScale, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
podczas Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć przez umieszczenie znaku "L" przed nazwą, na przykład: `L"MyColumn"` .

*wType*<br/>
podczas Typ danych.

*nPrecision*<br/>
podczas Maksymalna precyzja, która ma być używana podczas pobierania danych i *wType* `DBTYPE_NUMERIC` . W przeciwnym razie ten parametr jest ignorowany.

*nScale*<br/>
podczas Skala do użycia podczas pobierania danych i *wType* jest `DBTYPE_NUMERIC` lub `DBTYPE_DECIMAL` .

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

Aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_ *, zobacz [column_name](../../data/oledb/column-name.md) .

### <a name="column_name_type_size"></a><a name="column_name_type_size"></a>COLUMN_NAME_TYPE_SIZE

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie jak [column_name](../../data/oledb/column-name.md), z tą różnicą, że to makro pobiera również typ danych i rozmiar.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_TYPE_SIZE(pszName, wType, nLength, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
podczas Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć przez umieszczenie znaku "L" przed nazwą, na przykład: `L"MyColumn"` .

*wType*<br/>
podczas Typ danych.

*nLength*<br/>
podczas Rozmiar danych w bajtach.

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

Aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_ *, zobacz [column_name](../../data/oledb/column-name.md) .

### <a name="column_name_type_status"></a><a name="column_name_type_status"></a>COLUMN_NAME_TYPE_STATUS

Reprezentuje powiązanie zestawu wierszy z określoną kolumną w zestawie wierszy. Podobnie jak w przypadku [column_name](../../data/oledb/column-name.md), z tą różnicą, że to makro wymaga również typu danych i kolumny.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_TYPE_STATUS(pszName, wType, status, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
podczas Wskaźnik do nazwy kolumny. Nazwa musi być ciągiem Unicode. Można to osiągnąć przez umieszczenie znaku "L" przed nazwą, na przykład: `L"MyColumn"` .

*wType*<br/>
podczas Typ danych.

*Stany*<br/>
podczas Zmienna, która ma zostać powiązana ze stanem kolumny.

*data*<br/>
podczas Odpowiadający element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

Aby uzyskać informacje o tym, gdzie są używane makra COLUMN_NAME_ *, zobacz [column_name](../../data/oledb/column-name.md) .

### <a name="end_column_map"></a><a name="end_column_map"></a>END_COLUMN_MAP

Oznacza koniec wpisów mapy kolumn.

#### <a name="syntax"></a>Składnia

```cpp
END_COLUMN_MAP()
```

#### <a name="remarks"></a>Uwagi

Jest on używany z pojedynczym akcesorem zestawu wierszy. Makro BEGIN_COLUMN_MAP zostało wykonane z makrem END_COLUMN_MAP.

#### <a name="example"></a>Przykład

Zobacz [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md).

### <a name="define_command"></a><a name="define_command"></a>DEFINE_COMMAND

Określa polecenie, które zostanie użyte do utworzenia zestawu wierszy przy użyciu klasy [CCommand](../../data/oledb/ccommand-class.md) . Akceptuje tylko typy ciągów zgodne z określonym typem aplikacji (ANSI lub Unicode).

> [!NOTE]
> Zaleca się używanie [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) zamiast DEFINE_COMMAND.

#### <a name="syntax"></a>Składnia

```cpp
DEFINE_COMMAND(x, szCommand)
```

#### <a name="parameters"></a>Parametry

*x*<br/>
podczas Nazwa klasy rekordu użytkownika (polecenia).

*szCommand*<br/>
podczas Ciąg polecenia, który zostanie użyty do utworzenia zestawu wierszy przy użyciu [CCommand](../../data/oledb/ccommand-class.md).

#### <a name="remarks"></a>Uwagi

Określony ciąg polecenia będzie używany jako domyślny, jeśli nie określisz tekstu polecenia w metodzie [CCommand:: Open](../../data/oledb/ccommand-open.md) .

To makro akceptuje ciągi ANSI w przypadku kompilowania aplikacji jako ANSI lub ciągów Unicode w przypadku kompilowania aplikacji jako Unicode. Zaleca się używanie [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) zamiast DEFINE_COMMAND, ponieważ dawniej akceptuje ciągi Unicode, niezależnie od typu aplikacji ANSI lub Unicode.

#### <a name="example"></a>Przykład

Zobacz [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="define_command_ex"></a><a name="define_command_ex"></a>DEFINE_COMMAND_EX

Określa polecenie, które zostanie użyte do utworzenia zestawu wierszy przy użyciu klasy [CCommand](../../data/oledb/ccommand-class.md) . Obsługuje aplikacje Unicode i ANSI.

#### <a name="syntax"></a>Składnia

```cpp
DEFINE_COMMAND_EX(x, wszCommand)
```

#### <a name="parameters"></a>Parametry

*x*<br/>
podczas Nazwa klasy rekordu użytkownika (polecenia).

*wszCommand*<br/>
podczas Ciąg polecenia, który zostanie użyty do utworzenia zestawu wierszy przy użyciu [CCommand](../../data/oledb/ccommand-class.md).

#### <a name="remarks"></a>Uwagi

Określony ciąg polecenia będzie używany jako domyślny, jeśli nie określisz tekstu polecenia w metodzie [CCommand:: Open](../../data/oledb/ccommand-open.md) .

To makro akceptuje ciągi Unicode, niezależnie od typu aplikacji. To makro jest preferowane względem [DEFINE_COMMAND](../../data/oledb/define-command.md) , ponieważ obsługuje standard Unicode oraz aplikacje ANSI.

#### <a name="example"></a>Przykład

Zobacz [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="begin_param_map"></a><a name="begin_param_map"></a>BEGIN_PARAM_MAP

Oznacza początek wpisów mapowania parametrów.

#### <a name="syntax"></a>Składnia

```cpp
BEGIN_PARAM_MAP(x)
```

#### <a name="parameters"></a>Parametry

*x*<br/>
podczas Nazwa klasy rekordu użytkownika.

#### <a name="remarks"></a>Uwagi

Parametry są używane przez [polecenia](/previous-versions/windows/desktop/ms724608(v=vs.85)).

#### <a name="example"></a>Przykład

Zobacz przykład dla makra [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) .

### <a name="end_param_map"></a><a name="end_param_map"></a>END_PARAM_MAP

Oznacza koniec wpisów mapowania parametrów.

#### <a name="syntax"></a>Składnia

```cpp
END_PARAM_MAP()
```

#### <a name="example"></a>Przykład

Zobacz przykład dla makra [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) .

### <a name="set_param_type"></a><a name="set_param_type"></a>SET_PARAM_TYPE

Określa COLUMN_ENTRY makra, które obserwują SET_PARAM_TYPE danych wejściowych, wyjściowych lub wejściowych lub wyjściowych makra.

#### <a name="syntax"></a>Składnia

```cpp
SET_PARAM_TYPE(type)
```

#### <a name="parameters"></a>Parametry

*Wprowadź*<br/>
podczas Typ do ustawienia dla parametru.

#### <a name="remarks"></a>Uwagi

Dostawcy obsługują tylko typy wejściowe/wyjściowe parametrów, które są obsługiwane przez bazowe źródło danych. Typ jest kombinacją co najmniej jednej `DBPARAMIO` wartości (zobacz [struktury DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *dokumentacji programisty OLE DB*):

- `DBPARAMIO_NOTPARAM`Metoda dostępu nie ma parametrów. Zazwyczaj ustawia `eParamIO` się tę wartość w metodzie dostępu do wierszy, aby przypominać użytkownikowi, że parametry są ignorowane.

- `DBPARAMIO_INPUT`Parametr wejściowy.

- `DBPARAMIO_OUTPUT`Parametr wyjściowy.

- `DBPARAMIO_INPUT | DBPARAMIO_OUTPUT`Parametr jest parametrem wejściowym i wyjściowym.

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

**Nagłówek:** atldbcli. h

## <a name="see-also"></a>Zobacz także

[Makra i funkcje globalne dla OLE DB szablonów konsumentów](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Dokumentacja szablonów klientów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
