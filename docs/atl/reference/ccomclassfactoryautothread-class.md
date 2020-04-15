---
title: Klasa CComClassFactoryAutoThread, klasa
ms.date: 11/04/2016
f1_keywords:
- CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread::CreateInstance
- ATLCOM/ATL::CComClassFactoryAutoThread::LockServer
helpviewer_keywords:
- CComClassFactoryAutoThread class
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
ms.openlocfilehash: e997d92adfa9df46c82dacbd297db495b037c6e6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320905"
---
# <a name="ccomclassfactoryautothread-class"></a>Klasa CComClassFactoryAutoThread, klasa

Ta klasa implementuje interfejs [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) i umożliwia tworzenie obiektów w wielu mieszkaniach.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

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
|[CComClassFactoryAutoThread::CreateInstance](#createinstance)|Tworzy obiekt określonego identyfikatora CLSID.|
|[CComClassFactoryAutoThread::LockServer](#lockserver)|Blokuje fabrykę klasy w pamięci.|

## <a name="remarks"></a>Uwagi

`CComClassFactoryAutoThread`jest podobny do [CComClassFactory,](../../atl/reference/ccomclassfactory-class.md)ale umożliwia tworzenie obiektów w wielu mieszkaniach. Aby skorzystać z tej pomocy technicznej, należy wykorzystać z modułu EXE z [modułu CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Obiekty ATL zwykle nabywają fabrykę klas, wywodząc się z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera [makro DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), który deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako fabryka klasy domyślnej. Aby `CComClassFactoryAutoThread`użyć , określ [makro DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) w definicji klasy obiektu. Przykład:

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/ccomclassfactoryautothread-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CComObjectRootBase`

[Ccomobjectrootex](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

`CComClassFactoryAutoThread`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="ccomclassfactoryautothreadcreateinstance"></a><a name="createinstance"></a>CComClassFactoryAutoThread::CreateInstance

Tworzy obiekt określonego identyfikatora CLSID i pobiera wskaźnik interfejsu do tego obiektu.

```
STDMETHODIMP CreateInstance(
    LPUNKNOWN pUnkOuter,
    REFIID riid,
    void** ppvObj);
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

Jeśli moduł pochodzi z [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), `CreateInstance` najpierw wybiera wątek, aby utworzyć obiekt w skojarzonym mieszkaniu.

## <a name="ccomclassfactoryautothreadlockserver"></a><a name="lockserver"></a>CComClassFactoryAutoThread::LockServer

Zwiększa i zmniejsza liczbę blokad modułu `_Module::Lock` przez `_Module::Unlock`wywołanie i , odpowiednio.

```
STDMETHODIMP LockServer(BOOL fLock);
```

### <a name="parameters"></a>Parametry

*Stado*<br/>
[w] Jeśli true, liczba blokad jest zwiększana; w przeciwnym razie liczba blokad jest zmniejszana.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Podczas `CComClassFactoryAutoThread`korzystania `_Module` , zazwyczaj odnosi się do globalnego wystąpienia [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Wywołanie `LockServer` umożliwia klientowi przytrzymanie fabryki klas, dzięki czemu można szybko utworzyć wiele obiektów.

## <a name="see-also"></a>Zobacz też

[Iclassfactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[Klasa CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)<br/>
[Klasa CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[Ccomglobalsthreadmodel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
