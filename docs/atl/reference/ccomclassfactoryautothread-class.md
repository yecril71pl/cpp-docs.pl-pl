---
title: Klasa CComClassFactoryAutoThread | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread::CreateInstance
- ATLCOM/ATL::CComClassFactoryAutoThread::LockServer
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactoryAutoThread class
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 84d0d149c00024fab0d29ffc05d60270cb26741b
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054439"
---
# <a name="ccomclassfactoryautothread-class"></a>Klasa CComClassFactoryAutoThread

Ta klasa implementuje [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory) interfejs i umożliwia tworzenie w apartamentach wielu obiektów.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

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
|[CComClassFactoryAutoThread::CreateInstance](#createinstance)|Tworzy obiekt z określonym identyfikatorem CLSID.|
|[CComClassFactoryAutoThread::LockServer](#lockserver)|Blokuje fabryki klas w pamięci.|

## <a name="remarks"></a>Uwagi

`CComClassFactoryAutoThread` jest podobny do [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), ale pozwala na tworzenie w apartamentach wielu obiektów. Aby móc korzystać z tej obsługi, pochodzi z modułu EXE z [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Obiekty ATL zwykle uzyskać fabryki klas, wynikające z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Ta klasa zawiera makra [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), która deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako domyślnej fabryki klas. Aby użyć `CComClassFactoryAutoThread`, określ [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) makra w definicji klasy do obiektu. Na przykład:

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/ccomclassfactoryautothread-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

`CComClassFactoryAutoThread`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="createinstance"></a>  CComClassFactoryAutoThread::CreateInstance

Tworzy obiekt z określonym identyfikatorem CLSID i pobiera wskaźnik interfejsu do tego obiektu.

```
STDMETHODIMP CreateInstance(
    LPUNKNOWN pUnkOuter,
    REFIID riid,
    void** ppvObj);
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

### <a name="remarks"></a>Uwagi

Jeśli pochodzi od klasy modułu [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), `CreateInstance` wybiera pierwszy wątek do utworzenia obiektu w apartamentu skojarzone.

##  <a name="lockserver"></a>  CComClassFactoryAutoThread::LockServer

Zwiększa i zmniejsza liczbę blokad modułu, wywołując `_Module::Lock` i `_Module::Unlock`, odpowiednio.

```
STDMETHODIMP LockServer(BOOL fLock);
```

### <a name="parameters"></a>Parametry

*Stada*<br/>
[in] W przypadku opcji TRUE jest zwiększany liczbę blokad; w przeciwnym razie liczbę blokad zostanie zmniejszona.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Korzystając z `CComClassFactoryAutoThread`, `_Module` zazwyczaj odwołuje się do globalnego wystąpienia [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Wywoływanie `LockServer` umożliwia klientowi do zatrzymania się na fabrykę klas, umożliwiając szybkie tworzenie wielu obiektów.

## <a name="see-also"></a>Zobacz też

[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[Klasa CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)<br/>
[Klasa CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
