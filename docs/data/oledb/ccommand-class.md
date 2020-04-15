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
ms.openlocfilehash: 52c7e2ce5acdd2df33e2a6422535a337f0a43aec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368629"
---
# <a name="ccommand-class"></a>Klasa CCommand

Zawiera metody ustawiania i wykonywania polecenia.

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

*TAccessor ( TAccessor )*<br/>
Typ klasy akcesora `CDynamicParameterAccessor` `CDynamicStringAccessor`(na `CEnumeratorAccessor`przykład , lub ), który ma być używany. Wartość domyślna to `CNoAccessor`, która określa, że klasa nie obsługuje parametrów ani kolumn wyjściowych.

*Trowset ( TRowset )*<br/>
Typ klasy zestawu wierszy `CArrayRowset` (na przykład lub), `CNoRowset`której ma być używane polecenie. Wartość domyślna to `CRowset`.

*TMultiple (właśc.*<br/>
Aby użyć polecenia OLE DB, które może zwracać wiele wyników, należy określić [CMultipleResults](../../data/oledb/cmultipleresults-class.md). W przeciwnym razie należy użyć [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md). Aby uzyskać szczegółowe informacje, zobacz [IMultipleResults](/previous-versions/windows/desktop/ms721289(v=vs.85)).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli.h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Zamknij](#close)|Zamyka bieżące polecenie.|
|[GetNextResult ( GetNextResult )](#getnextresult)|Pobiera następny wynik podczas korzystania z wielu zestawów wyników.|
|[Otwórz](#open)|Wykonuje i opcjonalnie wiąże polecenie.|

### <a name="inherited-methods"></a>Metody dziedziczone

|||
|-|-|
|[Utwórz](#create)|Tworzy nowe polecenie dla określonej sesji, a następnie ustawia tekst polecenia.|
|[Utwórzkommanię](#createcommand)|Tworzy nowe polecenie.|
|[Getparameterinfo](#getparameterinfo)|Pobiera listę parametrów polecenia, ich nazwy i ich typy.|
|[Przygotowanie](#prepare)|Sprawdza poprawność i optymalizuje bieżące polecenie.|
|[ReleaseCommand](#releasecommand)|W razie potrzeby zwalnia akcesor parametrów, a następnie zwalnia polecenie.|
|[ZestawParameterInfo](#setparameterinfo)|Określa typ macierzysty każdego parametru polecenia.|
|[Nieprzygotowany](#unprepare)|Odrzuca bieżący plan wykonania polecenia.|

## <a name="remarks"></a>Uwagi

Tej klasy należy użyć, gdy trzeba wykonać operację opartą na parametrach lub wykonać polecenie. Jeśli wystarczy otworzyć prosty zestaw wierszy, użyj [CTable](../../data/oledb/ctable-class.md) zamiast tego.

Klasy akcesor, którego używasz określa metodę powiązania parametrów i danych.

Należy zauważyć, że nie można używać procedur przechowywanych z dostawcą ole bazy danych dla jet, ponieważ ten dostawca nie obsługuje procedur przechowywanych (tylko stałe są dozwolone w ciągach zapytań).

## <a name="ccommandclose"></a><a name="close"></a>CCommand::Zamknij

Zwalnia zestaw wierszy akcesora skojarzony z poleceniem.

### <a name="syntax"></a>Składnia

```cpp
void Close();
```

### <a name="remarks"></a>Uwagi

Polecenie używa zestawu wierszy, akcesora zestawu wyników i (opcjonalnie) akcesora parametrów (w przeciwieństwie do tabel, które nie obsługują parametrów i nie potrzebują akcesora parametrów).

Podczas wykonywania polecenia, należy wywołać zarówno `Close` i [ReleaseCommand](../../data/oledb/ccommand-releasecommand.md) po poleceniu.

Jeśli chcesz wykonać to samo polecenie wielokrotnie, należy zwolnić każdy `Close` akcesor zestawu wyników, wywołując przed wywołaniem `Execute`. Na końcu serii należy zwolnić akcesor `ReleaseCommand`parametrów, wywołując program . Innym typowym scenariuszem jest wywołanie procedury składowanej, która ma parametry wyjściowe. W przypadku wielu dostawców (takich jak dostawca ole db dla programu SQL Server) wartości parametrów wyjściowych nie będą dostępne, dopóki nie zamkniesz akcesora zestawu wyników. Wywołanie, `Close` aby zamknąć zwracany zestaw wierszy i akcesor zestawu wyników, ale nie akcesor parametrów, co pozwala na pobieranie wartości parametrów wyjściowych.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, `Close` jak `ReleaseCommand` można wywołać i podczas wykonywania tego samego polecenia wielokrotnie.

[!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]

## <a name="ccommandgetnextresult"></a><a name="getnextresult"></a>CCommand::GetNextResult

Pobiera następny zestaw wyników, jeśli jest dostępny.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,
   bool bBind = true) throw();
```

#### <a name="parameters"></a>Parametry

*pulRowsAfected (Wyważony)*<br/>
[w/wyjęcie] Wskaźnik do pamięci, w którym zwracana jest liczba wierszy, których dotyczy polecenie.

*bBind (bBind)*<br/>
[w] Określa, czy polecenie ma być powiązane automatycznie po wykonaniu. Wartość domyślna to **true**, co powoduje, że polecenie jest powiązane automatycznie. Ustawienie *bBind* na **false** zapobiega automatycznemu wiązaniu polecenia, dzięki czemu można powiązać ręcznie. (Ręczne wiązanie jest szczególnie interesujące dla użytkowników OLAP.)

### <a name="return-value"></a>Wartość zwracana

Standardowy HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli zestaw wyników został wcześniej pobrany, ta funkcja zwalnia poprzedni zestaw wyników i odłącza kolumny. Jeśli *bBind* jest **true**, wiąże nowe kolumny.

Tę funkcję należy wywołać tylko wtedy, gdy `CCommand` określono wiele wyników, ustawiając parametr szablonu *TMultiple*=`CMultipleResults`.

## <a name="ccommandopen"></a><a name="open"></a>CCommand::Otwórz

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

*Sesji*<br/>
[w] Sesja, w której ma być wykonywane polecenie.

*wszCommand*<br/>
[w] Polecenie do wykonania, przekazywane jako ciąg Unicode. Może być null `CAccessor`podczas korzystania , w którym to przypadku polecenie zostanie pobrane z wartości przekazanej do [makra DEFINE_COMMAND.](../../data/oledb/define-command.md) Zobacz [ICommand::Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) w *ole DB programista reference, aby* uzyskać szczegółowe informacje.

*szCommand ( szCommand )*<br/>
[w] Tak samo jak *wszCommand* z tą różnicą, że ten parametr przyjmuje ciąg polecenia ANSI. Czwarta forma tej metody może przybrać wartość NULL. Zobacz "Uwagi" w dalszej części tego tematu, aby uzyskać szczegółowe informacje.

*pPropSet (Zestaw pPropSet)*<br/>
[w] Wskaźnik do tablicy [struktur DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) zawierający właściwości i wartości, które mają zostać ustawione. Zobacz [Zestawy właściwości i grupy właściwości](/previous-versions/windows/desktop/ms713696(v=vs.85)) w *odwołaniu programisty OLE DB* w zestawie Windows SDK.

*pRowsAfected (Wyważony w posiedzie)*<br/>
[w/wyjęcie] Wskaźnik do pamięci, w którym zwracana jest liczba wierszy, których dotyczy polecenie. Jeśli * \*pRowsAffected* ma wartość NULL, nie jest zwracana żadna liczba wierszy. W `Open` przeciwnym razie ustawia * \*pRowsAffected* zgodnie z następującymi warunkami:

|Jeśli użytkownik|Następnie|
|--------|----------|
|Element `cParamSets` `pParams` jest większy niż 1|pRowsAffected reprezentuje całkowitą liczbę wierszy, których dotyczą wszystkie zestawy parametrów określone w wykonaniu. * \**|
|Liczba wierszy, których dotyczy problem, nie jest dostępna|pRowsAffected jest ustawiona na -1. * \**|
|Polecenie nie aktualizuje, nie usuwa ani nie wstawia wierszy|pRowsAffected jest niezdefiniowany. * \**|

*guidCommand ( guidCommand )*<br/>
[w] Identyfikator GUID określający składnię i ogólne reguły używane przez dostawcę do analizowania tekstu polecenia. Zobacz [ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) i [ICommandText::SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) w *ole DB Programista reference, aby* uzyskać szczegółowe informacje.

*bBind (bBind)*<br/>
[w] Określa, czy polecenie ma być powiązane automatycznie po wykonaniu. Wartość domyślna to **true**, co powoduje, że polecenie jest powiązane automatycznie. Ustawienie *bBind* na **false** zapobiega automatycznemu wiązaniu polecenia, dzięki czemu można powiązać ręcznie. (Ręczne wiązanie jest szczególnie interesujące dla użytkowników OLAP.)

*zestawy ulPropSets*<br/>
[w] Liczba struktur [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) przekazanych w *pPropSet* argumentu.

### <a name="return-value"></a>Wartość zwracana

Standardowy HRESULT.

### <a name="remarks"></a>Uwagi

Pierwsze trzy formy `Open` podjęcia sesji, utworzyć polecenie i wykonać polecenie, powiązanie wszelkich parametrów w razie potrzeby.

Pierwsza forma `Open` przyjmuje ciąg polecenia Unicode i nie ma wartości domyślnej.

Druga forma `Open` przyjmuje ciąg polecenia ANSI i nie ma wartości domyślnej (pod warunkiem, że zgodność z istniejącymi aplikacjami ANSI jest wsteczna).

Trzecia forma `Open` umożliwia ciąg polecenia do null, ze względu na typ **int** z domyślną wartością NULL. Jest on przewidziany do wywoływania `Open(session, NULL);` lub `Open(session);` ponieważ NULL jest typu **int**. Ta wersja wymaga i potwierdza, że parametr **int** ma wartość NULL.

Użyj czwartej `Open` formy, gdy już utworzono polecenie i chcesz wykonać jeden [Prepare](../../data/oledb/ccommand-prepare.md) i wiele wykonań.

> [!NOTE]
> `Open`połączeń, `Execute`co z `GetNextResult`kolei wywołuje .

## <a name="ccommandcreate"></a><a name="create"></a>CCommand::Utwórz

Wywołuje [CCommand::CreateCommand,](../../data/oledb/ccommand-createcommand.md) aby utworzyć polecenie dla określonej sesji, a następnie wywołuje [ICommandText::SetCommandText,](/previous-versions/windows/desktop/ms709825(v=vs.85)) aby określić tekst polecenia.

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
[w] Sesja, w której ma być utworzone polecenie.

*wszCommand*<br/>
[w] Wskaźnik do tekstu Unicode ciągu polecenia.

*szCommand ( szCommand )*<br/>
[w] Wskaźnik do tekstu ANSI ciągu polecenia.

*guidCommand ( guidCommand )*<br/>
[w] Identyfikator GUID określający składnię i ogólne reguły używane przez dostawcę do analizowania tekstu polecenia. Aby uzyskać opis dialektów, zobacz [ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) w *odwołaniu programisty OLE DB*.

### <a name="return-value"></a>Wartość zwracana

Standardowy HRESULT.

### <a name="remarks"></a>Uwagi

Pierwsza forma `Create` przyjmuje ciąg polecenia Unicode. Druga forma `Create` przyjmuje ciąg poleceń ANSI (pod warunkiem, że zgodność z istniejącymi aplikacjami ANSI jest wsteczna).

## <a name="ccommandcreatecommand"></a><a name="createcommand"></a>CCommand::CreateCommand

Tworzy nowe polecenie.

### <a name="syntax"></a>Składnia

```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();
```

#### <a name="parameters"></a>Parametry

*Sesji*<br/>
[w] Obiekt, `CSession` który ma być skojarzony z nowym poleceniem.

### <a name="return-value"></a>Wartość zwracana

Standardowy HRESULT.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy polecenie przy użyciu określonego obiektu sesji.

## <a name="ccommandgetparameterinfo"></a><a name="getparameterinfo"></a>CCommand::GetParameterInfo

Pobiera listę parametrów polecenia, ich nazwy i ich typy.

### <a name="syntax"></a>Składnia

```cpp
HRESULT CCommandBase::GetParameterInfo(DB_UPARAMS* pParams,
   DBPARAMINFO** ppParamInfo,
   OLECHAR** ppNamesBuffer) throw ();
```

#### <a name="parameters"></a>Parametry

Zobacz [ICommandWithParameters::GetParameterInfo](/previous-versions/windows/desktop/ms714917(v=vs.85)) w *odwołaniu programisty OLE DB*.

### <a name="return-value"></a>Wartość zwracana

Standardowy HRESULT.

## <a name="ccommandprepare"></a><a name="prepare"></a>CCommand::Prepare

Sprawdza poprawność i optymalizuje bieżące polecenie.

### <a name="syntax"></a>Składnia

```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();
```

#### <a name="parameters"></a>Parametry

*cWytaniaRuns*<br/>
[w] Liczba oczekiwanych razy, aby wykonać polecenie.

### <a name="return-value"></a>Wartość zwracana

Standardowy HRESULT.

### <a name="remarks"></a>Uwagi

Ta metoda zawija ole db metoda [ICommandPrepare::Prepare](/previous-versions/windows/desktop/ms718370(v=vs.85)).

## <a name="ccommandreleasecommand"></a><a name="releasecommand"></a>CCommand::ReleaseCommand

Zwalnia akcesor parametrów, a następnie zwalnia samo polecenie.

### <a name="syntax"></a>Składnia

```cpp
void CCommandBase::ReleaseCommand() throw();
```

### <a name="remarks"></a>Uwagi

`ReleaseCommand`jest używany w `Close`połączeniu z . Zobacz [Zamknij](../../data/oledb/ccommand-close.md) szczegóły użycia.

## <a name="ccommandsetparameterinfo"></a><a name="setparameterinfo"></a>CCommand::SetParameterInfo

Określa typ macierzysty każdego parametru polecenia.

### <a name="syntax"></a>Składnia

```cpp
HRESULT CCommandBase::SetParameterInfo(DB_UPARAMS ulParams,
   const DBORDINAL* pOrdinals,
   const DBPARAMBINDINFO* pParamInfo) throw();
```

#### <a name="parameters"></a>Parametry

Zobacz [ICommandWithParameters::SetParameterInfo](/previous-versions/windows/desktop/ms725393(v=vs.85)) w *odwołaniu programisty OLE DB*.

### <a name="return-value"></a>Wartość zwracana

Standardowy HRESULT.

## <a name="ccommandunprepare"></a><a name="unprepare"></a>CCommand::Nieprzygotować

Odrzuca bieżący plan wykonania polecenia.

### <a name="syntax"></a>Składnia

```cpp
HRESULT CCommandBase::Unprepare() throw();
```

### <a name="return-value"></a>Wartość zwracana

Standardowy HRESULT.

### <a name="remarks"></a>Uwagi

Ta metoda zawija ole db metoda [ICommandPrepare::Unprepare](/previous-versions/windows/desktop/ms719635(v=vs.85)).

## <a name="see-also"></a>Zobacz też

[Szablony dla konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Dokumentacja szablonów dla konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
