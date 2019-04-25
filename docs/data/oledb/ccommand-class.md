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
ms.openlocfilehash: 406a78ff1958d565fcc74781f6a63d4784f48bfc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62176099"
---
# <a name="ccommand-class"></a>Klasa CCommand

Udostępnia metody do ustawiania i wykonywania polecenia.

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
Typ klasy metody dostępu (takich jak `CDynamicParameterAccessor`, `CDynamicStringAccessor`, lub `CEnumeratorAccessor`) mają polecenie, aby użyć. Wartość domyślna to `CNoAccessor`, która określa, że klasa nie obsługuje parametrów lub kolumny wyjściowe.

*TRowset*<br/>
Typ klasy zestawu wierszy (takie jak `CArrayRowset` lub `CNoRowset`) mają polecenie, aby użyć. Wartość domyślna to `CRowset`.

*TMultiple*<br/>
Aby użyć polecenia OLE DB, która może zwrócić wiele wyników, należy określić [cmultipleresults —](../../data/oledb/cmultipleresults-class.md). W przeciwnym razie użyj [cnomultipleresults —](../../data/oledb/cnomultipleresults-class.md). Aby uzyskać więcej informacji, zobacz [IMultipleResults](/previous-versions/windows/desktop/ms721289(v=vs.85)).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli.h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Zamknij](#close)|Zamyka bieżące polecenie.|
|[GetNextResult](#getnextresult)|Pobiera następny wynik, gdy zestawów za pomocą wielu wyników.|
|[Otwórz](#open)|Wykonuje i opcjonalnie powiązanie polecenia.|

### <a name="inherited-methods"></a>Metody dziedziczone

|||
|-|-|
|[Tworzenie](#create)|Tworzy nowe polecenia dla określonej sesji, a następnie ustawia tekst polecenia.|
|[CreateCommand](#createcommand)|Tworzy nowe polecenie.|
|[GetParameterInfo](#getparameterinfo)|Pobiera listę parametrów poleceń, ich nazwy i ich typy.|
|[Przygotowywanie](#prepare)|Weryfikuje i optymalizuje bieżącego polecenia.|
|[ReleaseCommand](#releasecommand)|Zwalnia parametr metody dostępu, jeśli to konieczne, a następnie zwalnia polecenia.|
|[SetParameterInfo](#setparameterinfo)|Określa typ macierzysty każdego parametru polecenia.|
|[Unprepare](#unprepare)|Odrzuca bieżący plan wykonania polecenia.|

## <a name="remarks"></a>Uwagi

Klasa jest używana, gdy trzeba wykonywać operacje oparte o parametry lub wykonać polecenie. Jeśli potrzebujesz tylko otworzyć prosty zestaw wierszy, użyj [CTable](../../data/oledb/ctable-class.md) zamiast tego.

Akcesora, którego używasz, określa sposób wiązania parametrów i danych.

Należy pamiętać, że nie możesz użyć procedur składowanych z dostawcy OLE DB firmy Jet ponieważ ten dostawca nie obsługuje procedury składowane (tylko stałe są dozwolone w ciągach zapytań).

## <a name="close"></a> CCommand::Close

Zwalnia akcesor zestaw wierszy skojarzonych z poleceniem.

### <a name="syntax"></a>Składnia

```cpp
void Close();
```

### <a name="remarks"></a>Uwagi

Polecenie używa zestawu wierszy, metody dostępu set wynik, (opcjonalnie) parametr metody dostępu i (w przeciwieństwie do tabel, które nie obsługują parametrów i nie ma potrzeby akcesor parametru).

Po wykonaniu polecenia, należy wywołać oba `Close` i [releasecommand —](../../data/oledb/ccommand-releasecommand.md) po poleceniu.

Wykonać to samo polecenie wielokrotnie, powinien wersji każdej metody dostępu set wynik, wywołując `Close` przed wywołaniem `Execute`. Na końcu serii powinien zwolnić akcesor parametru, wywołując `ReleaseCommand`. Innym typowym scenariuszem jest wywoływanie procedury przechowywanej, która ma następujące parametry danych wyjściowych. W wielu dostawców (na przykład dostawca OLE DB dla programu SQL Server) wartości parametrów wyjściowych nie są dostępne do czasu zamknięcia dostępu set z wyników. Wywołaj `Close` zamknąć zwróconych wierszy i metody dostępu set wynik, ale nie akcesor parametru, co pozwala na pobieranie wartości parametrów wyjściowych.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak można wywołać `Close` i `ReleaseCommand` podczas wykonywania tego samego polecenia wielokrotnie.

[!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]

## <a name="getnextresult"></a> CCommand::GetNextResult

Pobiera następny wynik, jeśli jest on dostępny.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,
   bool bBind = true) throw();
```

#### <a name="parameters"></a>Parametry

*pulRowsAffected*<br/>
[/ Ściemnianie] Wskaźnik do pamięci, gdy liczba wierszy, których to dotyczy, za pomocą polecenia jest zwracany.

*bBind*<br/>
[in] Określa, czy należy powiązać polecenie automatycznie po wykonywana. Wartość domyślna to **true**, co powoduje, że polecenie, aby powiązać automatycznie. Ustawienie *bBind* do **false** uniemożliwia automatyczne powiązania polecenie tak, aby można powiązać ręcznie. (Ręczne powiązanie to szczególne znaczenie w odniesieniu do użytkowników OLAP).

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli zestaw wyników zostaną pobrane wcześniej, ta funkcja zwalnia poprzedni zestaw wyników i Rozpina kolumn. Jeśli *bBind* jest **true**, powiąże nowych kolumn.

Tę funkcję, należy wywołać tylko wtedy, gdy określono wiele wyników, ustawiając `CCommand` parametru szablonu *TMultiple*=`CMultipleResults`.

## <a name="open"></a> CCommand::Open

Wykonuje i opcjonalnie powiązanie polecenia.

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

*Sesji*<br/>
[in] Sesji, w którym można wykonać polecenia.

*wszCommand*<br/>
[in] Polecenie do wykonania, jest przekazywany jako ciąg Unicode. Może mieć wartości NULL, korzystając z `CAccessor`, w którym to przypadku polecenia zostanie pobrana wartość przekazana do [DEFINE_COMMAND](../../data/oledb/define-command.md) makra. Zobacz [ICommand::Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) w *OLE DB Podręcznik programisty* Aby uzyskać szczegółowe informacje.

*szCommand*<br/>
[in] Taki sam jak *wszCommand* z tą różnicą, że ten parametr przyjmuje ciąg polecenia ANSI. Czwarty formularz tej metody może potrwać wartość NULL. W dalszej części tego tematu, aby uzyskać szczegółowe informacje, zobacz "Uwagi".

*pPropSet*<br/>
[in] Wskaźnik do tablicy [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) struktury zawierający właściwości i wartości do ustawienia. Zobacz [zestawy właściwości i właściwości grupy](/previous-versions/windows/desktop/ms713696(v=vs.85)) w *OLE DB Podręcznik programisty* w Windows SDK.

*pRowsAffected*<br/>
[/ Ściemnianie] Wskaźnik do pamięci, gdy liczba wierszy, których to dotyczy, za pomocą polecenia jest zwracany. Jeśli  *\*pRowsAffected* ma wartość NULL, jest zwracana żadna liczba wierszy. W przeciwnym razie `Open` ustawia  *\*pRowsAffected* zgodnie z następujących warunków:

|IF|Następnie|
|--------|----------|
|`cParamSets` Elementu `pParams` jest większa niż 1|*\*pRowsAffected* — łączną liczbę wierszy dotyczy wszystkich zestawów parametrów, określony podczas wykonywania.|
|Liczba wierszy, których to dotyczy, nie jest dostępna|*\*pRowsAffected* jest ustawiona na wartość -1.|
|Polecenie nie powoduje aktualizacji, usunięcia lub wstawianie wierszy|*\*pRowsAffected* jest niezdefiniowana.|

*guidCommand*<br/>
[in] Identyfikator GUID, który określa składnię i ogólne zasady dostawcę, który ma być używany podczas analizowania tekstu polecenia. Zobacz [ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) i [ICommandText::SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) w *OLE DB Podręcznik programisty* Aby uzyskać szczegółowe informacje.

*bBind*<br/>
[in] Określa, czy należy powiązać polecenie automatycznie po wykonywana. Wartość domyślna to **true**, co powoduje, że polecenie, aby powiązać automatycznie. Ustawienie *bBind* do **false** uniemożliwia automatyczne powiązania polecenie tak, aby można powiązać ręcznie. (Ręczne powiązanie to szczególne znaczenie w odniesieniu do użytkowników OLAP).

*ulPropSets*<br/>
[in] Liczba [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) struktury przekazany *pPropSet* argumentu.

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT.

### <a name="remarks"></a>Uwagi

Pierwsze trzy rodzaje `Open` wykonać sesję, Utwórz polecenie i wykonaj polecenie powiązania parametrów, zgodnie z potrzebami.

Pierwszy formularz `Open` przyjmuje ciąg polecenia Unicode i nie ma wartości domyślnej.

Drugiej formy `Open` przyjmuje ciąg polecenia ANSI i ma wartości domyślnej (pod warunkiem zgodności z poprzednimi wersjami z istniejącymi aplikacjami ANSI).

Trzecia formą `Open` zezwala na ciąg polecenia mieć wartości NULL, ze względu na typ **int** z wartością domyślną wartością null. Jest ona udostępniana do wywoływania `Open(session, NULL);` lub `Open(session);` ponieważ o wartości NULL jest kolumną typu **int**. Ta wersja wymaga i potwierdza, że **int** parametrów mieć wartości NULL.

Użyć formy czwarty `Open` kiedy utworzono już polecenia i chcesz wykonać jeden [przygotowanie](../../data/oledb/ccommand-prepare.md) i wiele wykonań.

> [!NOTE]
>  `Open` wywołania `Execute`, który z kolei wywołuje `GetNextResult`.

## <a name="create"></a> CCommand::Create

Wywołania [CCommand::CreateCommand](../../data/oledb/ccommand-createcommand.md) można utworzyć polecenia dla określonej sesji, następnie wywołuje [ICommandText::SetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) do określenia tekstu polecenia.

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

*Sesji*<br/>
[in] Sesję, na którym chcesz utworzyć polecenie.

*wszCommand*<br/>
[in] Wskaźnik do tekst w formacie Unicode ciąg polecenia.

*szCommand*<br/>
[in] Wskaźnik do tekst ANSI ciągu polecenia.

*guidCommand*<br/>
[in] Identyfikator GUID, który określa składnię i ogólne zasady dostawcę, który ma być używany podczas analizowania tekstu polecenia. Aby uzyskać opis dialekty, zobacz [ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) w *OLE DB Podręcznik programisty*.

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT.

### <a name="remarks"></a>Uwagi

Pierwszy formularz `Create` polecenia ciąg znaków Unicode. Drugiej formy `Create` przyjmuje ciąg polecenia ANSI (pod warunkiem zgodności z poprzednimi wersjami z istniejącymi aplikacjami ANSI).

## <a name="createcommand"></a> CCommand::CreateCommand

Tworzy nowe polecenie.

### <a name="syntax"></a>Składnia

```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();
```

#### <a name="parameters"></a>Parametry

*Sesji*<br/>
[in] Element `CSession` obiektu do skojarzenia z nowego polecenia.

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy polecenie za pomocą obiektu określonej sesji.

## <a name="getparameterinfo"></a> CCommand::GetParameterInfo

Pobiera listę parametrów poleceń, ich nazwy i ich typy.

### <a name="syntax"></a>Składnia

```cpp
HRESULT CCommandBase::GetParameterInfo(DB_UPARAMS* pParams,
   DBPARAMINFO** ppParamInfo,
   OLECHAR** ppNamesBuffer) throw ();
```

#### <a name="parameters"></a>Parametry

Zobacz [ICommandWithParameters::GetParameterInfo](/previous-versions/windows/desktop/ms714917(v=vs.85)) w *OLE DB Podręcznik programisty*.

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT.

## <a name="prepare"></a> CCommand::Prepare

Weryfikuje i optymalizuje bieżącego polecenia.

### <a name="syntax"></a>Składnia

```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();
```

#### <a name="parameters"></a>Parametry

*cExpectedRuns*<br/>
[in] Liczba przypadków, o których oczekujesz, że można wykonać polecenia.

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT.

### <a name="remarks"></a>Uwagi

Ta metoda opakowuje metodę OLE DB [ICommandPrepare::Prepare](/previous-versions/windows/desktop/ms718370(v=vs.85)).

## <a name="releasecommand"></a> CCommand::ReleaseCommand

Zwalnia akcesor parametru, a następnie zwalnia samo polecenie.

### <a name="syntax"></a>Składnia

```cpp
void CCommandBase::ReleaseCommand() throw();
```

### <a name="remarks"></a>Uwagi

`ReleaseCommand` jest używana w połączeniu z `Close`. Zobacz [Zamknij](../../data/oledb/ccommand-close.md) szczegóły użycia.

## <a name="setparameterinfo"></a> CCommand::SetParameterInfo

Określa typ macierzysty każdego parametru polecenia.

### <a name="syntax"></a>Składnia

```cpp
HRESULT CCommandBase::SetParameterInfo(DB_UPARAMS ulParams,
   const DBORDINAL* pOrdinals,
   const DBPARAMBINDINFO* pParamInfo) throw();
```

#### <a name="parameters"></a>Parametry

Zobacz [ICommandWithParameters::SetParameterInfo](/previous-versions/windows/desktop/ms725393(v=vs.85)) w *OLE DB Podręcznik programisty*.

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT.

## <a name="unprepare"></a> CCommand::Unprepare

Odrzuca bieżący plan wykonania polecenia.

### <a name="syntax"></a>Składnia

```cpp
HRESULT CCommandBase::Unprepare() throw();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT.

### <a name="remarks"></a>Uwagi

Ta metoda opakowuje metodę OLE DB [ICommandPrepare::Unprepare](/previous-versions/windows/desktop/ms719635(v=vs.85)).

## <a name="see-also"></a>Zobacz także

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)