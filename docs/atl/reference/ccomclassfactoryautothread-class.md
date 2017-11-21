---
title: Klasa CComClassFactoryAutoThread | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread::CreateInstance
- ATLCOM/ATL::CComClassFactoryAutoThread::LockServer
dev_langs: C++
helpviewer_keywords: CComClassFactoryAutoThread class
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dfeadfba46f1dd0b033f3d82571e82c59a449ec9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccomclassfactoryautothread-class"></a>Klasa CComClassFactoryAutoThread
Ta klasa implementuje [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364) interfejsu i umożliwia tworzenie w apartamentach wiele obiektów.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CComClassFactoryAutoThread 
   : public IClassFactory, 
     public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComClassFactoryAutoThread::CreateInstance](#createinstance)|Tworzy obiekt CLSID określony.|  
|[CComClassFactoryAutoThread::LockServer](#lockserver)|Blokuje fabryki klasy w pamięci.|  
  
## <a name="remarks"></a>Uwagi  
 `CComClassFactoryAutoThread`przypomina [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), ale możliwe jest tworzenie w apartamentach wiele obiektów. Aby móc korzystać z tej pomocy technicznej, pochodzi z modułu EXE [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).  
  
 Zwykle obiektów ATL uzyskać fabryki klasy przez wynikających z [klasy CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera makra [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), który deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako domyślną fabrykę klas. Aby użyć `CComClassFactoryAutoThread`, określ [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) makra w definicji klasy do obiektu. Na przykład:  
  
 [!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/ccomclassfactoryautothread-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory`  
  
 `CComClassFactoryAutoThread`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="createinstance"></a>CComClassFactoryAutoThread::CreateInstance  
 Tworzy obiekt określonego identyfikatora CLSID i pobiera wskaźnika interfejsu do tego obiektu.  
  
```
STDMETHODIMP CreateInstance(
    LPUNKNOWN pUnkOuter,
    REFIID riid,
    void** ppvObj);
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
 Jeśli pochodzi z klasy modułu [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), `CreateInstance` najpierw wybiera do utworzenia obiektu w skojarzonych apartamentu wątku.  
  
##  <a name="lockserver"></a>CComClassFactoryAutoThread::LockServer  
 Zwiększa i zmniejsza liczbę blokad modułu wywołując **_Module::Lock** i **_Module::Unlock**odpowiednio.  
  
```
STDMETHODIMP LockServer(BOOL fLock);
```  
  
### <a name="parameters"></a>Parametry  
 `fLock`  
 [in] Jeśli **TRUE**, liczbę blokad jest zwiększany; w przeciwnym razie, zostanie zmniejszona liczbę blokad.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Korzystając z `CComClassFactoryAutoThread`, **_Module** zazwyczaj odwołuje się do globalnego wystąpienia [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).  
  
 Wywoływanie `LockServer` umożliwia klientowi przechowywania na fabrykę klas, dzięki czemu można szybko utworzyć wiele obiektów.  
  
## <a name="see-also"></a>Zobacz też  
 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)   
 [Klasa CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)   
 [Klasa CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)   
 [Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
 [Przegląd klas](../../atl/atl-class-overview.md)
