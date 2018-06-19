---
title: Klasa CComClassFactory2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComClassFactory2
- ATLCOM/ATL::CComClassFactory2
- ATLCOM/ATL::CComClassFactory2::CreateInstance
- ATLCOM/ATL::CComClassFactory2::CreateInstanceLic
- ATLCOM/ATL::CComClassFactory2::GetLicInfo
- ATLCOM/ATL::CComClassFactory2::LockServer
- ATLCOM/ATL::CComClassFactory2::RequestLicKey
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactory2 class
ms.assetid: 19b66fd6-b9ed-47a0-822c-8132184f5a3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: da2b47290d3d0be525ca65b16733c9f42835d24e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363519"
---
# <a name="ccomclassfactory2-class"></a>Klasa CComClassFactory2
Ta klasa implementuje [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class license>  
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```  
  
#### <a name="parameters"></a>Parametry  
 *Licencji*  
 Klasa, która implementuje statycznej następujące funkcje:  
  
- **statyczne VerifyLicenseKey BOOL (BSTR** `bstr` **);**  
  
- **statyczne GetLicenseKey BOOL (DWORD** `dwReserved` **, BSTR\***  `pBstr` **);**  
  
- **statyczne BOOL IsLicenseValid ();**  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComClassFactory2::CreateInstance](#createinstance)|Tworzy obiekt CLSID określony.|  
|[CComClassFactory2::CreateInstanceLic](#createinstancelic)|Podany klucz licencji tworzy określony identyfikator CLSID obiektu.|  
|[CComClassFactory2::GetLicInfo](#getlicinfo)|Pobiera informacje opisujące licencjonowania możliwości fabryki klasy.|  
|[CComClassFactory2::LockServer](#lockserver)|Blokuje fabryki klasy w pamięci.|  
|[CComClassFactory2::RequestLicKey](#requestlickey)|Tworzy i zwraca klucz licencji.|  
  
## <a name="remarks"></a>Uwagi  
 `CComClassFactory2` implementuje [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) interfejs, który jest rozszerzeniem z [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364). **IClassFactory2** formanty obiekt tworzenie za pośrednictwem licencji. Fabryki klas na maszynie licencjonowane wykonywania zapewniają klucz licencji środowiska wykonawczego. Ten klucz licencji umożliwia aplikacji do tworzenia wystąpień obiektów, gdy licencji pełne maszyny nie istnieje.  
  
 Zwykle obiektów ATL uzyskać fabryki klasy przez wynikających z [klasy CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera makra [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), który deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako domyślną fabrykę klas. Aby użyć `CComClassFactory2`, określ [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) makra w definicji klasy do obiektu. Na przykład:  
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]  
  
 **CMyLicense**, parametr szablonu w celu `CComClassFactory2`, musi implementować statyczne funkcje `VerifyLicenseKey`, `GetLicenseKey`, i `IsLicenseValid`. Poniżej przedstawiono przykład klasy proste licencji:  
  
 [!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]  
  
 `CComClassFactory2` pochodzi z obu **CComClassFactory2Base** i *licencji*. **CComClassFactory2Base**, z kolei jest pochodną **IClassFactory2** i **CComObjectRootEx\< CComGlobalsThreadModel >**.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CComObjectRootBase`  
  
 `license`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory2`  
  
 `CComClassFactory2`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="createinstance"></a>  CComClassFactory2::CreateInstance  
 Tworzy obiekt określonego identyfikatora CLSID i pobiera wskaźnika interfejsu do tego obiektu.  
  
```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```  
  
### <a name="parameters"></a>Parametry  
 `pUnkOuter`  
 [in] Jeśli obiekt jest tworzony jako część agregacji, następnie `pUnkOuter` musi być zewnętrzny nieznany. W przeciwnym razie `pUnkOuter` musi być **NULL**.  
  
 `riid`  
 [in] Uzyskanie identyfikatora IID żądanego interfejsu. Jeśli `pUnkOuter` ma wartość inną niż **NULL**, `riid` musi być **IID_IUnknown**.  
  
 `ppvObj`  
 [out] Wskaźnik do wskaźnika interfejsu identyfikowane przez `riid`. Jeśli obiekt nie obsługuje ten interfejs `ppvObj` ustawiono **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Komputer musi być w pełni licencjonowane. Jeśli licencji pełne maszyny nie istnieje, wywołanie [CreateInstanceLic](#createinstancelic).  
  
##  <a name="createinstancelic"></a>  CComClassFactory2::CreateInstanceLic  
 Podobnie jak [CreateInstance](#createinstance), ale `CreateInstanceLic` wymaga klucza licencji.  
  
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
 `pUnkOuter`  
 [in] Jeśli obiekt jest tworzony jako część agregacji, następnie `pUnkOuter` musi być zewnętrzny nieznany. W przeciwnym razie `pUnkOuter` musi być **NULL**.  
  
 *pUnkReserved*  
 [in] Nie jest używany. Musi być **NULL**.  
  
 `riid`  
 [in] Uzyskanie identyfikatora IID żądanego interfejsu. Jeśli `pUnkOuter` ma wartość inną niż **NULL**, `riid` musi być **IID_IUnknown**.  
  
 `bstrKey`  
 [in] Po wywołaniu uzyskany wcześniej klucz licencji środowiska wykonawczego `RequestLicKey`. Ten klucz jest wymagany do utworzenia obiektu.  
  
 `ppvObject`  
 [out] Wskaźnik do wskaźnika interfejsu, określony przez `riid`. Jeśli obiekt nie obsługuje ten interfejs `ppvObject` ustawiono **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Można uzyskać licencji klucza using [RequestLicKey](#requestlickey). Aby utworzyć obiekt komputera bez licencji, należy wywołać `CreateInstanceLic`.  
  
##  <a name="getlicinfo"></a>  CComClassFactory2::GetLicInfo  
 Wypełnia [LICINFO](http://msdn.microsoft.com/library/windows/desktop/ms690590) struktury przy użyciu informacji opisujących fabryki klasy obiektu licencjonowania możliwości.  
  
```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *pLicInfo*  
 [out] Wskaźnik do **LICINFO** struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 `fRuntimeKeyAvail` Członkiem tej struktury wskazuje, czy, danego klucza licencji, fabryki klasy umożliwia obiektów, które ma zostać utworzony na komputerze bez licencji. *FLicVerified* elementu członkowskiego wskazuje, czy istnieje licencja pełne maszyny.  
  
##  <a name="lockserver"></a>  CComClassFactory2::LockServer  
 Zwiększa i zmniejsza liczbę blokad modułu wywołując **_Module::Lock** i **_Module::Unlock**odpowiednio.  
  
```
STDMETHOD(LockServer)(BOOL fLock);
```  
  
### <a name="parameters"></a>Parametry  
 `fLock`  
 [in] Jeśli **TRUE**, liczbę blokad jest zwiększany; w przeciwnym razie, zostanie zmniejszona liczbę blokad.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 **_Module** odwołuje się do globalnego wystąpienia [ccommodule —](../../atl/reference/ccommodule-class.md) lub klasą pochodną go.  
  
 Wywoływanie `LockServer` umożliwia klientowi przechowywania na fabrykę klas, dzięki czemu można szybko utworzyć wiele obiektów.  
  
##  <a name="requestlickey"></a>  CComClassFactory2::RequestLicKey  
 Tworzy i zwraca klucz licencji, pod warunkiem, że `fRuntimeKeyAvail` członkiem [LICINFO](http://msdn.microsoft.com/library/windows/desktop/ms690590) struktura jest **TRUE**.  
  
```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```  
  
### <a name="parameters"></a>Parametry  
 `dwReserved`  
 [in] Nie jest używany. Musi być równy zero.  
  
 `pbstrKey`  
 [out] Wskaźnik do klucza licencji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Klucz licencji jest wymagana dla wywołania [CreateInstanceLic](#createinstancelic) do utworzenia obiektu na komputerze bez licencji. Jeśli `fRuntimeKeyAvail` jest **FALSE**, a następnie obiekty można tworzyć tylko w pełni licencjonowanej maszyny.  
  
 Wywołanie [GetLicInfo](#getlicinfo) można pobrać wartości `fRuntimeKeyAvail`.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)   
 [Klasa CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)   
 [Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [Przegląd klas](../../atl/atl-class-overview.md)
