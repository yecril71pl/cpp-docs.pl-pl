---
title: Klasa CCommand
ms.date: 11/04/2016
f1_keywords:
- ATL::CCommand
- CCommand
- ATL.CCommand
- CCommand.Close
- CCommand::Close
- CCommand.Create
- CCommand::Create
- CCommand.CreateCommand
- CreateCommand
- CCommand::CreateCommand
- ATL::CCommand::GetNextResult
- CCommand::GetNextResult
- GetNextResult
- CCommand.GetNextResult
- ATL.CCommand.GetNextResult
- GetParameterInfo
- CCommand.GetParameterInfo
- CCommand::GetParameterInfo
- ATL.CCommand.Open
- ATL::CCommand::Open
- CCommand.Open
- CCommand::Open
- CCommand.Prepare
- CCommand::Prepare
- Prepare
- CCommand.ReleaseCommand
- ReleaseCommand
- CCommand::ReleaseCommand
- SetParameterInfo
- CCommand.SetParameterInfo
- CCommand::SetParameterInfo
- Unprepare
- CCommand.Unprepare
- CCommand::Unprepare
helpviewer_keywords:
- CCommand class
- Close method
- Create method [C++]
- CreateCommand method
- GetNextResult method
- GetParameterInfo method
- Open method
- Prepare method
- ReleaseCommand method
- SetParameterInfo method
- Unprepare method
ms.assetid: 0760bfc5-b9ee-4aee-8e54-31bd78714d3a
ms.openlocfilehash: 109998dd742828b3c41672fa2afa8716e4687f6a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501006"
---
# <a name="ccommand-class"></a>Klasa CCommand

Dostarcza metody ustawiające i wykonujące polecenie.

## <a name="syntax"></a>Składnia

```cpp
template <class TAccessor = CNoAccessor,
   template <typename T> class TRowset = CRowset,
   class TMultiple = CNoMultipleResults>
class CCommand :
   public CAccessorRowset <TAccessor, TRowset>,
   public CCommandBase,
   public TMultiple
```

### <a name="parameters"></a>Parametry

*TAccessor*<br/>
Typ klasy akcesora (takich jak `CDynamicParameterAccessor` , `CDynamicStringAccessor` lub `CEnumeratorAccessor` ), która ma być używana przez polecenie. Wartość domyślna to `CNoAccessor` , która określa, że Klasa nie obsługuje parametrów lub kolumn danych wyjściowych.

*TRowset*<br/>
Typ klasy zestawu wierszy (na przykład `CArrayRowset` lub `CNoRowset` ), która ma być używana przez polecenie. Wartość domyślna to `CRowset`.

*TMultiple*<br/>
Aby użyć polecenia OLE DB, które może zwracać wiele wyników, określ [CMultipleResults —](../../data/oledb/cmultipleresults-class.md). W przeciwnym razie użyj [CNoMultipleResults —](../../data/oledb/cnomultipleresults-class.md). Aby uzyskać szczegółowe informacje, zobacz [IMultipleResults](/previous-versions/windows/desktop/ms721289(v=vs.85)).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

| Nazwa | Opis |
|-|-|
|[Zamknij](#close)|Zamyka bieżące polecenie.|
|[GetNextResult](#getnextresult)|Pobiera następny wynik przy użyciu wielu zestawów wyników.|
|[Otwórz](#open)|Wykonuje i opcjonalnie wiąże polecenie.|

### <a name="inherited-methods"></a>Dziedziczone metody

| Nazwa | Opis |
|-|-|
|[Utwórz](#create)|Tworzy nowe polecenie dla określonej sesji, a następnie ustawia tekst polecenia.|
|[CreateCommand](#createcommand)|Tworzy nowe polecenie.|
|[GetParameterInfo](#getparameterinfo)|Pobiera listę parametrów poleceń, ich nazw i ich typów.|
|[Przygotowywanie](#prepare)|Weryfikuje i optymalizuje bieżące polecenie.|
|[ReleaseCommand](#releasecommand)|Zwalnia metodę dostępu do parametru, jeśli jest to konieczne, a następnie zwolni polecenie.|
|[SetParameterInfo](#setparameterinfo)|Określa typ natywny każdego parametru polecenia.|
|[Prepare](#unprepare)|Odrzuca bieżący plan wykonywania polecenia.|

## <a name="remarks"></a>Uwagi

Użyj tej klasy, gdy musisz wykonać operację opartą na parametrach lub wykonać polecenie. Jeśli konieczne jest tylko otwarcie prostego zestawu wierszy, zamiast tego należy użyć [CTable](../../data/oledb/ctable-class.md) .

Używana Klasa akcesora określa metodę powiązań parametrów i danych.

Należy pamiętać, że nie można użyć procedur składowanych z dostawcą OLE DB dla aparatu Jet, ponieważ ten dostawca nie obsługuje procedur składowanych (w ciągach zapytań są dozwolone tylko stałe).

## <a name="ccommandclose"></a><a name="close"></a> CCommand:: Close

Zwalnia zestaw wierszy akcesora skojarzony z poleceniem.

### <a name="syntax"></a>Składnia

```cpp
void Close();
```

### <a name="remarks"></a>Uwagi

Polecenie używa zestawu wierszy, akcesora zestawu wyników i (opcjonalnie) metody dostępu do parametrów (w przeciwieństwie do tabel, które nie obsługują parametrów i nie potrzebują metody dostępu do parametrów).

Po wykonaniu polecenia, należy wywołać oba `Close` i [ReleaseCommand](#releasecommand) po poleceniu.

Aby wielokrotnie wykonać to samo polecenie, należy wydać każdy akcesor zestawu wyników, wywołując `Close` przed wywołaniem `Execute` . Na końcu serii należy zwolnić metodę dostępu do parametru przez wywołanie metody `ReleaseCommand` . Inny typowy scenariusz wywołuje procedurę składowaną, która ma parametry wyjściowe. W przypadku wielu dostawców (takich jak dostawca OLE DB dla SQL Server) wartości parametrów wyjściowych nie będą dostępne do momentu zamknięcia akcesora zestawu wyników. Wywołaj, `Close` Aby zamknąć zwracaną metodę dostępu zestawu wierszy i zestawu wyników, ale nie metodę dostępu do parametru, umożliwiając w ten sposób pobieranie wartości parametrów wyjściowych.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak można nawiązać połączenie `Close` i `ReleaseCommand` kiedy wielokrotnie wykonać to samo polecenie.

[!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]

## <a name="ccommandgetnextresult"></a><a name="getnextresult"></a> CCommand:: GetNextResult

Pobiera następny zestaw wyników, jeśli jest dostępny.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,
   bool bBind = true) throw();
```

#### <a name="parameters"></a>Parametry

*pulRowsAffected*<br/>
[we/out] Wskaźnik do pamięci, w której zwracana jest liczba wierszy, na które ma wpływ polecenie.

*bBind*<br/>
podczas Określa, czy polecenie ma być powiązane automatycznie po wykonaniu. Wartość domyślna to **`true`** , co powoduje, że polecenie ma być powiązane automatycznie. Ustawienie *bBind* **`false`** uniemożliwia automatyczne wiązanie polecenia, aby można było powiązać je ręcznie. (Ręczne powiązanie ma szczególne znaczenie dla użytkowników OLAP).

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli zestaw wyników został wcześniej pobrany, ta funkcja zwolni poprzedni zestaw wyników i rozwiąże kolumny. Jeśli *bBind* jest **`true`** , wiąże nowe kolumny.

Tę funkcję należy wywołać tylko wtedy, gdy określono wiele wyników przez ustawienie `CCommand` parametru szablonu *TMultiple* = `CMultipleResults` .

## <a name="ccommandopen"></a><a name="open"></a> CCommand:: Open

Wykonuje i opcjonalnie wiąże polecenie.

### <a name="syntax"></a>Składnia

```cpp
HRESULT Open(const CSession& session,
   LPCWSTR wszCommand,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(const CSession& session,
   LPCSTR szCommand,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(const CSession& session,
   INT szCommand = NULL,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();
```

#### <a name="parameters"></a>Parametry

*obrad*<br/>
podczas Sesja, w której ma zostać wykonane polecenie.

*wszCommand*<br/>
podczas Polecenie do wykonania, które zostało przesłane jako ciąg Unicode. Może mieć wartość NULL przy użyciu `CAccessor` , w którym przypadku polecenie zostanie pobrane z wartości przesłanej do makra [DEFINE_COMMAND](./macros-and-global-functions-for-ole-db-consumer-templates.md#define_command) . Aby uzyskać szczegółowe informacje, zobacz [Interfejs ICommand:: Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) w *dokumentacji programisty OLE DB* .

*szCommand*<br/>
podczas Analogicznie jak *wszCommand* , z tą różnicą, że ten parametr pobiera ciąg poleceń ANSI. Czwarta postać tej metody może przyjmować wartość NULL. Aby uzyskać szczegółowe informacje, zobacz sekcję "uwagi" w dalszej części tego tematu.

*pPropSet*<br/>
podczas Wskaźnik do tablicy struktur [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) zawierających właściwości i wartości, które mają zostać ustawione. Zobacz [zestawy właściwości i grupy właściwości](/previous-versions/windows/desktop/ms713696(v=vs.85)) w *odniesieniu do OLE DB programisty* w Windows SDK.

*pRowsAffected*<br/>
[we/out] Wskaźnik do pamięci, w której zwracana jest liczba wierszy, na które ma wpływ polecenie. Jeśli * \* pRowsAffected* ma wartość null, nie jest zwracana liczba wierszy. W przeciwnym razie `Open` ustawia * \* pRowsAffected* zgodnie z następującymi warunkami:

|Jeśli użytkownik|Następnie|
|--------|----------|
|`cParamSets`Element `pParams` jest większy niż 1|* \* pRowsAffected* reprezentuje łączną liczbę wierszy, na które mają wpływ wszystkie zestawy parametrów określone w wykonaniu.|
|Liczba objętych wierszy jest niedostępna|* \* pRowsAffected* jest ustawiona na-1.|
|Polecenie nie aktualizuje, nie usuwa ani nie wstawia wierszy|* \* pRowsAffected* jest niezdefiniowany.|

*guidCommand*<br/>
podczas Identyfikator GUID, który określa składnię i ogólne reguły dla dostawcy do użycia podczas analizowania tekstu polecenia. Aby uzyskać szczegółowe informacje, zobacz [ICommandText:: GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) i [ICommandText:: SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) w *dokumentacji programisty OLE DB* .

*bBind*<br/>
podczas Określa, czy polecenie ma być powiązane automatycznie po wykonaniu. Wartość domyślna to **`true`** , co powoduje, że polecenie ma być powiązane automatycznie. Ustawienie *bBind* **`false`** uniemożliwia automatyczne wiązanie polecenia, aby można było powiązać je ręcznie. (Ręczne powiązanie ma szczególne znaczenie dla użytkowników OLAP).

*ulPropSets*<br/>
podczas Liczba struktur [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) przeniesiona w argumencie *pPropSet* .

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Pierwsze trzy formy `Open` podejmowania sesji, tworzenia polecenia i wykonywania polecenia, powiązania wszelkich parametrów w razie potrzeby.

Pierwszy formularz `Open` przyjmuje ciąg polecenia Unicode i nie ma wartości domyślnej.

Druga forma `Open` przyjmuje ciąg polecenia ANSI i nie ma wartości domyślnej (zapewnianej dla zgodności z poprzednimi wersjami z istniejącymi aplikacjami ANSI).

Trzecia forma `Open` dopuszcza, aby ciąg polecenia miał wartość null, z powodu typu **`int`** z wartością domyślną NULL. Jest on przeznaczony do wywoływania `Open(session, NULL);` lub `Open(session);` ponieważ ma wartość null, jest typu **`int`** . Ta wersja wymaga i potwierdza, że **`int`** parametr ma wartość null.

Użyj czwartej formy, `Open` gdy utworzono już polecenie i chcesz wykonać pojedyncze [przygotowanie](#prepare) i wiele wykonań.

> [!NOTE]
> `Open` wywołania `Execute` , które z kolei powodują wywoływanie `GetNextResult` .

## <a name="ccommandcreate"></a><a name="create"></a> CCommand:: Create

Wywołuje [CCommand::](#createcommand) ICommandText, aby utworzyć polecenie dla określonej sesji, a następnie wywołuje [:: SetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) , aby określić tekst polecenia.

### <a name="syntax"></a>Składnia

```cpp
HRESULT CCommandBase::Create(const CSession& session,
   LPCWSTR wszCommand,
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();

HRESULT CCommandBase::Create(const CSession& session,
   LPCSTR szCommand,
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();
```

#### <a name="parameters"></a>Parametry

*obrad*<br/>
podczas Sesja, dla której ma zostać utworzone polecenie.

*wszCommand*<br/>
podczas Wskaźnik do tekstu Unicode ciągu polecenia.

*szCommand*<br/>
podczas Wskaźnik do tekstu ANSI ciągu polecenia.

*guidCommand*<br/>
podczas Identyfikator GUID, który określa składnię i ogólne reguły dla dostawcy do użycia podczas analizowania tekstu polecenia. Aby uzyskać opis dialektów, zobacz [ICommandText:: GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) w *dokumentacji programisty OLE DB*.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Pierwszy formularz `Create` Pobiera ciąg poleceń Unicode. Druga forma `Create` Pobiera ciąg poleceń ANSI (pod kątem zgodności z poprzednimi wersjami z istniejącymi aplikacjami ANSI).

## <a name="ccommandcreatecommand"></a><a name="createcommand"></a> CCommand:: SetCommand

Tworzy nowe polecenie.

### <a name="syntax"></a>Składnia

```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();
```

#### <a name="parameters"></a>Parametry

*obrad*<br/>
podczas `CSession` Obiekt, który ma zostać skojarzony z nowym poleceniem.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy polecenie przy użyciu określonego obiektu sesji.

## <a name="ccommandgetparameterinfo"></a><a name="getparameterinfo"></a> CCommand:: GetParameterInfo

Pobiera listę parametrów poleceń, ich nazw i ich typów.

### <a name="syntax"></a>Składnia

```cpp
HRESULT CCommandBase::GetParameterInfo(DB_UPARAMS* pParams,
   DBPARAMINFO** ppParamInfo,
   OLECHAR** ppNamesBuffer) throw ();
```

#### <a name="parameters"></a>Parametry

Zobacz [ICommandWithParameters:: GetParameterInfo](/previous-versions/windows/desktop/ms714917(v=vs.85)) w *dokumentacji programisty OLE DB*.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="ccommandprepare"></a><a name="prepare"></a> CCommand::P Przygotuj

Weryfikuje i optymalizuje bieżące polecenie.

### <a name="syntax"></a>Składnia

```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();
```

#### <a name="parameters"></a>Parametry

*cExpectedRuns*<br/>
podczas Liczba przypadków, kiedy należy wykonać polecenie.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ta metoda otacza OLE DB Metoda [ICommandPrepare::P Przygotuj](/previous-versions/windows/desktop/ms718370(v=vs.85)).

## <a name="ccommandreleasecommand"></a><a name="releasecommand"></a> CCommand:: ReleaseCommand

Zwalnia metodę dostępu do parametrów, a następnie zwalnia samo polecenie.

### <a name="syntax"></a>Składnia

```cpp
void CCommandBase::ReleaseCommand() throw();
```

### <a name="remarks"></a>Uwagi

`ReleaseCommand` jest używany w połączeniu z `Close` . Zobacz [Zamknij](#close) , aby uzyskać szczegółowe informacje na temat użycia.

## <a name="ccommandsetparameterinfo"></a><a name="setparameterinfo"></a> CCommand:: SetParameterInfo

Określa typ natywny każdego parametru polecenia.

### <a name="syntax"></a>Składnia

```cpp
HRESULT CCommandBase::SetParameterInfo(DB_UPARAMS ulParams,
   const DBORDINAL* pOrdinals,
   const DBPARAMBINDINFO* pParamInfo) throw();
```

#### <a name="parameters"></a>Parametry

Zobacz [ICommandWithParameters:: SetParameterInfo](/previous-versions/windows/desktop/ms725393(v=vs.85)) w *Kompendium OLE DB programisty*.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="ccommandunprepare"></a><a name="unprepare"></a> CCommand:: Prepare

Odrzuca bieżący plan wykonywania polecenia.

### <a name="syntax"></a>Składnia

```cpp
HRESULT CCommandBase::Unprepare() throw();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Ta metoda otacza metodę OLE DB [ICommandPrepare:: Prepare](/previous-versions/windows/desktop/ms719635(v=vs.85)).

## <a name="see-also"></a>Zobacz też

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Dokumentacja szablonów klientów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
