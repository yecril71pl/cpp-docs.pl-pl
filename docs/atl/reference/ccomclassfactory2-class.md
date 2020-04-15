---
title: Klasa CComClassFactory2
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory2
- ATLCOM/ATL::CComClassFactory2
- ATLCOM/ATL::CComClassFactory2::CreateInstance
- ATLCOM/ATL::CComClassFactory2::CreateInstanceLic
- ATLCOM/ATL::CComClassFactory2::GetLicInfo
- ATLCOM/ATL::CComClassFactory2::LockServer
- ATLCOM/ATL::CComClassFactory2::RequestLicKey
helpviewer_keywords:
- CComClassFactory2 class
ms.assetid: 19b66fd6-b9ed-47a0-822c-8132184f5a3e
ms.openlocfilehash: 0cb2064cfaea6317c4522ff917f3963fca2219b8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321013"
---
# <a name="ccomclassfactory2-class"></a>Klasa CComClassFactory2

Ta klasa implementuje interfejs [IClassFactory2.](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)

## <a name="syntax"></a>Składnia

```
template <class license>
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

#### <a name="parameters"></a>Parametry

*Licencji*<br/>
Klasa, która implementuje następujące funkcje statyczne:

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComClassFactory2::Utwórz instance](#createinstance)|Tworzy obiekt określonego identyfikatora CLSID.|
|[CComClassFactory2::CreateInstanceLic](#createinstancelic)|Biorąc pod uwagę klucz licencyjny, tworzy obiekt określonego identyfikatora CLSID.|
|[CComClassFactory2::GetLicInfo](#getlicinfo)|Pobiera informacje opisujące możliwości licencjonowania fabryki klasy.|
|[CComClassFactory2::LockServer](#lockserver)|Blokuje fabrykę klasy w pamięci.|
|[CComClassFactory2::RequestLicKey](#requestlickey)|Tworzy i zwraca klucz licencyjny.|

## <a name="remarks"></a>Uwagi

`CComClassFactory2`implementuje interfejs [IClassFactory2,](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) który jest rozszerzeniem [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory). `IClassFactory2`steruje tworzeniem obiektów za pośrednictwem licencji. Fabryczna klasa wykonywana na licencjonowanym komputerze może zapewnić klucz licencji w czasie wykonywania. Ten klucz licencyjny umożliwia aplikacji tworzenie wystąpienia obiektów, gdy pełna licencja komputera nie istnieje.

Obiekty ATL zwykle nabywają fabrykę klas, wywodząc się z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera [makro DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), który deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako fabryka klasy domyślnej. Aby `CComClassFactory2`użyć , określ [makro DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) w definicji klasy obiektu. Przykład:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]

`CMyLicense`, parametr szablonu `CComClassFactory2`do , musi `VerifyLicenseKey` `GetLicenseKey`implementować `IsLicenseValid`funkcje statyczne , i . Oto przykład prostej klasy licencji:

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]

`CComClassFactory2`pochodzi zarówno `CComClassFactory2Base` z *licencji.* `CComClassFactory2Base`, z kolei, `IClassFactory2` wywodzi się z i `CComObjectRootEx< CComGlobalsThreadModel >`.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CComObjectRootBase`

`license`

[Ccomobjectrootex](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory2`

`CComClassFactory2`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="ccomclassfactory2createinstance"></a><a name="createinstance"></a>CComClassFactory2::Utwórz instance

Tworzy obiekt określonego identyfikatora CLSID i pobiera wskaźnik interfejsu do tego obiektu.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Parametry

*pUnkOuter (Nieunikat.*<br/>
[w] Jeśli obiekt jest tworzony jako część agregacji, a następnie *pUnkOuter* musi być zewnętrzny nieznany. W przeciwnym razie *pUnkOuter* musi mieć wartość NULL.

*Riid*<br/>
[w] Identyfikator żądanego interfejsu. Jeśli *pUnkOuter* nie jest NULL, `IID_IUnknown` *riid* musi być .

*ppvObj (polski)*<br/>
[na zewnątrz] Wskaźnik do wskaźnika interfejsu identyfikowanego przez *riid*. Jeśli obiekt nie obsługuje tego interfejsu, *ppvObj* jest ustawiona na wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Wymaga pełnej licencji na urządzenie. Jeśli pełna licencja komputera nie istnieje, [wywołanie CreateInstanceLic](#createinstancelic).

## <a name="ccomclassfactory2createinstancelic"></a><a name="createinstancelic"></a>CComClassFactory2::CreateInstanceLic

Podobnie [jak CreateInstance](#createinstance) `CreateInstanceLic` , z tą różnicą, że wymaga klucza licencyjnego.

```
STDMETHOD(CreateInstanceLic)(
    IUnknown* pUnkOuter,
    IUnknown* /* pUnkReserved
*/,
    REFIID riid,
    BSTR bstrKey,
    void** ppvObject);
```

### <a name="parameters"></a>Parametry

*pUnkOuter (Nieunikat.*<br/>
[w] Jeśli obiekt jest tworzony jako część agregacji, a następnie *pUnkOuter* musi być zewnętrzny nieznany. W przeciwnym razie *pUnkOuter* musi mieć wartość NULL.

*pUnkReserved (Nie)*<br/>
[w] Nie używane. Musi mieć wartość NULL.

*Riid*<br/>
[w] Identyfikator żądanego interfejsu. Jeśli *pUnkOuter* nie jest NULL, `IID_IUnknown` *riid* musi być .

*klawisz bstrKey*<br/>
[w] Klucz licencji w czasie wykonywania uzyskany `RequestLicKey`wcześniej z połączenia do . Ten klucz jest wymagany do utworzenia obiektu.

*ppvObiekt*<br/>
[na zewnątrz] Wskaźnik do wskaźnika interfejsu określonego przez *riid*. Jeśli obiekt nie obsługuje tego interfejsu, *ppvObject* jest ustawiona na wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Klucz licencji można uzyskać za pomocą [requestlickey](#requestlickey). Aby utworzyć obiekt na nielicencjonowanym komputerze, `CreateInstanceLic`należy wywołać program .

## <a name="ccomclassfactory2getlicinfo"></a><a name="getlicinfo"></a>CComClassFactory2::GetLicInfo

Wypełnia strukturę [LICINFO](/windows/win32/api/ocidl/ns-ocidl-licinfo) informacjami opisującymi możliwości licencjonowania fabryki klas.

```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```

### <a name="parameters"></a>Parametry

*pLicInfo (pLicInfo)*<br/>
[na zewnątrz] Wskaźnik do `LICINFO` struktury.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Element `fRuntimeKeyAvail` członkowski tej struktury wskazuje, czy, biorąc pod uwagę klucz licencyjny, fabryka klas umożliwia tworzenie obiektów na nielicencjonowanym komputerze. *FLicVerified* element członkowski wskazuje, czy istnieje pełna licencja komputera.

## <a name="ccomclassfactory2lockserver"></a><a name="lockserver"></a>CComClassFactory2::LockServer

Zwiększa i zmniejsza liczbę blokad modułu `_Module::Lock` przez `_Module::Unlock`wywołanie i , odpowiednio.

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>Parametry

*Stado*<br/>
[w] Jeśli true, liczba blokad jest zwiększana; w przeciwnym razie liczba blokad jest zmniejszana.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

`_Module`odnosi się do globalnego wystąpienia [CComModule](../../atl/reference/ccommodule-class.md) lub klasy pochodzące z niego.

Wywołanie `LockServer` umożliwia klientowi przytrzymanie fabryki klas, dzięki czemu można szybko utworzyć wiele obiektów.

## <a name="ccomclassfactory2requestlickey"></a><a name="requestlickey"></a>CComClassFactory2::RequestLicKey

Tworzy i zwraca klucz licencyjny, pod warunkiem, że `fRuntimeKeyAvail` element członkowski struktury [LICINFO](/windows/win32/api/ocidl/ns-ocidl-licinfo) ma wartość PRAWDA.

```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```

### <a name="parameters"></a>Parametry

*dwReserved (niesłuszne)*<br/>
[w] Nie używane. Musi być zero.

*klawisz pbstrKey*<br/>
[na zewnątrz] Wskaźnik do klucza licencyjnego.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Klucz licencyjny jest wymagany do wywoływania [CreateInstanceLic](#createinstancelic) do utworzenia obiektu na nielicencjonowanym komputerze. Jeśli `fRuntimeKeyAvail` jest false, a następnie obiekty mogą być tworzone tylko na komputerze w pełni licencjonowane.

Wywołanie [GetLicInfo,](#getlicinfo) aby `fRuntimeKeyAvail`pobrać wartość . .

## <a name="see-also"></a>Zobacz też

[Klasa CComClassFactoryAutoThread, klasa](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[Klasa CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[Ccomglobalsthreadmodel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
