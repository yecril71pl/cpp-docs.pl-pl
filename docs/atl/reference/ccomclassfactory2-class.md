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
ms.openlocfilehash: fe4ddaab8de2369c7cb1b31132f686bc6037676b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205528"
---
# <a name="ccomclassfactory2-class"></a>Klasa CComClassFactory2
Ta klasa implementuje [IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class license>  
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```  
  
#### <a name="parameters"></a>Parametry  
 *Licencja*  
 Klasa, która implementuje następujące funkcje statyczne:  
  
- `static BOOL VerifyLicenseKey( BSTR bstr );`  
  
- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`  
  
- `static BOOL IsLicenseValid( );`  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComClassFactory2::CreateInstance](#createinstance)|Tworzy obiekt z określonym identyfikatorem CLSID.|  
|[CComClassFactory2::CreateInstanceLic](#createinstancelic)|Podany klucz licencji tworzy obiekt z określonym identyfikatorem CLSID.|  
|[CComClassFactory2::GetLicInfo](#getlicinfo)|Pobiera informacje opisujące licencjonowania możliwości fabryki klas.|  
|[CComClassFactory2::LockServer](#lockserver)|Blokuje fabryki klas w pamięci.|  
|[CComClassFactory2::RequestLicKey](#requestlickey)|Tworzy i zwraca klucz licencji.|  
  
## <a name="remarks"></a>Uwagi  
 `CComClassFactory2` implementuje [IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2) interfejs, który jest rozszerzeniem programu [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory). `IClassFactory2` Tworzenie obiektów kontrolki za pomocą licencji. Fabryki klas na maszynie licencjonowane wykonywania może zapewnić klucz licencji czasu wykonywania. Ten klucz licencji umożliwia aplikacji do tworzenia wystąpień obiektów, gdy licencja pełną maszyny nie istnieje.  
  
 Obiekty ATL zwykle uzyskać fabryki klas, wynikające z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera makra [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), która deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako domyślnej fabryki klas. Aby użyć `CComClassFactory2`, określ [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) makra w definicji klasy do obiektu. Na przykład:  
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]  
  
 `CMyLicense`, parametr szablonu `CComClassFactory2`, należy zaimplementować funkcje statyczne `VerifyLicenseKey`, `GetLicenseKey`, i `IsLicenseValid`. Oto przykład klasy proste licencji:  
  
 [!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]  
  
 `CComClassFactory2` pochodzi z obu `CComClassFactory2Base` i *licencji*. `CComClassFactory2Base`, z kolei pochodzi od klasy `IClassFactory2` i `CComObjectRootEx< CComGlobalsThreadModel >`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CComObjectRootBase`  
  
 `license`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory2`  
  
 `CComClassFactory2`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="createinstance"></a>  CComClassFactory2::CreateInstance  
 Tworzy obiekt z określonym identyfikatorem CLSID i pobiera wskaźnik interfejsu do tego obiektu.  
  
```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnkOuter*  
 [in] Jeśli obiekt jest tworzony jako część agregacji, następnie *pUnkOuter* musi być zewnętrzny nieznany. W przeciwnym razie *pUnkOuter* musi mieć wartość NULL.  
  
 *Parametr riid*  
 [in] Identyfikator IID żądanego interfejsu. Jeśli *pUnkOuter* jest różna od NULL, *riid* musi być `IID_IUnknown`.  
  
 *ppvObj*  
 [out] Wskaźnik do wskaźnika interfejsu identyfikowane przez *riid*. Jeśli obiekt nie obsługuje ten interfejs *ppvObj* ma wartość NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Komputer musi być w pełni licencjonowane. Jeśli nie ma licencji maszyny pełną, wywołaj [CreateInstanceLic](#createinstancelic).  
  
##  <a name="createinstancelic"></a>  CComClassFactory2::CreateInstanceLic  
 Podobnie jak [CreateInstance —](#createinstance), chyba że `CreateInstanceLic` wymaga klucza licencji.  
  
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
 *pUnkOuter*  
 [in] Jeśli obiekt jest tworzony jako część agregacji, następnie *pUnkOuter* musi być zewnętrzny nieznany. W przeciwnym razie *pUnkOuter* musi mieć wartość NULL.  
  
 *pUnkReserved*  
 [in] Nie jest używany. Musi mieć wartość NULL.  
  
 *Parametr riid*  
 [in] Identyfikator IID żądanego interfejsu. Jeśli *pUnkOuter* jest różna od NULL, *riid* musi być `IID_IUnknown`.  
  
 *bstrKey*  
 [in] Klucz licencji środowiska wykonawczego zostały wcześniej uzyskane z wywołania `RequestLicKey`. Ten klucz jest wymagany do utworzenia obiektu.  
  
 *ppvObject*  
 [out] Wskaźnik do wskaźnika interfejsu, określonego przez *riid*. Jeśli obiekt nie obsługuje ten interfejs *ppvObject* ma wartość NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Można uzyskać licencji klucza przy użyciu [RequestLicKey](#requestlickey). Aby utworzyć obiekt na maszynie bez licencji, należy wywołać `CreateInstanceLic`.  
  
##  <a name="getlicinfo"></a>  CComClassFactory2::GetLicInfo  
 Wypełnia [LICINFO](/windows/desktop/api/ocidl/ns-ocidl-taglicinfo) struktury udostępnić informacje opisujące fabryki klas firmy licencjonowania możliwości.  
  
```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *pLicInfo*  
 [out] Wskaźnik do `LICINFO` struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 `fRuntimeKeyAvail` Członkiem tej struktury wskazuje, czy, biorąc pod uwagę klucz licencji, fabryki klas obiektów, które ma zostać utworzony na maszynie bez licencji. *FLicVerified* członka wskazuje na to, czy istnieje licencja pełną maszyny.  
  
##  <a name="lockserver"></a>  CComClassFactory2::LockServer  
 Zwiększa i zmniejsza liczbę blokad modułu, wywołując `_Module::Lock` i `_Module::Unlock`, odpowiednio.  
  
```
STDMETHOD(LockServer)(BOOL fLock);
```  
  
### <a name="parameters"></a>Parametry  
 *Stada*  
 [in] W przypadku opcji TRUE jest zwiększany liczbę blokad; w przeciwnym razie liczbę blokad zostanie zmniejszona.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 `_Module` odwołuje się do globalnego wystąpienia [CComModule](../../atl/reference/ccommodule-class.md) lub klasa pochodnej od niego.  
  
 Wywoływanie `LockServer` umożliwia klientowi do zatrzymania się na fabrykę klas, umożliwiając szybkie tworzenie wielu obiektów.  
  
##  <a name="requestlickey"></a>  CComClassFactory2::RequestLicKey  
 Tworzy i zwraca klucz licencji, pod warunkiem, że `fRuntimeKeyAvail` członkiem [LICINFO](/windows/desktop/api/ocidl/ns-ocidl-taglicinfo) struktura ma wartość TRUE.  
  
```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```  
  
### <a name="parameters"></a>Parametry  
 *dwReserved*  
 [in] Nie jest używany. Musi mieć wartość zero.  
  
 *pbstrKey*  
 [out] Wskaźnik do klucza licencji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Klucz licencji jest wymagana do wywoływania [CreateInstanceLic](#createinstancelic) do utworzenia obiektu na maszynie bez licencji. Jeśli `fRuntimeKeyAvail` ma wartość FAŁSZ, a następnie obiekty można tworzyć tylko w pełni licencjonowanej maszynie.  
  
 Wywołaj [GetLicInfo](#getlicinfo) można pobrać wartości `fRuntimeKeyAvail`.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)   
 [Klasa CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)   
 [Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
