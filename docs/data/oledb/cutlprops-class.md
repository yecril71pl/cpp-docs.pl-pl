---
title: CUtlProps — Klasa
ms.date: 11/04/2016
f1_keywords:
- CUtlProps
- CUtlProps::GetPropValue
- CUtlProps.GetPropValue
- GetPropValue
- CUtlProps::IsValidValue
- CUtlProps.IsValidValue
- IsValidValue
- OnPropertyChanged
- CUtlProps.OnPropertyChanged
- CUtlProps::OnPropertyChanged
- SetPropValue
- ATL::CUtlProps<T>::SetPropValue
- ATL.CUtlProps<T>.SetPropValue
- ATL.CUtlProps.SetPropValue
- CUtlProps::SetPropValue
- CUtlProps<T>::SetPropValue
- CUtlProps.SetPropValue
- CUtlProps<T>.SetPropValue
- ATL::CUtlProps::SetPropValue
helpviewer_keywords:
- CUtlProps class
- GetPropValue method
- IsValidValue method
- OnInterfaceRequested method
- OnPropertyChanged method
- SetPropValue method
ms.assetid: bb525178-765c-4e23-a110-c0fd70c05437
ms.openlocfilehash: 46fa266c5a8328bbcf7cfd1257ce1ff3e38ed2bb
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845669"
---
# <a name="cutlprops-class"></a>CUtlProps — Klasa

Implementuje właściwości dla różnych OLE DB interfejsów właściwości (na przykład,, `IDBProperties` `IDBProperties` i `IRowsetInfo` ).

## <a name="syntax"></a>Składnia

```cpp
template < class T >
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która zawiera `BEGIN_PROPSET_MAP` .

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLDB. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

| Nazwa | Opis |
|-|-|
|[GetPropValue](#getpropvalue)|Pobiera właściwość z zestawu właściwości.|
|[IsValidValue](#isvalidvalue)|Służy do sprawdzania poprawności wartości przed ustawieniem właściwości.|
|[OnInterfaceRequested](#oninterfacerequested)|Obsługuje żądania dla opcjonalnego interfejsu, gdy odbiorca wywołuje metodę w interfejsie tworzenia obiektu.|
|[OnPropertyChanged](#onpropertychanged)|Wywołuje się po ustawieniu właściwości w celu obsługi właściwości łańcucha.|
|[SetPropValue](#setpropvalue)|Ustawia właściwość w zestawie właściwości.|

## <a name="remarks"></a>Uwagi

Większość tej klasy jest szczegółami implementacji.

`CUtlProps` zawiera dwa elementy członkowskie do ustawiania właściwości wewnętrznie: [GetPropValue](../../data/oledb/cutlprops-getpropvalue.md) i [SetPropValue](../../data/oledb/cutlprops-setpropvalue.md).

Aby uzyskać więcej informacji na temat makr używanych na mapie zestawu właściwości, zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) i [END_PROPSET_MAP](../../data/oledb/end-propset-map.md).

## <a name="cutlpropsgetpropvalue"></a><a name="getpropvalue"></a> CUtlProps:: GetPropValue

Pobiera właściwość z zestawu właściwości.

### <a name="syntax"></a>Składnia

```cpp
OUT_OF_LINE HRESULT GetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>Parametry

*pguidPropSet*<br/>
podczas Identyfikator GUID dla PropSet.

*dwPropId*<br/>
podczas Indeks właściwości.

*pvValue*<br/>
określoną Wskaźnik do wariantu, który zawiera nową wartość właściwości.

### <a name="return-value"></a>Wartość zwracana

`Failure` w przypadku awarii i S_OK, jeśli się to powiedzie.

## <a name="cutlpropsisvalidvalue"></a><a name="isvalidvalue"></a> CUtlProps:: IsValidValue

Służy do sprawdzania poprawności wartości przed ustawieniem właściwości.

### <a name="syntax"></a>Składnia

```cpp
virtual HRESULT CUtlPropsBase::IsValidValue(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>Parametry

*iCurSet*<br/>
Indeks do tablicy zestawu właściwości; zero, jeśli istnieje tylko jeden zestaw właściwości.

*pDBProp*<br/>
Identyfikator właściwości i Nowa wartość w strukturze [DBPROP](/previous-versions/windows/desktop/ms717970(v=vs.85)) .

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT. Domyślną wartością zwracaną jest S_OK.

### <a name="remarks"></a>Uwagi

Jeśli masz jakiekolwiek procedury walidacji, które chcesz uruchomić na wartości, która ma zostać użyta do ustawienia właściwości, należy zastąpić tę funkcję. Na przykład można sprawdzić poprawność DBPROP_AUTH_PASSWORD względem tabeli haseł, aby określić prawidłową wartość.

## <a name="cutlpropsoninterfacerequested"></a><a name="oninterfacerequested"></a> CUtlProps:: OnInterfaceRequested

Obsługuje żądania dla opcjonalnego interfejsu, gdy odbiorca wywołuje metodę na jednym z interfejsów tworzenia obiektów.

### <a name="syntax"></a>Składnia

```cpp
virtual HRESULT CUtlPropsBase::OnInterfaceRequested(REFIID riid);
```

#### <a name="parameters"></a>Parametry

*riid*<br/>
podczas Identyfikator IID dla żądanego interfejsu. Aby uzyskać więcej informacji, zobacz opis parametru *riid* `ICommand::Execute` w *dokumentacji programisty OLE DB* (w *zestawie MDAC SDK*).

### <a name="remarks"></a>Uwagi

`OnInterfaceRequested` obsługuje żądania klientów dla opcjonalnego interfejsu, gdy odbiorca wywołuje metodę na jednym z interfejsów tworzenia obiektów (takich jak, `IDBCreateSession` , `IDBCreateCommand` `IOpenRowset` lub `ICommand` ). Ustawia odpowiadającą właściwość OLE DB dla żądanego interfejsu. Na przykład jeśli odbiorca żąda `IID_IRowsetLocate` , `OnInterfaceRequested` ustawia `DBPROP_IRowsetLocate` interfejs. Podczas tworzenia zestawu wierszy należy zachować prawidłowy stan.

Ta metoda jest wywoływana, gdy odbiorca wywołuje `IOpenRowset::OpenRowset` lub `ICommand::Execute` .

Jeśli odbiorca otworzy obiekt i zażąda opcjonalnego interfejsu, dostawca powinien ustawić właściwość skojarzoną z tym interfejsem na VARIANT_TRUE. Aby zezwolić na przetwarzanie specyficzne dla właściwości, `OnInterfaceRequested` jest wywoływana przed `Execute` wywołaniem metody dostawcy. Domyślnie program `OnInterfaceRequested` obsługuje następujące interfejsy:

- `IRowsetLocate`

- `IRowsetChange`

- `IRowsetUpdate`

- `IConnectionPointContainer`

- `IRowsetScroll`

Jeśli chcesz obsłużyć inne interfejsy, Przesłoń tę funkcję w klasie źródła danych, sesji, polecenia lub zestawu wierszy, aby przetwarzać funkcje. Przesłonięcie powinno przekroczyć normalne interfejsy zestawu/pobierania właściwości, aby upewnić się, że właściwości ustawienia również ustawiają wszystkie właściwości łańcucha (zobacz [OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md)).

## <a name="cutlpropsonpropertychanged"></a><a name="onpropertychanged"></a> CUtlProps:: OnPropertyChanged

Wywołuje się po ustawieniu właściwości w celu obsługi właściwości łańcucha.

### <a name="syntax"></a>Składnia

```cpp
virtual HRESULT OnPropertyChanged(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>Parametry

*iCurSet*<br/>
Indeks do tablicy zestawu właściwości; zero, jeśli istnieje tylko jeden zestaw właściwości.

*pDBProp*<br/>
Identyfikator właściwości i Nowa wartość w strukturze [DBPROP](/previous-versions/windows/desktop/ms717970(v=vs.85)) .

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT. Domyślną wartością zwracaną jest S_OK.

### <a name="remarks"></a>Uwagi

Jeśli chcesz obsługiwać właściwości łańcucha, takie jak zakładki lub aktualizacje, których wartości są zależne od wartości innej właściwości, należy zastąpić tę funkcję.

### <a name="example"></a>Przykład

W tej funkcji użytkownik pobiera identyfikator właściwości z `DBPROP*` parametru. Teraz można porównać identyfikator z właściwością do łańcucha. Gdy właściwość zostanie znaleziona, `SetProperties` jest wywoływana z właściwością, która zostanie teraz ustawiona w połączeniu z inną właściwością. W takim przypadku, jeśli jeden pobiera `DBPROP_IRowsetLocate` Właściwość, `DBPROP_LITERALBOOKMARKS` , lub `DBPROP_ORDEREDBOOKMARKS` , może ustawić `DBPROP_BOOKMARKS` Właściwość.

[!code-cpp[NVC_OLEDB_Provider#2](../../data/oledb/codesnippet/cpp/cutlprops-onpropertychanged_1.h)]

## <a name="cutlpropssetpropvalue"></a><a name="setpropvalue"></a> CUtlProps:: SetPropValue

Ustawia właściwość w zestawie właściwości.

### <a name="syntax"></a>Składnia

```cpp
HRESULT SetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>Parametry

*pguidPropSet*<br/>
podczas Identyfikator GUID dla PropSet.

*dwPropId*<br/>
podczas Indeks właściwości.

*pvValue*<br/>
podczas Wskaźnik do wariantu, który zawiera nową wartość właściwości.

### <a name="return-value"></a>Wartość zwracana

`Failure` w przypadku awarii i S_OK, jeśli się to powiedzie.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
