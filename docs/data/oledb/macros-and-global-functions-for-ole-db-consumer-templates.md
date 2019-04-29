---
title: Makra i funkcje globalne dla szablonów konsumentów OLE DB
ms.date: 02/11/2019
f1_keywords:
- vc.templates.ole
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
ms.openlocfilehash: d4ed6b86d99cdfc272b5df10ede6af6bd05ed366
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361350"
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>Makra i funkcje globalne dla szablonów konsumentów OLE DB

Szablony OLE DB konsumenta obejmują następujące makra i funkcje globalne:

## <a name="global-functions"></a>Funkcje globalne

|||
|-|-|
|[AtlTraceErrorRecords](#atltraceerrorrecords)|Zrzuca informacje o OLE DB rekordu błędu na urządzeniu zrzutu, jeśli zostanie zwrócony błąd.|

## <a name="accessor-map-macros"></a>Makra mapy metody dostępu

|||
|-|-|
|[BEGIN_ACCESSOR](#begin_accessor)|Oznacza początek wpisu dostępu.|
|[BEGIN_ACCESSOR_MAP](#begin_accessor_map)|Oznacza początek wpisy mapy dostępu.|
|[END_ACCESSOR](#end_accessor)|Oznacza koniec wpisu dostępu.|
|[END_ACCESSOR_MAP](#end_accessor_map)|Oznacza koniec wpisy mapy dostępu.|

## <a name="column-map-macros"></a>Makra mapy kolumny

|||
|-|-|
|[BEGIN_COLUMN_MAP](#begin_column_map)|Oznacza początek wpisy mapy kolumny w klasie rekordu użytkownika.|
|[BLOB_ENTRY](#blob_entry)|Używane do powiązania duży obiekt binarny (BLOB).|
|[BLOB_ENTRY_LENGTH](#blob_entry_length)|Raporty długość kolumny danych obiektów BLOB.|
|[BLOB_ENTRY_LENGTH_STATUS](#blob_entry_length_status)|Raporty długość i stan kolumny danych obiektów BLOB.|
|[BLOB_ENTRY_STATUS](#blob_entry_status)|Informuje o stanie kolumnę danych obiektów BLOB.|
|[BLOB_NAME](#blob_name)|Używane do powiązania duży obiekt binarny według nazwy kolumny.|
|[BLOB_NAME_LENGTH](#blob_name_length)|Raporty długość kolumny danych obiektów BLOB.|
|[BLOB_NAME_LENGTH_STATUS](#blob_name_length_status)|Raporty długość i stan kolumny danych obiektów BLOB.|
|[BLOB_NAME_STATUS](#blob_name_status)|Informuje o stanie kolumnę danych obiektów BLOB.|
|[BOOKMARK_ENTRY](#bookmark_entry)|Reprezentuje wpis zakładki w zestawie wierszy. Wpis zakładka jest specjalnym rodzajem wpisu kolumny.|
|[COLUMN_ENTRY](#column_entry)|Reprezentuje wiązanie do określonej kolumny w bazie danych.|
|[COLUMN_ENTRY_EX](#column_entry_ex)|Reprezentuje powiązanie z określonej kolumny w bazie danych. Obsługuje *typu*, *długość*, *dokładności*, *skalowania*, i *stan* parametrów.|
|[COLUMN_ENTRY_LENGTH](#column_entry_length)|Reprezentuje powiązanie z określonej kolumny w bazie danych. Obsługuje *długość* zmiennej.|
|[COLUMN_ENTRY_LENGTH_STATUS](#column_entry_length_status)|Reprezentuje powiązanie z określonej kolumny w bazie danych. Obsługuje *stan* i *długość* parametrów.|
|[COLUMN_ENTRY_PS](#column_entry_ps)|Reprezentuje powiązanie z określonej kolumny w bazie danych. Obsługuje *dokładności* i *skalowania* parametrów.|
|[COLUMN_ENTRY_PS_LENGTH](#column_entry_ps_length)|Reprezentuje powiązanie z określonej kolumny w bazie danych. Obsługuje *długość* zmiennej *dokładności* i *skalowania* parametrów.|
|[COLUMN_ENTRY_PS_LENGTH_STATUS](#column_entry_ps_length_status)|Reprezentuje powiązanie z określonej kolumny w bazie danych. Obsługuje *stan* i *długość* zmiennych, *dokładności* i *skalowania* parametrów.|
|[COLUMN_ENTRY_PS_STATUS](#column_entry_ps_status)|Reprezentuje powiązanie z określonej kolumny w bazie danych. Obsługuje *stan* zmiennej *dokładności* i *skalowania* parametrów.|
|[COLUMN_ENTRY_STATUS](#column_entry_status)|Reprezentuje powiązanie z określonej kolumny w bazie danych. Obsługuje *stan* zmiennej.|
|[COLUMN_ENTRY_TYPE](#column_entry_type)|Reprezentuje wiązanie do określonej kolumny w bazie danych. Obsługuje *typu* parametru.|
|[COLUMN_ENTRY_TYPE_SIZE](#column_entry_type_size)|Reprezentuje powiązanie z określonej kolumny w bazie danych. Obsługuje *typu* i *rozmiar* parametrów.|
|[COLUMN_NAME](#column_name)|Reprezentuje wiązanie do określonej kolumny w bazie danych według nazwy.|
|[COLUMN_NAME_EX](#column_name_ex)|Reprezentuje wiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje specyfikację typu danych, rozmiaru, dokładność, skala, długość kolumny i stan kolumny.|
|[COLUMN_NAME_LENGTH](#column_name_length)|Reprezentuje wiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje specyfikację długość kolumny.|
|[COLUMN_NAME_LENGTH_STATUS](#column_name_length_status)|Reprezentuje wiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje specyfikację długość kolumny i stanu.|
|[COLUMN_NAME_PS](#column_name_ps)|Reprezentuje wiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje specyfikację dokładności i skali.|
|[COLUMN_NAME_PS_LENGTH](#column_name_ps_length)|Reprezentuje wiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje specyfikację długości dokładność, skalę i kolumny.|
|[COLUMN_NAME_PS_LENGTH_STATUS](#column_name_ps_length_status)|Reprezentuje wiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje specyfikację dokładność, skala, długość kolumny i kolumny Stan.|
|[COLUMN_NAME_PS_STATUS](#column_name_ps_status)|Reprezentuje wiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje specyfikację dokładność, skalę i kolumny stanu.|
|[COLUMN_NAME_STATUS](#column_name_status)|Reprezentuje wiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje specyfikację stan kolumny.|
|[COLUMN_NAME_TYPE](#column_name_type)|Reprezentuje wiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje Specyfikacja typu danych.|
|[COLUMN_NAME_TYPE_PS](#column_name_type_ps)|Reprezentuje wiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje specyfikację typu danych, dokładności i skali.|
|[COLUMN_NAME_TYPE_SIZE](#column_name_type_size)|Reprezentuje wiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje specyfikację typu danych oraz jego rozmiaru.|
|[COLUMN_NAME_TYPE_STATUS](#column_name_type_status)|Reprezentuje wiązanie do określonej kolumny w bazie danych według nazwy. Obsługuje specyfikację stan typu i kolumn danych.|
|[END_COLUMN_MAP](#end_column_map)|Oznacza koniec wpisy mapy kolumny.|

## <a name="command-macros"></a>Makra poleceń

|||
|-|-|
|[DEFINE_COMMAND](#define_command)|Określa polecenie, które będą służyć do tworzenia zestawu wierszy, korzystając z [CCommand](../../data/oledb/ccommand-class.md) klasy. Akceptuje tylko typy parametrów odpowiadał typowi określonej aplikacji (ANSI lub Unicode). Zaleca się, że używasz [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) zamiast DEFINE_COMMAND.|
|[DEFINE_COMMAND_EX](#define_command_ex)|Określa polecenie, które będą służyć do tworzenia zestawu wierszy, korzystając z [CCommand](../../data/oledb/ccommand-class.md) klasy. Obsługuje aplikacje ANSI i Unicode.|

## <a name="parameter-map-macros"></a>Makra mapy parametru

|||
|-|-|
|[BEGIN_PARAM_MAP](#begin_param_map)|Oznacza początek wpisy mapy parametr w klasie rekordu użytkownika.|
|[END_PARAM_MAP](#end_param_map)|Oznacza koniec wpisy mapy parametru.|
|[SET_PARAM_TYPE](#set_param_type)|Określa makra COLUMN_ENTRY, które należy wykonać SET_PARAM_TYPE — makro jako danych wejściowych, danych wyjściowych lub wejścia/wyjścia.|

### <a name="atltraceerrorrecords"></a> AtlTraceErrorRecords

Zrzuca informacje o OLE DB rekordu błędu na urządzeniu zrzutu, jeśli zostanie zwrócony błąd.

#### <a name="syntax"></a>Składnia

```cpp
inline void AtlTraceErrorRecords(HRESULT hrErr = S_OK);
```

#### <a name="parameters"></a>Parametry

*hErr*<br/>
[in] Wartości HRESULT zwracane przez funkcję elementu członkowskiego OLE DB szablon konsumenta.

#### <a name="remarks"></a>Uwagi

Jeśli *hErr* nie jest S_OK, `AtlTraceErrorRecords` Zrzuca informacje OLE DB rekordu błędu na urządzeniu zrzutu ( **debugowania** karty w oknie danych wyjściowych lub pliku). Rekord błędu informacje uzyskane od dostawcy zawiera numer wiersza, źródło, opis, pliku pomocy, kontekstu i identyfikator GUID dla każdego wpisu rekordów błędów. `AtlTraceErrorRecords` Zrzuca te informacje tylko w kompilacjach do debugowania. W kompilacjach do wydania jest pusty odcinek, który jest zoptymalizowany pod kątem out. Aby uzyskać więcej informacji, zobacz [cdberrorinfo — klasa](../../data/oledb/cdberrorinfo-class.md).

### <a name="begin_accessor"></a> BEGIN_ACCESSOR

Oznacza początek wpisu dostępu.

#### <a name="syntax"></a>Składnia

```cpp
BEGIN_ACCESSOR(num, bAuto)
```

#### <a name="parameters"></a>Parametry

*num*<br/>
[in] Przesunięcie zero numer dostępu na tej mapie metody dostępu.

*bAuto*<br/>
[in] Określa, czy metoda dostępu do tej metody dostępu automatyczne lub ręczne metody dostępu. Jeśli **true**, metody dostępu jest ustalana automatycznie; Jeśli **false**, Metoda dostępu jest ręczne. Metody dostępu automatycznie oznacza, że pobierane dane dla Ciebie w operacji przenoszenia.

#### <a name="remarks"></a>Uwagi

W przypadku wielu metod dostępu w zestawie wierszy należy określić BEGIN_ACCESSOR_MAP i użyć BEGIN_ACCESSOR — makro dla każdego poszczególne metody dostępu. BEGIN_ACCESSOR — makro zostało zakończone z END_ACCESSOR — makro. BEGIN_ACCESSOR_MAP — makro zostało zakończone z END_ACCESSOR_MAP — makro.

#### <a name="example"></a>Przykład

Zobacz [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="begin_accessor_map"></a> BEGIN_ACCESSOR_MAP

Oznacza początek wpisy mapy dostępu.

#### <a name="syntax"></a>Składnia

```cpp
BEGIN_ACCESSOR_MAP(x, num)
```

#### <a name="parameters"></a>Parametry

*x*<br/>
[in] Nazwa klasy rekordu użytkownika.

*num*<br/>
[in] Liczba metod dostępu na tej mapie metody dostępu.

#### <a name="remarks"></a>Uwagi

W przypadku wielu metod dostępu w zestawie wierszy należy określić BEGIN_ACCESSOR_MAP na początku i użyć BEGIN_ACCESSOR — makro dla każdego poszczególne metody dostępu. BEGIN_ACCESSOR — makro zostało zakończone z END_ACCESSOR — makro. Mapa metody dostępu jest wykonywane przy użyciu END_ACCESSOR_MAP — makro.

Jeśli masz tylko jedną metodę dostępu w rekordzie użytkownika, należy użyć makra [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md).

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

### <a name="end_accessor"></a> END_ACCESSOR

Oznacza koniec wpisu dostępu.

#### <a name="syntax"></a>Składnia

```cpp
END_ACCESSOR()
```

#### <a name="remarks"></a>Uwagi

Dla wielu metod dostępu w zestawie wierszy należy określić BEGIN_ACCESSOR_MAP i użyć BEGIN_ACCESSOR — makro dla każdego poszczególne metody dostępu. BEGIN_ACCESSOR — makro zostało zakończone z END_ACCESSOR — makro. BEGIN_ACCESSOR_MAP — makro zostało zakończone z END_ACCESSOR_MAP — makro.

#### <a name="example"></a>Przykład

Zobacz [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="end_accessor_map"></a> END_ACCESSOR_MAP

Oznacza koniec wpisy mapy dostępu.

#### <a name="syntax"></a>Składnia

```cpp
END_ACCESSOR_MAP()
```

#### <a name="remarks"></a>Uwagi

Dla wielu metod dostępu w zestawie wierszy należy określić BEGIN_ACCESSOR_MAP i użyć BEGIN_ACCESSOR — makro dla każdego poszczególne metody dostępu. BEGIN_ACCESSOR — makro zostało zakończone z END_ACCESSOR — makro. BEGIN_ACCESSOR_MAP — makro zostało zakończone z END_ACCESSOR_MAP — makro.

#### <a name="example"></a>Przykład

Zobacz [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="begin_column_map"></a> BEGIN_COLUMN_MAP

Oznacza początek wpisu mapowania kolumn.

#### <a name="syntax"></a>Składnia

```cpp
BEGIN_COLUMN_MAP(x)
```

#### <a name="parameters"></a>Parametry

*x*<br/>
[in] Nazwa klasy rekordu użytkownika tworzona na podstawie `CAccessor`.

#### <a name="remarks"></a>Uwagi

To makro jest używane w przypadku pojedynczej metody dostępu w zestawie wierszy. Jeśli masz wielu metod dostępu w zestawie wierszy użyć [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

BEGIN_COLUMN_MAP — makro zostało zakończone z END_COLUMN_MAP — makro. To makro jest używane, gdy istnieje tylko jedna metoda dostępu do wymaganych w rekordzie użytkownika.

Kolumny odnoszą się do pól w zestawie wierszy, które chcesz powiązać.

#### <a name="example"></a>Przykład

Oto mapy próbki kolumny i parametru:

<!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->

### <a name="blob_entry"></a> BLOB_ENTRY

Używane z BEGIN_COLUMN_MAP i END_COLUMN_MAP powiązać duży obiekt binarny ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))).

#### <a name="syntax"></a>Składnia

```cpp
BLOB_ENTRY(nOrdinal, IID, flags, data)
```

#### <a name="parameters"></a>Parametry

*nOrdinal*<br/>
[in] Numer kolumny.

*IID*<br/>
[in] Interfejs identyfikatora GUID, takich jak `IDD_ISequentialStream`, który jest używany do pobierania obiektu BLOB.

*flagi*<br/>
[in] Tryb przechowywania flagi zgodnie z definicją w modelu magazynu strukturalnego OLE (na przykład `STGM_READ`).

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="example"></a>Przykład

Zobacz [sposób pobierania obiektu BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_length"></a> BLOB_ENTRY_LENGTH

Używane z BEGIN_COLUMN_MAP i END_COLUMN_MAP powiązać duży obiekt binarny ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobnie jak [BLOB_ENTRY](../../data/oledb/blob-entry.md), z tą różnicą, że to makro również pobiera długość w bajtach dla kolumny obiektu BLOB.

#### <a name="syntax"></a>Składnia

```cpp
BLOB_ENTRY_LENGTH(nOrdinal, IID, flags, data, length)
```

#### <a name="parameters"></a>Parametry

*nOrdinal*<br/>
[in] Numer kolumny.

*IID*<br/>
[in] Interfejs identyfikatora GUID, takich jak `IDD_ISequentialStream`, który jest używany do pobierania obiektu BLOB.

*flagi*<br/>
[in] Tryb przechowywania flagi zgodnie z definicją w modelu magazynu strukturalnego OLE (na przykład `STGM_READ`).

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[out] (Rzeczywiste) długość w bajtach kolumny obiektów BLOB.

#### <a name="example"></a>Przykład

Zobacz [sposób pobierania obiektu BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_length_status"></a> BLOB_ENTRY_LENGTH_STATUS

Używane z BEGIN_COLUMN_MAP i END_COLUMN_MAP powiązać duży obiekt binarny ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobnie jak [BLOB_ENTRY](../../data/oledb/blob-entry.md), z tą różnicą, że to makro również pobiera długość i stan dla kolumny obiektu BLOB.

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
[in] Numer kolumny.

*IID*<br/>
[in] Interfejs identyfikatora GUID, takich jak `IDD_ISequentialStream`, który jest używany do pobierania obiektu BLOB.

*flagi*<br/>
[in] Tryb przechowywania flagi zgodnie z definicją w modelu magazynu strukturalnego OLE (na przykład `STGM_READ`).

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[out] (Rzeczywiste) długość w bajtach kolumny obiektów BLOB.

*status*<br/>
[out] Stan kolumny danych obiektów BLOB.

#### <a name="example"></a>Przykład

Zobacz [sposób pobierania obiektu BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_status"></a> BLOB_ENTRY_STATUS

Używane z BEGIN_COLUMN_MAP lub BEGIN_ACCESSOR_MAP powiązać duży obiekt binarny ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobnie jak [BLOB_ENTRY](../../data/oledb/blob-entry.md), z tą różnicą, że to makro, staje się również stan dla kolumny obiektu BLOB.

#### <a name="syntax"></a>Składnia

```cpp
BLOB_ENTRY_STATUS(nOrdinal, IID, flags, data, status)
```

#### <a name="parameters"></a>Parametry

*nOrdinal*<br/>
[in] Numer kolumny.

*IID*<br/>
[in] Interfejs identyfikatora GUID, takich jak `IDD_ISequentialStream`, który jest używany do pobierania obiektu BLOB.

*flagi*<br/>
[in] Tryb przechowywania flagi zgodnie z definicją w modelu magazynu strukturalnego OLE (na przykład `STGM_READ`).

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

*status*<br/>
[out] Stan pola obiektu BLOB.

#### <a name="example"></a>Przykład

Zobacz [sposób pobierania obiektu BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_name"></a> BLOB_NAME

Używane z BEGIN_COLUMN_MAP i END_COLUMN_MAP powiązać duży obiekt binarny ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobnie jak [BLOB_ENTRY](../../data/oledb/blob-entry.md), z tą różnicą, że to makro przyjmuje nazwę kolumny zamiast numeru kolumny.

#### <a name="syntax"></a>Składnia

```cpp
BLOB_NAME(pszName, IID, flags, data )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Wskaźnik na nazwę kolumny. Nazwa musi być ciąg Unicode. Można to zrobić poprzez umieszczenie "L" przed nazwą, na przykład: `L"MyColumn"`.

*IID*<br/>
[in] Interfejs identyfikatora GUID, takich jak `IDD_ISequentialStream`, który jest używany do pobierania obiektu BLOB.

*flagi*<br/>
[in] Tryb przechowywania flagi zgodnie z definicją w modelu magazynu strukturalnego OLE (na przykład `STGM_READ`).

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="example"></a>Przykład

Zobacz [sposób pobierania obiektu BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_name_length"></a> BLOB_NAME_LENGTH

Używane z BEGIN_COLUMN_MAP i END_COLUMN_MAP powiązać duży obiekt binarny ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobnie jak [BLOB_NAME](../../data/oledb/blob-name.md), z tą różnicą, że to makro również pobiera długość w bajtach kolumny danych obiektów BLOB.

#### <a name="syntax"></a>Składnia

```cpp
BLOB_NAME_LENGTH(pszName, IID, flags, data, length )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Wskaźnik na nazwę kolumny. Nazwa musi być ciąg Unicode. Można to zrobić poprzez umieszczenie "L" przed nazwą, na przykład: `L"MyColumn"`.

*IID*<br/>
[in] Interfejs identyfikatora GUID, takich jak `IDD_ISequentialStream`, który jest używany do pobierania obiektu BLOB.

*flagi*<br/>
[in] Tryb przechowywania flagi zgodnie z definicją w modelu magazynu strukturalnego OLE (na przykład `STGM_READ`).

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[out] (Rzeczywiste) długość w bajtach kolumny obiektów BLOB.

### <a name="blob_name_length_status"></a> BLOB_NAME_LENGTH_STATUS

Używane z BEGIN_COLUMN_MAP i END_COLUMN_MAP powiązać duży obiekt binarny ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobnie jak [BLOB_NAME](../../data/oledb/blob-name.md), z tą różnicą, że to makro również pobiera długość i stan kolumny danych obiektów BLOB.

#### <a name="syntax"></a>Składnia

```cpp
BLOB_NAME_LENGTH_STATUS(pszName, IID, flags, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Wskaźnik na nazwę kolumny. Nazwa musi być ciąg Unicode. Można to zrobić poprzez umieszczenie "L" przed nazwą, na przykład: `L"MyColumn"`.

*IID*<br/>
[in] Interfejs identyfikatora GUID, takich jak `IDD_ISequentialStream`, który jest używany do pobierania obiektu BLOB.

*flagi*<br/>
[in] Tryb przechowywania flagi zgodnie z definicją w modelu magazynu strukturalnego OLE (na przykład `STGM_READ`).

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[out] (Rzeczywiste) długość w bajtach kolumny obiektów BLOB.

*status*<br/>
[out] Stan pola obiektu BLOB.

### <a name="blob_name_status"></a> BLOB_NAME_STATUS

Używane z BEGIN_COLUMN_MAP i END_COLUMN_MAP powiązać duży obiekt binarny ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobnie jak [BLOB_NAME](../../data/oledb/blob-name.md), z tą różnicą, że to makro jest również pobiera stan kolumny danych obiektów BLOB.

#### <a name="syntax"></a>Składnia

```cpp
BLOB_NAME_STATUS(pszName, IID, flags, data, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Wskaźnik na nazwę kolumny. Nazwa musi być ciąg Unicode. Można to zrobić poprzez umieszczenie "L" przed nazwą, na przykład: `L"MyColumn"`.

*IID*<br/>
[in] Interfejs identyfikatora GUID, takich jak `IDD_ISequentialStream`, który jest używany do pobierania obiektu BLOB.

*flagi*<br/>
[in] Tryb przechowywania flagi zgodnie z definicją w modelu magazynu strukturalnego OLE (na przykład `STGM_READ`).

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

*status*<br/>
[out] Stan pola obiektu BLOB.

### <a name="bookmark_entry"></a> BOOKMARK_ENTRY

Wiąże kolumna zakładki.

#### <a name="syntax"></a>Składnia

```cpp
BOOKMARK_ENTRY(variable)
```

#### <a name="parameters"></a>Parametry

*Zmienna*<br/>
[in] Zmienna, która ma być powiązana z kolumną zakładki.

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

Aby uzyskać więcej informacji, zobacz [przy użyciu zakładki](using-bookmarks.md) i [klasa CBookmark](../../data/oledb/cbookmark-class.md).

### <a name="column_entry"></a> COLUMN_ENTRY

Reprezentuje powiązanie w zestawie wierszy do określonej kolumny w zestawie wierszy.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY(nOrdinal, data)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *OLE DB Podręcznik programisty*.

*nOrdinal*<br/>
[in] Numer kolumny.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

COLUMN_ENTRY — makro jest używane w następujących miejscach:

- Między [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP](../../data/oledb/end-column-map.md) makra.

- Między [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Między [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

#### <a name="example"></a>Przykład

Zobacz przykłady w tematach — makro [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="column_entry_ex"></a> COLUMN_ENTRY_EX

Reprezentuje powiązanie w zestawie wierszy do określonej kolumny w bazie danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_EX(nOrdinal, wType, nLength, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *OLE DB Podręcznik programisty*.

*nOrdinal*<br/>
[in] Numer kolumny.

*wType*<br/>
[in] Typ danych.

*nLength*<br/>
[in] Rozmiar danych w bajtach.

*nPrecision*<br/>
[in] Maksymalna dozwolona dokładność do użycia podczas pobierania danych i *wType* jest `DBTYPE_NUMERIC`. W przeciwnym razie ten parametr jest ignorowany.

*nScale*<br/>
[in] Skalowanie do użycia podczas pobierania danych i *wType* jest `DBTYPE_NUMERIC` lub `DBTYPE_DECIMAL`.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[in] Zmienna, która może być powiązane z długość kolumny.

*status*<br/>
[in] Zmienna, która może być powiązane z stan kolumny.

#### <a name="remarks"></a>Uwagi

COLUMN_ENTRY_EX — makro jest używane w następujących miejscach:

- Między [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP](../../data/oledb/end-column-map.md) makra.

- Między [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Między [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

#### <a name="example"></a>Przykład

Zobacz [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="column_entry_length"></a> COLUMN_ENTRY_LENGTH

Reprezentuje powiązanie w zestawie wierszy do określonej kolumny w bazie danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_LENGTH(nOrdinal, data, length)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *OLE DB Podręcznik programisty*.

*nOrdinal*<br/>
[in] Numer kolumny, zaczynając od jednej. Zakładka odnosi się do kolumny zero.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[in] Zmienna, która może być powiązane z długość kolumny.

#### <a name="remarks"></a>Uwagi

To makro obsługuje *długość* zmiennej. Jest on używany w następujących miejscach:

- Między [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP](../../data/oledb/end-column-map.md) makra.

- Między [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Między [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_entry_length_status"></a> COLUMN_ENTRY_LENGTH_STATUS

Reprezentuje powiązanie w zestawie wierszy do określonej kolumny w bazie danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_LENGTH_STATUS(nOrdinal, data, length, status)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *OLE DB Podręcznik programisty*.

*nOrdinal*<br/>
[in] Numer kolumny.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[in] Zmienna, która może być powiązane z długość kolumny.

*status*<br/>
[in] Zmienna, która może być powiązane z stan kolumny.

#### <a name="remarks"></a>Uwagi

Użyj tego makra, gdy chcesz obsługiwać zmiennych długości i stanu. Jest on używany w następujących miejscach:

- Między [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP](../../data/oledb/end-column-map.md) makra.

- Między [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Między [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_entry_ps"></a> COLUMN_ENTRY_PS

Reprezentuje powiązanie w zestawie wierszy do określonej kolumny w zestawie wierszy.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_PS(nOrdinal, nPrecision, nScale, data)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *OLE DB Podręcznik programisty*.

*nOrdinal*<br/>
[in] Numer kolumny.

*nPrecision*<br/>
[in] Precyzja maksymalna kolumnę, którą chcesz powiązać.

*nScale*<br/>
[in] Skala kolumny, którą chcesz powiązać.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

Pozwala określić dokładności i skali kolumnę, którą chcesz powiązać. Jest on używany w następujących miejscach:

- Między [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP](../../data/oledb/end-column-map.md) makra.

- Między [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Między [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_entry_ps_length"></a> COLUMN_ENTRY_PS_LENGTH

Reprezentuje powiązanie w zestawie wierszy do określonej kolumny w bazie danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_PS_LENGTH(nOrdinal, nPrecision, nScale, data, length)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *OLE DB Podręcznik programisty*.

*nOrdinal*<br/>
[in] Numer kolumny, zaczynając od jednej. Zakładka odnosi się do kolumny zero.

*nPrecision*<br/>
[in] Precyzja maksymalna kolumnę, którą chcesz powiązać.

*nScale*<br/>
[in] Skala kolumny, którą chcesz powiązać.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[in] Zmienna, która może być powiązane z długość kolumny.

#### <a name="remarks"></a>Uwagi

Pozwala określić dokładności i skali kolumnę, którą chcesz powiązać. To makro obsługuje *długość* zmiennej. Jest on używany w następujących miejscach:

- Między [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP](../../data/oledb/end-column-map.md) makra.

- Między [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Między [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_entry_ps_length_status"></a> COLUMN_ENTRY_PS_LENGTH_STATUS

Reprezentuje powiązanie w zestawie wierszy do określonej kolumny w bazie danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_PS_LENGTH_STATUS(nOrdinal, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *OLE DB Podręcznik programisty*.

*nOrdinal*<br/>
[in] Numer kolumny.

*nPrecision*<br/>
[in] Precyzja maksymalna kolumnę, którą chcesz powiązać.

*nScale*<br/>
[in] Skala kolumny, którą chcesz powiązać.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[in] Zmienna, która może być powiązane z długość kolumny.

*status*<br/>
[in] Zmienna, która może być powiązane z stan kolumny.

#### <a name="remarks"></a>Uwagi

Pozwala określić dokładności i skali kolumnę, którą chcesz powiązać. Użyj tego makra, gdy chcesz obsługiwać zmiennych długości i stanu. Jest on używany w następujących miejscach:

- Między [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP](../../data/oledb/end-column-map.md) makra.

- Między [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Między [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_entry_ps_status"></a> COLUMN_ENTRY_PS_STATUS

Reprezentuje powiązanie w zestawie wierszy do określonej kolumny w bazie danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_PS_STATUS(nOrdinal, nPrecision, nScale, data, status)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *OLE DB Podręcznik programisty*.

*nOrdinal*<br/>
[in] Numer kolumny.

*nPrecision*<br/>
[in] Precyzja maksymalna kolumnę, którą chcesz powiązać.

*nScale*<br/>
[in] Skala kolumny, którą chcesz powiązać.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

*status*<br/>
[in] Zmienna, która może być powiązane z stan kolumny.

#### <a name="remarks"></a>Uwagi

Pozwala określić dokładności i skali kolumnę, którą chcesz powiązać. To makro obsługuje *stan* zmiennej. Jest on używany w następujących miejscach:

- Między [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP](../../data/oledb/end-column-map.md) makra.

- Między [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Między [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_entry_status"></a> COLUMN_ENTRY_STATUS

Reprezentuje powiązanie w zestawie wierszy do określonej kolumny w bazie danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_STATUS(nOrdinal, data, status)
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *OLE DB Podręcznik programisty*.

*nOrdinal*<br/>
[in] Numer kolumny.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

*status*<br/>
[in] Zmienna, która może być powiązane z stan kolumny.

#### <a name="remarks"></a>Uwagi

To makro obsługuje *stan* zmiennej. Jest on używany w następujących miejscach:

- Między [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP](../../data/oledb/end-column-map.md) makra.

- Między [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Między [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_entry_type"></a> COLUMN_ENTRY_TYPE

Reprezentuje powiązanie z określonej kolumny w bazie danych. Obsługuje *typu* parametru.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_TYPE (nOrdinal, wType, data)
```

#### <a name="parameters"></a>Parametry

*nOrdinal*<br/>
[in] Numer kolumny.

*wType*<br/>
[in] Typ danych kolumny wpisu.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

To makro jest wyspecjalizowane wariant [COLUMN_ENTRY](../../data/oledb/column-entry.md) makro, które umożliwia określenie typu danych.

### <a name="column_entry_type_size"></a> COLUMN_ENTRY_TYPE_SIZE

Reprezentuje powiązanie z określonej kolumny w bazie danych. Obsługuje *typu* i *rozmiar* parametrów.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)
```

#### <a name="parameters"></a>Parametry

*nOrdinal*<br/>
[in] Numer kolumny.

*wType*<br/>
[in] Typ danych kolumny wpisu.

*nLength*<br/>
[in] Rozmiar zapisu kolumny w bajtach.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

To makro jest wyspecjalizowane wariant [COLUMN_ENTRY](../../data/oledb/column-entry.md) makro, które umożliwia określenie typu i rozmiaru danych.

### <a name="column_name"></a> COLUMN_NAME

Reprezentuje powiązanie w zestawie wierszy do określonej kolumny w zestawie wierszy. Podobnie jak [COLUMN_ENTRY](../../data/oledb/column-entry.md), z tą różnicą, że to makro przyjmuje nazwę kolumny zamiast numeru kolumny.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME(pszName, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Wskaźnik na nazwę kolumny. Nazwa musi być ciąg Unicode. Można to zrobić poprzez umieszczenie "L" przed nazwą, na przykład: `L"MyColumn"`.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

Makra COLUMN_NAME_ * są używane w tych samych miejsc co [COLUMN_ENTRY](../../data/oledb/column-entry.md):

- Między [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) i [END_COLUMN_MAP](../../data/oledb/end-column-map.md) makra.

- Między [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) i [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Między [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) i [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_name_ex"></a> COLUMN_NAME_EX

Reprezentuje powiązanie w zestawie wierszy do określonej kolumny w zestawie wierszy. Podobnie jak [COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że to makro również ma typ danych, rozmiar, dokładności, skala, długość kolumny i stan kolumny.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_EX(pszName, wType, nLength, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Wskaźnik na nazwę kolumny. Nazwa musi być ciąg Unicode. Można to zrobić poprzez umieszczenie "L" przed nazwą, na przykład: `L"MyColumn"`.

*wType*<br/>
[in] Typ danych.

*nLength*<br/>
[in] Rozmiar danych w bajtach.

*nPrecision*<br/>
[in] Maksymalna dozwolona dokładność do użycia podczas pobierania danych i *wType* jest `DBTYPE_NUMERIC`. W przeciwnym razie ten parametr jest ignorowany.

*nScale*<br/>
[in] Skalowanie do użycia podczas pobierania danych i *wType* jest `DBTYPE_NUMERIC` lub `DBTYPE_DECIMAL`.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[in] Zmienna, która może być powiązane z długość kolumny.

*status*<br/>
[in] Zmienna, która może być powiązane z stan kolumny.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME](../../data/oledb/column-name.md) uzyskać informacji na temat użycia makra COLUMN_NAME_ *.

### <a name="column_name_length"></a> COLUMN_NAME_LENGTH

Reprezentuje powiązanie w zestawie wierszy do określonej kolumny w zestawie wierszy. Podobnie jak [COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że to makro, również ma długość kolumny.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_LENGTH(pszName, data, length)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Wskaźnik na nazwę kolumny. Nazwa musi być ciąg Unicode. Można to zrobić poprzez umieszczenie "L" przed nazwą, na przykład: `L"MyColumn"`.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[in] Zmienna, która może być powiązane z długość kolumny.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME](../../data/oledb/column-name.md) uzyskać informacji na temat użycia makra COLUMN_NAME_ *.

### <a name="column_name_length_status"></a> COLUMN_NAME_LENGTH_STATUS

Reprezentuje powiązanie w zestawie wierszy do określonej kolumny w zestawie wierszy. Podobnie jak [COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że to makro również ma długość kolumny i kolumny Stan.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_LENGTH_STATUS(pszName, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Wskaźnik na nazwę kolumny. Nazwa musi być ciąg Unicode. Można to zrobić poprzez umieszczenie "L" przed nazwą, na przykład: `L"MyColumn"`.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[in] Zmienna, która może być powiązane z długość kolumny.

*status*<br/>
[in] Zmienna, która może być powiązane z stan kolumny.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME](../../data/oledb/column-name.md) uzyskać informacji na temat użycia makra COLUMN_NAME_ *.

### <a name="column_name_ps"></a> COLUMN_NAME_PS

Reprezentuje powiązanie w zestawie wierszy do określonej kolumny w zestawie wierszy. Podobnie jak [COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że to makro pobiera również dokładności i skali.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_PS(pszName, nPrecision, nScale, data )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Wskaźnik na nazwę kolumny. Nazwa musi być ciąg Unicode. Można to zrobić poprzez umieszczenie "L" przed nazwą, na przykład: `L"MyColumn"`.

*nPrecision*<br/>
[in] Precyzja maksymalna kolumnę, którą chcesz powiązać.

*nScale*<br/>
[in] Skala kolumny, którą chcesz powiązać.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME](../../data/oledb/column-name.md) uzyskać informacji na temat użycia makra COLUMN_NAME_ *.

### <a name="column_name_ps_length"></a> COLUMN_NAME_PS_LENGTH

Reprezentuje powiązanie w zestawie wierszy do określonej kolumny w zestawie wierszy. Podobnie jak [COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że to makro również ma długość dokładność, skalę i kolumny.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_PS_LENGTH(pszName, nPrecision, nScale, data, length )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Wskaźnik na nazwę kolumny. Nazwa musi być ciąg Unicode. Można to zrobić poprzez umieszczenie "L" przed nazwą, na przykład: `L"MyColumn"`.

*nPrecision*<br/>
[in] Precyzja maksymalna kolumnę, którą chcesz powiązać.

*nScale*<br/>
[in] Skala kolumny, którą chcesz powiązać.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[in] Zmienna, która może być powiązane z długość kolumny.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME](../../data/oledb/column-name.md) uzyskać informacji na temat użycia makra COLUMN_NAME_ *.

### <a name="column_name_ps_length_status"></a> COLUMN_NAME_PS_LENGTH_STATUS

Reprezentuje powiązanie w zestawie wierszy do określonej kolumny w zestawie wierszy. Podobnie jak [COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że to makro pobiera również dokładność, skala, długość kolumny i kolumny Stan.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_PS_LENGTH_STATUS(pszName, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Wskaźnik na nazwę kolumny. Nazwa musi być ciąg Unicode. Można to zrobić poprzez umieszczenie "L" przed nazwą, na przykład: `L"MyColumn"`.

*nPrecision*<br/>
[in] Precyzja maksymalna kolumnę, którą chcesz powiązać.

*nScale*<br/>
[in] Skala kolumny, którą chcesz powiązać.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

*Długość*<br/>
[in] Zmienna, która może być powiązane z długość kolumny.

*status*<br/>
[in] Zmienna, która może być powiązane z stan kolumny.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME](../../data/oledb/column-name.md) uzyskać informacji na temat użycia makra COLUMN_NAME_ *.

### <a name="column_name_ps_status"></a> COLUMN_NAME_PS_STATUS

Reprezentuje powiązanie w zestawie wierszy do określonej kolumny w zestawie wierszy. Podobnie jak [COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że to makro pobiera również dokładność, skalę i kolumny stanu.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_PS_STATUS(pszName, nPrecision, nScale, data, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Wskaźnik na nazwę kolumny. Nazwa musi być ciąg Unicode. Można to zrobić poprzez umieszczenie "L" przed nazwą, na przykład: `L"MyColumn"`.

*nPrecision*<br/>
[in] Precyzja maksymalna kolumnę, którą chcesz powiązać.

*nScale*<br/>
[in] Skala kolumny, którą chcesz powiązać.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

*status*<br/>
[in] Zmienna, która może być powiązane z stan kolumny.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME](../../data/oledb/column-name.md) uzyskać informacji na temat użycia makra COLUMN_NAME_ *.

### <a name="column_name_status"></a> COLUMN_NAME_STATUS

Reprezentuje powiązanie w zestawie wierszy do określonej kolumny w zestawie wierszy. Podobnie jak [COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że to makro również ma stan kolumny.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_STATUS(pszName, data, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Wskaźnik na nazwę kolumny. Nazwa musi być ciąg Unicode. Można to zrobić poprzez umieszczenie "L" przed nazwą, na przykład: `L"MyColumn"`.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

*status*<br/>
[in] Zmienna, która może być powiązane z stan kolumny.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME](../../data/oledb/column-name.md) uzyskać informacji na temat użycia makra COLUMN_NAME_ *.

### <a name="column_name_type"></a> COLUMN_NAME_TYPE

Reprezentuje powiązanie w zestawie wierszy do określonej kolumny w zestawie wierszy. Podobnie jak [COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że to makro również ma typ danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_TYPE(pszName, wType, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Wskaźnik na nazwę kolumny. Nazwa musi być ciąg Unicode. Można to zrobić poprzez umieszczenie "L" przed nazwą, na przykład: `L"MyColumn"`.

*wType*<br/>
[in] Typ danych.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME](../../data/oledb/column-name.md) uzyskać informacji na temat użycia makra COLUMN_NAME_ *.

### <a name="column_name_type_ps"></a> COLUMN_NAME_TYPE_PS

Reprezentuje powiązanie w zestawie wierszy do określonej kolumny w zestawie wierszy. Podobnie jak [COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że to makro również ma typ danych, dokładności i skali.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_TYPE_PS(pszName, wType, nPrecision, nScale, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Wskaźnik na nazwę kolumny. Nazwa musi być ciąg Unicode. Można to zrobić poprzez umieszczenie "L" przed nazwą, na przykład: `L"MyColumn"`.

*wType*<br/>
[in] Typ danych.

*nPrecision*<br/>
[in] Maksymalna dozwolona dokładność do użycia podczas pobierania danych i *wType* jest `DBTYPE_NUMERIC`. W przeciwnym razie ten parametr jest ignorowany.

*nScale*<br/>
[in] Skalowanie do użycia podczas pobierania danych i *wType* jest `DBTYPE_NUMERIC` lub `DBTYPE_DECIMAL`.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME](../../data/oledb/column-name.md) uzyskać informacji na temat użycia makra COLUMN_NAME_ *.

### <a name="column_name_type_size"></a> COLUMN_NAME_TYPE_SIZE

Reprezentuje powiązanie w zestawie wierszy do określonej kolumny w zestawie wierszy. Podobnie jak [COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że to makro pobiera również dane typu i rozmiaru.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_TYPE_SIZE(pszName, wType, nLength, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Wskaźnik na nazwę kolumny. Nazwa musi być ciąg Unicode. Można to zrobić poprzez umieszczenie "L" przed nazwą, na przykład: `L"MyColumn"`.

*wType*<br/>
[in] Typ danych.

*nLength*<br/>
[in] Rozmiar danych w bajtach.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME](../../data/oledb/column-name.md) uzyskać informacji na temat użycia makra COLUMN_NAME_ *.

### <a name="column_name_type_status"></a> COLUMN_NAME_TYPE_STATUS

Reprezentuje powiązanie w zestawie wierszy do określonej kolumny w zestawie wierszy. Podobnie jak [COLUMN_NAME](../../data/oledb/column-name.md), z tą różnicą, że to makro również ma stan typu i kolumn danych.

#### <a name="syntax"></a>Składnia

```cpp
COLUMN_NAME_TYPE_STATUS(pszName, wType, status, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Wskaźnik na nazwę kolumny. Nazwa musi być ciąg Unicode. Można to zrobić poprzez umieszczenie "L" przed nazwą, na przykład: `L"MyColumn"`.

*wType*<br/>
[in] Typ danych.

*status*<br/>
[in] Zmienna, która może być powiązane z stan kolumny.

*data*<br/>
[in] Odpowiedni element członkowski danych w rekordzie użytkownika.

#### <a name="remarks"></a>Uwagi

Zobacz [COLUMN_NAME](../../data/oledb/column-name.md) uzyskać informacji na temat użycia makra COLUMN_NAME_ *.

### <a name="end_column_map"></a> END_COLUMN_MAP

Oznacza koniec wpisy mapy kolumny.

#### <a name="syntax"></a>Składnia

```cpp
END_COLUMN_MAP()
```

#### <a name="remarks"></a>Uwagi

Jest używany z jednej metody dostępu w zestawie wierszy. BEGIN_COLUMN_MAP — makro zostało zakończone z END_COLUMN_MAP — makro.

#### <a name="example"></a>Przykład

See [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md).

### <a name="define_command"></a> DEFINE_COMMAND

Określa polecenie, które będą służyć do tworzenia zestawu wierszy, korzystając z [CCommand](../../data/oledb/ccommand-class.md) klasy. Akceptuje tylko typy parametrów odpowiadał typowi określonej aplikacji (ANSI lub Unicode).

> [!NOTE]
>  Zaleca się, że używasz [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) zamiast DEFINE_COMMAND.

#### <a name="syntax"></a>Składnia

```cpp
DEFINE_COMMAND(x, szCommand)
```

#### <a name="parameters"></a>Parametry

*x*<br/>
[in] Nazwa klasy rekordu (polecenie) użytkownika.

*szCommand*<br/>
[in] Ciąg polecenia, która będzie służyć do tworzenia zestawu wierszy, korzystając z [CCommand](../../data/oledb/ccommand-class.md).

#### <a name="remarks"></a>Uwagi

Ciąg polecenia, które określisz będzie służyć jako domyślny, jeśli nie określisz tekst polecenia w [CCommand::Open](../../data/oledb/ccommand-open.md) metody.

To makro akceptuje ciągów ANSI, jeśli kompilujesz aplikację jako ANSI lub Unicode ciągi, jeśli kompilujesz aplikację w formacie Unicode. Zaleca się, że używasz [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) zamiast DEFINE_COMMAND, ponieważ pierwsza akceptuje ciągi Unicode, niezależnie od typu aplikacji ANSI lub Unicode.

#### <a name="example"></a>Przykład

Zobacz [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="define_command_ex"></a> DEFINE_COMMAND_EX

Określa polecenie, które będą służyć do tworzenia zestawu wierszy, korzystając z [CCommand](../../data/oledb/ccommand-class.md) klasy. Obsługuje aplikacje ANSI i Unicode.

#### <a name="syntax"></a>Składnia

```cpp
DEFINE_COMMAND_EX(x, wszCommand)
```

#### <a name="parameters"></a>Parametry

*x*<br/>
[in] Nazwa klasy rekordu (polecenie) użytkownika.

*wszCommand*<br/>
[in] Ciąg polecenia, która będzie służyć do tworzenia zestawu wierszy, korzystając z [CCommand](../../data/oledb/ccommand-class.md).

#### <a name="remarks"></a>Uwagi

Ciąg polecenia, które określisz będzie służyć jako domyślny, jeśli nie określisz tekst polecenia w [CCommand::Open](../../data/oledb/ccommand-open.md) metody.

To makro akceptuje ciągi Unicode, niezależnie od typu aplikacji. To makro jest preferowana nad [DEFINE_COMMAND](../../data/oledb/define-command.md) ponieważ obsługa Unicode oraz aplikacje ANSI.

#### <a name="example"></a>Przykład

Zobacz [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="begin_param_map"></a> BEGIN_PARAM_MAP

Oznacza początek wpisy mapy parametru.

#### <a name="syntax"></a>Składnia

```cpp
BEGIN_PARAM_MAP(x)
```

#### <a name="parameters"></a>Parametry

*x*<br/>
[in] Nazwa klasy rekordu użytkownika.

#### <a name="remarks"></a>Uwagi

Parametry są używane przez [polecenia](/previous-versions/windows/desktop/ms724608(v=vs.85)).

#### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) makra.

### <a name="end_param_map"></a> END_PARAM_MAP

Oznacza koniec wpisy mapy parametru.

#### <a name="syntax"></a>Składnia

```cpp
END_PARAM_MAP()
```

#### <a name="example"></a>Przykład

Zobacz przykład [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) makra.

### <a name="set_param_type"></a> SET_PARAM_TYPE

Określa makra COLUMN_ENTRY, które należy wykonać SET_PARAM_TYPE — makro danych wejściowych, danych wyjściowych lub wejścia/wyjścia.

#### <a name="syntax"></a>Składnia

```cpp
SET_PARAM_TYPE(type)
```

#### <a name="parameters"></a>Parametry

*type*<br/>
[in] Typ, który można ustawić dla parametru.

#### <a name="remarks"></a>Uwagi

Dostawcy obsługują tylko typy wejścia/wyjścia parametrów, które są obsługiwane przez bazowe źródło danych. Typ składa się z co najmniej jeden `DBPARAMIO` wartości (zobacz [struktury DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *OLE DB Podręcznik programisty*):

- `DBPARAMIO_NOTPARAM` Metoda dostępu nie ma parametrów. Zwykle ustawiasz `eParamIO` tej wartości w metodach dostępu wiersz w celu przypominania użytkownikowi, że parametry są ignorowane.

- `DBPARAMIO_INPUT` Parametr wejściowy.

- `DBPARAMIO_OUTPUT` Parametr wyjściowy.

- `DBPARAMIO_INPUT | DBPARAMIO_OUTPUT` Parametr jest zarówno dane wejściowe, jak i parametr wyjściowy.

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

## <a name="see-also"></a>Zobacz także

[Makra i funkcje globalne dla szablonów konsumentów OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)