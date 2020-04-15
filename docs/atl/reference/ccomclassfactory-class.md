---
title: Klasa CComClassFactory
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory
- ATLCOM/ATL::CComClassFactory
- ATLCOM/ATL::CComClassFactory::CreateInstance
- ATLCOM/ATL::CComClassFactory::LockServer
helpviewer_keywords:
- CComClassFactory class
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
ms.openlocfilehash: 041575339906b83488697f1db5a7f8b08b53070e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321020"
---
# <a name="ccomclassfactory-class"></a>Klasa CComClassFactory

Ta klasa implementuje interfejs [IClassFactory.](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)

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
|[CComClassFactory::Tworzenie instance](#createinstance)|Tworzy obiekt określonego identyfikatora CLSID.|
|[CComClassFactory::LockServer](#lockserver)|Blokuje fabrykę klasy w pamięci.|

## <a name="remarks"></a>Uwagi

`CComClassFactory`implementuje interfejs [IClassFactory,](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) który zawiera metody tworzenia obiektu określonego identyfikatora CLSID, a także blokowanie fabryki klas w pamięci, aby umożliwić szybkie tworzenie nowych obiektów. `IClassFactory`musi być zaimplementowana dla każdej klasy, która jest rejestrowana w rejestrze systemowym i do której można przypisać CLSID.

Obiekty ATL zwykle nabywają fabrykę klas, wywodząc się z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera [makro DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), `CComClassFactory` który deklaruje jako fabryka klas domyślnych. Aby zastąpić tę wartość domyślną, `DECLARE_CLASSFACTORY`określ jedno z makr *XXX* w definicji klasy. Na przykład makro [DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex) używa określonej klasy dla fabryki klas:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]

Powyższa definicja klasy `CMyClassFactory` określa, że będzie używany jako fabryka klas domyślnych obiektu. `CMyClassFactory`musi pochodzić `CComClassFactory` od i `CreateInstance`zastąpić .

ATL udostępnia trzy inne makra, które deklarują fabrykę klas:

- [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) Używa [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), który kontroluje tworzenie za pośrednictwem licencji.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) Używa [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), który tworzy obiekty w wielu mieszkaniach.

- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) Używa [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), który konstruuje pojedynczy [obiekt CComObjectGlobal.](../../atl/reference/ccomobjectglobal-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="ccomclassfactorycreateinstance"></a><a name="createinstance"></a>CComClassFactory::Tworzenie instance

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

## <a name="ccomclassfactorylockserver"></a><a name="lockserver"></a>CComClassFactory::LockServer

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

## <a name="see-also"></a>Zobacz też

[Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[Ccomglobalsthreadmodel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
