---
title: CComClassFactory Class
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory
- ATLCOM/ATL::CComClassFactory
- ATLCOM/ATL::CComClassFactory::CreateInstance
- ATLCOM/ATL::CComClassFactory::LockServer
helpviewer_keywords:
- CComClassFactory class
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
ms.openlocfilehash: 85ef287a905abc7b3151628c0f5dc29b9050b187
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246725"
---
# <a name="ccomclassfactory-class"></a>CComClassFactory Class

Ta klasa implementuje [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory) interfejsu.

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
|[CComClassFactory::CreateInstance](#createinstance)|Tworzy obiekt z określonym identyfikatorem CLSID.|
|[CComClassFactory::LockServer](#lockserver)|Blokuje fabryki klas w pamięci.|

## <a name="remarks"></a>Uwagi

`CComClassFactory` implementuje [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory) interfejs, który zawiera metody do tworzenia obiektu z określonym identyfikatorem CLSID, jak również blokowanie fabryki klas w pamięci umożliwiające szybsze tworzenie nowych obiektów. `IClassFactory` należy zaimplementować dla każdej klasy, która zarejestrowania w rejestrze systemowym i który przypisania CLSID.

Obiekty ATL zwykle uzyskać fabryki klas, wynikające z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera makra [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), która deklaruje `CComClassFactory` jako domyślnej fabryki klas. Aby zastąpić to ustawienie domyślne, należy określić jedną z `DECLARE_CLASSFACTORY` *XXX* makra w definicji klasy. Na przykład [DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex) makro używa określonej klasie dla fabryki klas:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]

Powyższej definicji klasy określa, że `CMyClassFactory` będzie służyć jako obiektu domyślnej fabryki klas. `CMyClassFactory` musi pochodzić od klasy `CComClassFactory` i zastąpić `CreateInstance`.

ATL udostępnia trzy makra, które deklarują fabrykę klas:

- [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) używa [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), która kontroluje tworzenie za pomocą licencji.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) używa [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), który tworzy obiekty w wielu apartamentach.

- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) używa [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), który tworzy jeden [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="createinstance"></a>  CComClassFactory::CreateInstance

Tworzy obiekt z określonym identyfikatorem CLSID i pobiera wskaźnik interfejsu do tego obiektu.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Parametry

*pUnkOuter*<br/>
[in] Jeśli obiekt jest tworzony jako część agregacji, następnie *pUnkOuter* musi być zewnętrzny nieznany. W przeciwnym razie *pUnkOuter* musi mieć wartość NULL.

*Parametr riid*<br/>
[in] Identyfikator IID żądanego interfejsu. Jeśli *pUnkOuter* jest różna od NULL, *riid* musi być `IID_IUnknown`.

*ppvObj*<br/>
[out] Wskaźnik do wskaźnika interfejsu identyfikowane przez *riid*. Jeśli obiekt nie obsługuje ten interfejs *ppvObj* ma wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

##  <a name="lockserver"></a>  CComClassFactory::LockServer

Zwiększa i zmniejsza liczbę blokad modułu, wywołując `_Module::Lock` i `_Module::Unlock`, odpowiednio.

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>Parametry

*Stada*<br/>
[in] W przypadku opcji TRUE jest zwiększany liczbę blokad; w przeciwnym razie liczbę blokad zostanie zmniejszona.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

`_Module` odwołuje się do globalnego wystąpienia [CComModule](../../atl/reference/ccommodule-class.md) lub klasa pochodnej od niego.

Wywoływanie `LockServer` umożliwia klientowi, które mają być przechowywane fabrykę klas, aby można go szybko utworzyć wiele obiektów.

## <a name="see-also"></a>Zobacz także

[Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
