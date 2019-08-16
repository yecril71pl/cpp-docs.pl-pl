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
ms.openlocfilehash: 892153e47ac4e9dd45d5dfc01b76f1ce29d23938
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497450"
---
# <a name="ccomclassfactory-class"></a>Klasa CComClassFactory

Ta klasa implementuje interfejs [elementu IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) .

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
|[CComClassFactory:: CreateInstance](#createinstance)|Tworzy obiekt o określonym identyfikatorze CLSID.|
|[CComClassFactory:: LockServer —](#lockserver)|Blokuje fabrykę klas w pamięci.|

## <a name="remarks"></a>Uwagi

`CComClassFactory`implementuje interfejs [elementu IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) , który zawiera metody tworzenia obiektu określonego identyfikatora CLSID, a także blokowania fabryki klas w pamięci, aby umożliwić szybsze tworzenie nowych obiektów. `IClassFactory`należy zaimplementować dla każdej klasy, która jest zarejestrowana w rejestrze systemowym i do której przypisany jest identyfikator CLSID.

Obiekty ATL zwykle uzyskują fabrykę klasy poprzez wyprowadzanie z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)makro, które deklaruje `CComClassFactory` jako domyślną fabrykę klas. Aby zastąpić to ustawienie domyślne, należy określić jedno `DECLARE_CLASSFACTORY`z *XXX* makr w definicji klasy. Na przykład makro [DECLARE_CLASSFACTORY_EX](aggregation-and-class-factory-macros.md#declare_classfactory_ex) używa określonej klasy dla fabryki klas:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]

Powyższa definicja klasy określa, `CMyClassFactory` że będzie używana jako domyślna fabryka klas obiektu. `CMyClassFactory`musi pochodzić od `CComClassFactory` i override `CreateInstance`.

ATL udostępnia trzy inne makra, które deklarują fabrykę klasy:

- [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) Używa [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), który kontroluje tworzenie za pośrednictwem licencji.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) Używa [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), który tworzy obiekty w wielu apartamentachach.

- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) Używa [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), który konstruuje pojedynczy obiekt [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) .

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

##  <a name="createinstance"></a>CComClassFactory:: CreateInstance

Tworzy obiekt o określonym identyfikatorze CLSID i Pobiera wskaźnik interfejsu do tego obiektu.

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

##  <a name="lockserver"></a>CComClassFactory:: LockServer —

Zwiększa i zmniejsza liczbę blokad modułu przez wywoływanie `_Module::Lock` i `_Module::Unlock`, odpowiednio.

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>Parametry

*Zarodowych*<br/>
podczas W przypadku wartości TRUE liczba blokad jest zwiększana; w przeciwnym razie licznik blokady jest zmniejszany.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

`_Module`odwołuje się do globalnego wystąpienia [CComModule](../../atl/reference/ccommodule-class.md) lub klasy pochodzącej od niej.

Wywołanie `LockServer` umożliwia klientowi przechowywanie w fabryce klasy, dzięki czemu można szybko tworzyć wiele obiektów.

## <a name="see-also"></a>Zobacz także

[Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
