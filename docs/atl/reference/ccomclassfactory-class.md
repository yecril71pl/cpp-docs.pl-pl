---
title: Klasa CComClassFactory | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComClassFactory
- ATLCOM/ATL::CComClassFactory
- ATLCOM/ATL::CComClassFactory::CreateInstance
- ATLCOM/ATL::CComClassFactory::LockServer
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactory class
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7a144f4ff9902a633933ae556df872a9d55a5409
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ccomclassfactory-class"></a>Klasa CComClassFactory
Ta klasa implementuje [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```
class CComClassFactory 
   : public IClassFactory,  
     public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComClassFactory::CreateInstance](#createinstance)|Tworzy obiekt CLSID określony.|  
|[CComClassFactory::LockServer](#lockserver)|Blokuje fabryki klasy w pamięci.|  
  
## <a name="remarks"></a>Uwagi  
 `CComClassFactory` implementuje [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) interfejsu, który zawiera metody do tworzenia obiektu określonego identyfikatora CLSID, a także blokowania fabryki klasy w pamięci, aby pozwolić na szybsze tworzenie nowych obiektów. **IClassFactory** musi zostać wdrożone dla każdej klasy, który zarejestrował w rejestrze systemu i do której można przypisać CLSID.  
  
 Zwykle obiektów ATL uzyskać fabryki klasy przez wynikających z [klasy CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera makra [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), który deklaruje `CComClassFactory` jako domyślną fabrykę klas. Aby zastąpić to ustawienie domyślne, określ jedną z `DECLARE_CLASSFACTORY` *XXX* makra w definicji klasy. Na przykład [DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex) makro używa określonej klasy fabryki klasy:  
  
 [!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]  
  
 Powyżej definicji klasy określa, że **CMyClassFactory** będzie używana jako fabryka klas domyślnego obiektu. **CMyClassFactory** musi pochodzić od `CComClassFactory` i zastąpić `CreateInstance`.  
  
 ATL udostępnia trzy makra, które deklaruje fabrykę klas:  
  
- [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) używa [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), która kontroluje tworzenie za pośrednictwem licencji.  
  
- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) używa [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), która tworzy obiekty w wielu apartamentach.  
  
- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) używa [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), która tworzy pojedynczy [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="createinstance"></a>  CComClassFactory::CreateInstance  
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
  
##  <a name="lockserver"></a>  CComClassFactory::LockServer  
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
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [Przegląd klas](../../atl/atl-class-overview.md)
