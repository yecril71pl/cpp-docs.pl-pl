---
title: Klasa CComClassFactorySingleton
ms.date: 11/04/2016
f1_keywords:
- CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton::CreateInstance
- ATLCOM/ATL::CComClassFactorySingleton::m_spObj
helpviewer_keywords:
- CComClassFactorySingleton class
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
ms.openlocfilehash: ec860f7ef59b7d3289bf2e18fea0f0e064a7c8f9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320818"
---
# <a name="ccomclassfactorysingleton-class"></a>Klasa CComClassFactorySingleton

Ta klasa pochodzi z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) i używa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) do konstruowania pojedynczego obiektu.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa.

`CComClassFactorySingleton`pochodzi z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) i używa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) do konstruowania pojedynczego obiektu. Każde wywołanie `CreateInstance` metody po prostu wysyła zapytanie do tego obiektu dla wskaźnika interfejsu.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComClassFactorySingleton::CreateInstance](#createinstance)|Zapytania `m_spObj` dotyczące wskaźnika interfejsu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComClassFactorySingleton::m_spObj](#m_spobj)|[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) obiekt zbudowany `CComClassFactorySingleton`przez .|

## <a name="remarks"></a>Uwagi

Obiekty ATL zwykle nabywają fabrykę klas, wywodząc się z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera [makro DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), `CComClassFactory` który deklaruje jako fabryka klas domyślnych. Aby `CComClassFactorySingleton`użyć , określ [makro DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) w definicji klasy obiektu. Przykład:

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CComObjectRootBase`

[Ccomobjectrootex](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

[CComClassFactory (Polski)](../../atl/reference/ccomclassfactory-class.md)

`CComClassFactorySingleton`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="ccomclassfactorysingletoncreateinstance"></a><a name="createinstance"></a>CComClassFactorySingleton::CreateInstance

Wywołania `QueryInterface` za pośrednictwem [m_spObj,](#m_spobj) aby pobrać wskaźnik interfejsu.

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

## <a name="ccomclassfactorysingletonm_spobj"></a><a name="m_spobj"></a>CComClassFactorySingleton::m_spObj

[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) obiekt zbudowany `CComClassFactorySingleton`przez .

```
CComPtr<IUnknown> m_spObj;
```

### <a name="remarks"></a>Uwagi

Każde wywołanie [metody CreateInstance](#createinstance) po prostu wysyła zapytanie do tego obiektu dla wskaźnika interfejsu.

Należy zauważyć, że `m_spObj` bieżąca forma przedstawia przełomową zmianę w stosunku do sposobu, który `CComClassFactorySingleton` działał w poprzednich wersjach ATL. W poprzednich `CComClassFactorySingleton` wersjach obiekt został utworzony w tym samym czasie co fabryka klas podczas inicjowania serwera. W języku Visual C++.NET 2003 i nowszych obiekt jest tworzony leniwie, na pierwsze żądanie. Ta zmiana może spowodować błędy w programach, które opierają się na wczesnej inicjowania.

## <a name="see-also"></a>Zobacz też

[Iclassfactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[Klasa CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)<br/>
[Klasa CComClassFactoryAutoThread, klasa](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[Ccomglobalsthreadmodel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
