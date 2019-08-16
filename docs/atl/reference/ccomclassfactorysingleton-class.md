---
title: CComClassFactorySingleton Class
ms.date: 11/04/2016
f1_keywords:
- CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton::CreateInstance
- ATLCOM/ATL::CComClassFactorySingleton::m_spObj
helpviewer_keywords:
- CComClassFactorySingleton class
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
ms.openlocfilehash: 71705d02140f0392a9ce023c64e7b4125c14443f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497367"
---
# <a name="ccomclassfactorysingleton-class"></a>CComClassFactorySingleton Class

Ta klasa pochodzi z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) i używa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) do konstruowania pojedynczego obiektu.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa.

`CComClassFactorySingleton`pochodzi z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) i używa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) do konstruowania pojedynczego obiektu. Każde wywołanie `CreateInstance` metody po prostu wysyła zapytanie do tego obiektu dla wskaźnika interfejsu.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComClassFactorySingleton:: CreateInstance](#createinstance)|Zapytania `m_spObj` dotyczące wskaźnika interfejsu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComClassFactorySingleton::m_spObj](#m_spobj)|Obiekt [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) skonstruowany przez `CComClassFactorySingleton`.|

## <a name="remarks"></a>Uwagi

Obiekty ATL zwykle uzyskują fabrykę klasy poprzez wyprowadzanie z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)makro, które deklaruje `CComClassFactory` jako domyślną fabrykę klas. Aby użyć `CComClassFactorySingleton`, określ makro [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) w definicji klasy obiektu. Na przykład:

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)

`CComClassFactorySingleton`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="createinstance"></a>CComClassFactorySingleton:: CreateInstance

Wywołuje `QueryInterface` za [m_spObj](#m_spobj) , aby pobrać wskaźnik interfejsu.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
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

##  <a name="m_spobj"></a>CComClassFactorySingleton::m_spObj

Obiekt [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) skonstruowany przez `CComClassFactorySingleton`.

```
CComPtr<IUnknown> m_spObj;
```

### <a name="remarks"></a>Uwagi

Każde wywołanie metody [CreateInstance](#createinstance) po prostu wysyła zapytanie do tego obiektu dla wskaźnika interfejsu.

Należy zauważyć, że bieżąca forma `m_spObj` przedstawia nieprzerwaną zmianę od sposobu, `CComClassFactorySingleton` w którym działały poprzednie wersje ATL. W poprzednich wersjach `CComClassFactorySingleton` obiekt został utworzony w tym samym czasie co fabryka klas podczas inicjowania serwera. W programie C++Visual .NET 2003 i nowszych obiekt jest tworzony opóźnieniem podczas pierwszego żądania. Ta zmiana może spowodować błędy w programach, które opierają się na wczesnej inicjacji.

## <a name="see-also"></a>Zobacz także

[Elementu IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[Klasa CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)<br/>
[Klasa CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
