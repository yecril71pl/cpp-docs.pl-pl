---
title: Klasa CComClassFactoryAutoThread
ms.date: 11/04/2016
f1_keywords:
- CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread::CreateInstance
- ATLCOM/ATL::CComClassFactoryAutoThread::LockServer
helpviewer_keywords:
- CComClassFactoryAutoThread class
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
ms.openlocfilehash: 73879a73a48290e19d2a27307884953129826df7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497489"
---
# <a name="ccomclassfactoryautothread-class"></a>Klasa CComClassFactoryAutoThread

Ta klasa implementuje interfejs [elementu IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) i umożliwia tworzenie obiektów w wielu apartamentachach.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

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
|[CComClassFactoryAutoThread::CreateInstance](#createinstance)|Tworzy obiekt o określonym identyfikatorze CLSID.|
|[CComClassFactoryAutoThread::LockServer](#lockserver)|Blokuje fabrykę klas w pamięci.|

## <a name="remarks"></a>Uwagi

`CComClassFactoryAutoThread`jest podobny do [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), ale umożliwia tworzenie obiektów w wielu apartamentachach. Aby skorzystać z tej obsługi, należy utworzyć moduł EXE z [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Obiekty ATL zwykle uzyskują fabrykę klasy poprzez wyprowadzanie z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)makro, które deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako domyślną fabrykę klas. Aby użyć `CComClassFactoryAutoThread`, określ makro [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) w definicji klasy obiektu. Na przykład:

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/ccomclassfactoryautothread-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

`CComClassFactoryAutoThread`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="createinstance"></a>CComClassFactoryAutoThread:: CreateInstance

Tworzy obiekt o określonym identyfikatorze CLSID i Pobiera wskaźnik interfejsu do tego obiektu.

```
STDMETHODIMP CreateInstance(
    LPUNKNOWN pUnkOuter,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>Parametry

*pUnkOuter*<br/>
podczas Jeśli obiekt jest tworzony w ramach agregacji, *pUnkOuter* musi być nieznane zewnętrzne. W przeciwnym razie *pUnkOuter* musi mieć wartość null.

*riid*<br/>
podczas Identyfikator IID żądanego interfejsu. Jeśli *pUnkOuter* ma wartość różną od null, *riid* musi `IID_IUnknown`być.

*ppvObj*<br/>
określoną Wskaźnik do wskaźnika interfejsu identyfikowanego przez *riid*. Jeśli obiekt nie obsługuje tego interfejsu, *ppvObj* ma wartość null.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli moduł pochodzi z [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), najpierw `CreateInstance` wybiera wątek, aby utworzyć obiekt w skojarzonej apartamentu.

##  <a name="lockserver"></a>CComClassFactoryAutoThread:: LockServer —

Zwiększa i zmniejsza liczbę blokad modułu przez wywoływanie `_Module::Lock` i `_Module::Unlock`, odpowiednio.

```
STDMETHODIMP LockServer(BOOL fLock);
```

### <a name="parameters"></a>Parametry

*Zarodowych*<br/>
podczas W przypadku wartości TRUE liczba blokad jest zwiększana; w przeciwnym razie licznik blokady jest zmniejszany.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Gdy jest `CComClassFactoryAutoThread`używany `_Module` , zazwyczaj odnosi się do globalnego wystąpienia [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Wywołanie `LockServer` umożliwia klientowi przechowywanie w fabryce klasy, dzięki czemu można szybko utworzyć wiele obiektów.

## <a name="see-also"></a>Zobacz także

[Elementu IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[Klasa CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)<br/>
[Klasa CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
