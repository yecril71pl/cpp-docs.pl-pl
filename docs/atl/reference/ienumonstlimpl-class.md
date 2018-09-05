---
title: Klasa IEnumOnSTLImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl::Clone
- ATLCOM/ATL::IEnumOnSTLImpl::Init
- ATLCOM/ATL::IEnumOnSTLImpl::Next
- ATLCOM/ATL::IEnumOnSTLImpl::Reset
- ATLCOM/ATL::IEnumOnSTLImpl::Skip
- ATLCOM/ATL::IEnumOnSTLImpl::m_iter
- ATLCOM/ATL::IEnumOnSTLImpl::m_pcollection
- ATLCOM/ATL::IEnumOnSTLImpl::m_spUnk
dev_langs:
- C++
helpviewer_keywords:
- IEnumOnSTLImpl class
ms.assetid: 1789e77b-88b8-447d-a490-806b918912ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4f2e448d5fa73c64e9abb66ef70e513bc9fa0728
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43759249"
---
# <a name="ienumonstlimpl-class"></a>Klasa IEnumOnSTLImpl

Ta klasa definiuje interfejs moduł wyliczający na podstawie kolekcji standardowej biblioteki języka C++.

## <a name="syntax"></a>Składnia

```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>  
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```

#### <a name="parameters"></a>Parametry

*podstawowy*  
Moduł wyliczający COM. Zobacz [IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring) przykład.

*piid*  
Wskaźnik do Identyfikatora interfejsu interfejsu modułu wyliczającego.

*T*  
Typ elementu udostępnianych przez interfejs modułu wyliczającego.

*Kopiuj*  
A [kopiowania klasy zasad](../../atl/atl-copy-policy-classes.md).

*CollType*  
Klasa kontenera standardowej biblioteki języka C++.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IEnumOnSTLImpl::Clone](#clone)|Implementacja **klonowania**.|
|[IEnumOnSTLImpl::Init](#init)|Inicjuje modułu wyliczającego.|
|[IEnumOnSTLImpl::Next](#next)|Implementacja **dalej**.|
|[IEnumOnSTLImpl::Reset](#reset)|Implementacja **resetowania**.|
|[IEnumOnSTLImpl::Skip](#skip)|Implementacja **Pomiń**.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[IEnumOnSTLImpl::m_iter](#m_iter)|Iterator, który reprezentuje moduł wyliczający bieżącej pozycji w kolekcji.|
|[IEnumOnSTLImpl::m_pcollection](#m_pcollection)|Wskaźnik do standardowej biblioteki języka C++ pojemnik elementów do wyliczenia.|
|[IEnumOnSTLImpl::m_spUnk](#m_spunk)|`IUnknown` Wskaźnika obiektu podając kolekcji.|

## <a name="remarks"></a>Uwagi

`IEnumOnSTLImpl` udostępnia implementację dla interfejsu modułu wyliczającego COM przechowywania elementów wyliczany w kontenerze C++ Standard zgodnym z biblioteki. Ta klasa jest odpowiednikiem [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md) klasy, która dostarcza implementację interfejsu modułu wyliczającego na podstawie tablicy.

> [!NOTE]
>  Zobacz [CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init) szczegółowe informacje na temat dalszych różnice między `CComEnumImpl` i `IEnumOnSTLImpl`.

Zazwyczaj będzie *nie* musisz utworzyć własne klasy modułu wyliczającego, wynikających z tej implementacji interfejsu. Jeśli chcesz użyć moduł wyliczający dostarczony ATL oparta na kontenerze standardowej biblioteki języka C++ jest bardziej powszechne, aby utworzyć wystąpienie [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md), lub utworzyć klasy kolekcji, która zwraca moduł wyliczający, wynikające z [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md).

Jednakże jeśli musisz podać niestandardowy moduł wyliczający, (na przykład taki, który uwidacznia interfejsy oprócz interfejsu modułu wyliczającego), może pochodzić z tej klasy. W tej sytuacji jest prawdopodobne, że musisz przesłonić [klonowania](#clone) metody w celu zapewnienia Twojej własnej implementacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Base`

`IEnumOnSTLImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

##  <a name="init"></a>  IEnumOnSTLImpl::Init

Inicjuje modułu wyliczającego.

```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```

### <a name="parameters"></a>Parametry

*pUnkForRelease*  
[in] `IUnknown` Wskaźnika obiektu, który musi znajdować się aktywne w okresie istnienia modułu wyliczającego. Przekaż wartość NULL, jeśli taki obiekt nie istnieje.

*Kolekcja*  
Odwołanie do kontenera standardowej biblioteki języka C++, który zawiera elementy do wyliczenia.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

W przypadku przekazania `Init` odwołania do kolekcji, która odbyła się w innym obiekcie, możesz użyć *pUnkForRelease* parametru, aby upewnij się, że obiekt i kolekcja przechowuje, dostępne dla tak długo, jak moduł wyliczający ich potrzebuje.

Tę metodę należy wywołać przed przekazaniem wskaźnik do interfejsu modułu wyliczającego do wszystkich klientów.

##  <a name="clone"></a>  IEnumOnSTLImpl::Clone

Ta metoda zapewnia wykonania **klonowania** metoda przez utworzenie obiektu typu `CComEnumOnSTL`, inicjując go przy użyciu tej samej kolekcji i używane przez bieżący obiekt iteratora i zwraca interfejs na nowo utworzony obiekt.

```
STDMETHOD(Clone)(Base** ppEnum);
```

### <a name="parameters"></a>Parametry

*ppEnum*  
[out] Sklonowany interfejsu modułu wyliczającego na nowo utworzony obiekt z bieżącego modułu wyliczającego.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

##  <a name="m_spunk"></a>  IEnumOnSTLImpl::m_spUnk

`IUnknown` Wskaźnika obiektu podając kolekcji.

```
CComPtr<IUnknown> m_spUnk;
```

### <a name="remarks"></a>Uwagi

To inteligentny wskaźnik obsługuje odwołania na obiekt przekazany do [IEnumOnSTLImpl::Init](#init), zapewniając, że pozostaje aktywne w okresie istnienia modułu wyliczającego.

##  <a name="m_pcollection"></a>  IEnumOnSTLImpl::m_pcollection

Wskazuje ten element członkowski kolekcji, która udostępnia dane kierowania implementacji interfejsu modułu wyliczającego.

```
CollType* m_pcollection;
```

### <a name="remarks"></a>Uwagi

Ten element członkowski jest inicjowany przez wywołanie [IEnumOnSTLImpl::Init](#init).

##  <a name="m_iter"></a>  IEnumOnSTLImpl::m_iter

Ten element członkowski przechowuje iterator używany do oznaczania bieżącej pozycji w kolekcji, a następnie przejdź do kolejnych elementów.

```
CollType::iterator m_iter;
```

##  <a name="next"></a>  IEnumOnSTLImpl::Next

Ta metoda zapewnia wykonania **dalej** metody.

```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```

### <a name="parameters"></a>Parametry

*celt*  
[in] Liczba elementów żądanie.

*rgelt*  
[out] Tablica, która ma zostać wypełniony przy użyciu elementów.

*pceltFetched*  
[out] Liczba elementów, które faktycznie są zwracane w *rgelt*. Może to być mniejszy niż *celt* Jeśli mniej niż *celt* elementy pozostają na liście.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

##  <a name="reset"></a>  IEnumOnSTLImpl::Reset

Ta metoda zapewnia wykonania **resetowania** metody.

```
STDMETHOD(Reset)(void);
```

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

##  <a name="skip"></a>  IEnumOnSTLImpl::Skip

Ta metoda zapewnia wykonania **Pomiń** metody.

```
STDMETHOD(Skip)(ULONG celt);
```

### <a name="parameters"></a>Parametry

*celt*  
[in] Liczba elementów do pominięcia.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../../atl/atl-class-overview.md)
