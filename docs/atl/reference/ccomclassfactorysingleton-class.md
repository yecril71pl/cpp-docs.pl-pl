---
title: Klasa CComClassFactorySingleton | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton::CreateInstance
- ATLCOM/ATL::CComClassFactorySingleton::m_spObj
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactorySingleton class
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 754a3abd02a4a09df3e36aa9aea75c400ef00761
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360384"
---
# <a name="ccomclassfactorysingleton-class"></a>Klasa CComClassFactorySingleton
Ta klasa pochodzi od [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) i używa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) do konstruowania pojedynczego obiektu.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>  
class CComClassFactorySingleton : public CComClassFactory
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasy.  
  
 `CComClassFactorySingleton` pochodną [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) i używa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) do konstruowania pojedynczego obiektu. Każde wywołanie `CreateInstance` metoda po prostu wysyła zapytanie do tego obiektu dla wskaźnika interfejsu.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComClassFactorySingleton::CreateInstance](#createinstance)|Zapytania `m_spObj` dla wskaźnika interfejsu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComClassFactorySingleton::m_spObj](#m_spobj)|[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) tworzony przez obiekt `CComClassFactorySingleton`.|  
  
## <a name="remarks"></a>Uwagi  
 Zwykle obiektów ATL uzyskać fabryki klasy przez wynikających z [klasy CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera makra [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), który deklaruje `CComClassFactory` jako domyślną fabrykę klas. Aby użyć `CComClassFactorySingleton`, określ [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) makra w definicji klasy do obiektu. Na przykład:  
  
 [!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory`  
  
 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)  
  
 `CComClassFactorySingleton`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="createinstance"></a>  CComClassFactorySingleton::CreateInstance  
 Wywołania `QueryInterface` za pośrednictwem [m_spObj](#m_spobj) można pobrać wskaźnika interfejsu.  
  
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
  
##  <a name="m_spobj"></a>  CComClassFactorySingleton::m_spObj  
 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) tworzony przez obiekt `CComClassFactorySingleton`.  
  
```
CComPtr<IUnknown> m_spObj;
```  
  
### <a name="remarks"></a>Uwagi  
 Każde wywołanie [CreateInstance](#createinstance) metoda po prostu wysyła zapytanie do tego obiektu dla wskaźnika interfejsu.  
  
 Należy pamiętać, że bieżący formę `m_spObj` przedstawiono istotne zmiany w sposobie, w który `CComClassFactorySingleton` w poprzednich wersjach ATL. W poprzednich wersjach `CComClassFactorySingleton` obiekt został utworzony w tym samym czasie jako fabryki klasy podczas inicjowania serwera. W programie Visual C++ .NET 2003 obiekt jest tworzony w trybie opóźnienia, po pierwszym żądaniu. Ta zmiana może spowodować błędy w programach, które opierają się na początku inicjowania.  
  
## <a name="see-also"></a>Zobacz też  
 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)   
 [Klasa CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)   
 [Klasa CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)   
 [Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [Przegląd klas](../../atl/atl-class-overview.md)
