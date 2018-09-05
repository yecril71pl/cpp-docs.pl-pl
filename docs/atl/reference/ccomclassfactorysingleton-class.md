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
ms.openlocfilehash: 6b812ddd4dbd3c81d9018be926d9103bca3ec796
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755976"
---
# <a name="ccomclassfactorysingleton-class"></a>Klasa CComClassFactorySingleton

Ta klasa jest pochodną [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) i używa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) skonstruowanie pojedynczego obiektu.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template<class T>  
class CComClassFactorySingleton : public CComClassFactory
```

#### <a name="parameters"></a>Parametry

*T*  
Klasa.

`CComClassFactorySingleton` pochodzi od klasy [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) i używa [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) skonstruowanie pojedynczego obiektu. Każde wywołanie `CreateInstance` metoda po prostu wysyła zapytanie dotyczące wskaźnika interfejsu tego obiektu.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComClassFactorySingleton::CreateInstance](#createinstance)|Zapytania `m_spObj` dla wskaźnika interfejsu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComClassFactorySingleton::m_spObj](#m_spobj)|[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) obiekt zbudowany przez `CComClassFactorySingleton`.|

## <a name="remarks"></a>Uwagi

Obiekty ATL zwykle uzyskać fabryki klas, wynikające z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera makra [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), która deklaruje `CComClassFactory` jako domyślnej fabryki klas. Aby użyć `CComClassFactorySingleton`, określ [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) makra w definicji klasy do obiektu. Na przykład:

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

Wywołania `QueryInterface` za pośrednictwem [m_spObj](#m_spobj) do pobrania wskaźnika interfejsu.

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

##  <a name="m_spobj"></a>  CComClassFactorySingleton::m_spObj

[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) obiekt zbudowany przez `CComClassFactorySingleton`.

```
CComPtr<IUnknown> m_spObj;
```

### <a name="remarks"></a>Uwagi

Każde wywołanie [CreateInstance —](#createinstance) metoda po prostu wysyła zapytanie dotyczące wskaźnika interfejsu tego obiektu.

Należy pamiętać, że formularzu bieżącego `m_spObj` przedstawia istotną zmianę w sposobie, w który `CComClassFactorySingleton` w poprzednich wersjach ATL. W poprzednich wersjach `CComClassFactorySingleton` został utworzony obiekt, w tym samym czasie jako fabryki klas podczas inicjowania serwera. W programie Visual C++ .NET 2003 obiekt jest tworzony opóźnieniem, pierwsze żądanie. Ta zmiana może spowodować błędy w programach, które opierają się na początku inicjowania.

## <a name="see-also"></a>Zobacz też

[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)   
[Klasa CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)   
[Klasa CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)   
[Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)   
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
[Klasa — Przegląd](../../atl/atl-class-overview.md)
