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
- CUtlProps
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
ms.openlocfilehash: 5accc7e5901e8082f5483bca5439462a3c4ffd24
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525765"
---
# <a name="cutlprops-class"></a>CUtlProps — Klasa

Implementuje właściwości dla różnych interfejsów właściwość OLE DB (na przykład `IDBProperties`, `IDBProperties`, i `IRowsetInfo`).

## <a name="syntax"></a>Składnia

```cpp
template < class T >
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase
```

### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która zawiera `BEGIN_PROPSET_MAP`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldb.h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[GetPropValue](#getpropvalue)|Pobiera właściwości z zestawu właściwości.|
|[Isvalidvalue —](#isvalidvalue)|Używany do sprawdzania poprawności wartości przed ustawieniem właściwości.|
|[OnInterfaceRequested](#oninterfacerequested)|Obsługuje żądania na potrzeby opcjonalny interfejs, gdy użytkownik wywołuje metodę dla interfejsu tworzenia obiektu.|
|[OnPropertyChanged](#onpropertychanged)|Wywołuje się po ustawieniu właściwości w celu obsługi łańcuchowych właściwości.|
|[Setpropvalue —](#setpropvalue)|Ustawia właściwość w zbiorze właściwości.|

## <a name="remarks"></a>Uwagi

W większości tej klasy jest szczegółowo opisuje implementacja.

`CUtlProps` zawiera dwa elementy członkowskie do ustawiania właściwości wewnętrznie: [getpropvalue —](../../data/oledb/cutlprops-getpropvalue.md) i [setpropvalue —](../../data/oledb/cutlprops-setpropvalue.md).

Aby uzyskać więcej informacji na temat makra używane w mapie zestaw właściwości, zobacz [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) i [END_PROPSET_MAP](../../data/oledb/end-propset-map.md).

## <a name="getpropvalue"></a> CUtlProps::GetPropValue

Pobiera właściwości z zestawu właściwości.

### <a name="syntax"></a>Składnia

```cpp
OUT_OF_LINE HRESULT GetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>Parametry

*pguidPropSet*<br/>
[in] Identyfikator GUID zestawu właściwości.

*dwPropId*<br/>
[in] Indeks właściwości.

*pvValue*<br/>
[out] Wskaźnik do typu variant, który zawiera nową wartość właściwości.

### <a name="return-value"></a>Wartość zwracana

`Failure` błąd i S_OK w przypadku powodzenia.

## <a name="isvalidvalue"></a> CUtlProps::IsValidValue

Używany do sprawdzania poprawności wartości przed ustawieniem właściwości.

### <a name="syntax"></a>Składnia

```cpp
virtual HRESULT CUtlPropsBase::IsValidValue(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>Parametry

*iCurSet*<br/>
Indeks do tablicy ustawioną właściwość; zero, jeśli istnieje tylko jedna właściwość.

*pDBProp*<br/>
Identyfikator właściwości i nową wartość w [DBPROP](/previous-versions/windows/desktop/ms717970) struktury.

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT. Zwracana wartość domyślna to S_OK.

### <a name="remarks"></a>Uwagi

W przypadku dowolnej procedury weryfikacji, który ma zostać uruchomiony na podstawie wartości, które są używane do ustawiania właściwości powinny przesłaniać tę funkcję. Na przykład można sprawdzić poprawności DBPROP_AUTH_PASSWORD na tabeli hasło, aby określić prawidłową wartość.

## <a name="oninterfacerequested"></a> CUtlProps::OnInterfaceRequested

Obsługuje żądania na potrzeby opcjonalny interfejs, gdy użytkownik wywołuje metodę dla jednego obiektu Tworzenie interfejsów.

### <a name="syntax"></a>Składnia

```cpp
virtual HRESULT CUtlPropsBase::OnInterfaceRequested(REFIID riid);
```

#### <a name="parameters"></a>Parametry

*Parametr riid*<br/>
[in] IID dla żądanego interfejsu. Aby uzyskać więcej informacji, zobacz opis *riid* parametru `ICommand::Execute` w *OLE DB Podręcznik programisty* (w *MDAC SDK*).

### <a name="remarks"></a>Uwagi

`OnInterfaceRequested` obsługuje żądania klientów dotyczące opcjonalny interfejs, gdy użytkownik wywołuje metodę dla jednego obiektu Tworzenie interfejsów (takie jak `IDBCreateSession`, `IDBCreateCommand`, `IOpenRowset`, lub `ICommand`). Ustawia odpowiednie właściwości OLE DB dla żądanego interfejsu. Na przykład, jeśli użytkownik zażąda `IID_IRowsetLocate`, `OnInterfaceRequested` ustawia `DBPROP_IRowsetLocate` interfejsu. Ten sposób utrzymuje prawidłowy stan podczas tworzenia zestawu wierszy.

Ta metoda jest wywoływana, gdy użytkownik wywołuje `IOpenRowset::OpenRowset` lub `ICommand::Execute`.

Jeśli użytkownik otwiera obiekt, żąda opcjonalny interfejs dostawcy należy ustawić właściwość skojarzoną z tym interfejsem VARIANT_TRUE. Aby zezwolić na przetwarzanie specyficzne dla właściwości `OnInterfaceRequested` jest wywoływana przed dostawcy `Execute` metoda jest wywoływana. Domyślnie `OnInterfaceRequested` obsługuje następujące interfejsy:

- `IRowsetLocate`

- `IRowsetChange`

- `IRowsetUpdate`

- `IConnectionPointContainer`

- `IRowsetScroll`

Jeśli chcesz obsłużyć inne interfejsy, należy przesłonić tę funkcję, w klasie źródła, sesji, polecenie lub zestawu wierszy danych dla funkcji procesu. Przesłonięcia powinny przechodzić przez interfejsy właściwości normalne Ustawianie/pobieranie, aby upewnić się, że ustawienie właściwości ustawia również wszelkie łańcuchowych właściwości (zobacz [onpropertychanged —](../../data/oledb/cutlprops-onpropertychanged.md)).

## <a name="onpropertychanged"></a> CUtlProps::OnPropertyChanged

Wywołuje się po ustawieniu właściwości w celu obsługi łańcuchowych właściwości.

### <a name="syntax"></a>Składnia

```cpp
virtual HRESULT OnPropertyChanged(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>Parametry

*iCurSet*<br/>
Indeks do tablicy ustawioną właściwość; zero, jeśli istnieje tylko jedna właściwość.

*pDBProp*<br/>
Identyfikator właściwości i nową wartość w [DBPROP](/previous-versions/windows/desktop/ms717970) struktury.

### <a name="return-value"></a>Wartość zwracana

Standardowa HRESULT. Zwracana wartość domyślna to S_OK.

### <a name="remarks"></a>Uwagi

Jeśli chcesz obsługiwać właściwości łańcuchowych, takich jak zakładek lub aktualizacji, których wartości są zależne od wartości innej właściwości, należy przesłonić tę funkcję.

### <a name="example"></a>Przykład

W tej funkcji, użytkownik uzyskuje identyfikator właściwości z `DBPROP*` parametru. Teraz jest to możliwe do porównania Identyfikatora względem właściwość, która ma łańcuch. W przypadku odnalezienia właściwość `SetProperties` jest wywoływana z właściwość, która będzie teraz ustawić w połączeniu z innych właściwości. W tym przypadku jeden pobiera `DBPROP_IRowsetLocate`, `DBPROP_LITERALBOOKMARKS`, lub `DBPROP_ORDEREDBOOKMARKS` właściwość, jedną wartość `DBPROP_BOOKMARKS` właściwości.

[!code-cpp[NVC_OLEDB_Provider#2](../../data/oledb/codesnippet/cpp/cutlprops-onpropertychanged_1.h)]

## <a name="setpropvalue"></a> CUtlProps::SetPropValue

Ustawia właściwość w zbiorze właściwości.

### <a name="syntax"></a>Składnia

```cpp
HRESULT SetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>Parametry

*pguidPropSet*<br/>
[in] Identyfikator GUID zestawu właściwości.

*dwPropId*<br/>
[in] Indeks właściwości.

*pvValue*<br/>
[in] Wskaźnik do typu variant, który zawiera nową wartość właściwości.

### <a name="return-value"></a>Wartość zwracana

`Failure` błąd i S_OK w przypadku powodzenia.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura szablonu dostawcy OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)