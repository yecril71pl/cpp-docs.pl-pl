---
title: Klasa IEnumOnSTLImpl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 38d645f7841cb71af9812bd1d62a979752a0343d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ienumonstlimpl-class"></a>Klasa IEnumOnSTLImpl
Ta klasa definiuje interfejs modułu wyliczającego oparte na kolekcji standardowa biblioteka C++.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>  
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```  
  
#### <a name="parameters"></a>Parametry  
 `Base`  
 Moduł wyliczający COM ( [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) interfejsu.  
  
 `piid`  
 Wskaźnik do Identyfikatora interfejsu interfejsu modułu wyliczającego.  
  
 `T`  
 Typ elementu udostępnianych przez interfejs modułu wyliczającego.  
  
 `Copy`  
 A [skopiuj klasy zasad](../../atl/atl-copy-policy-classes.md).  
  
 `CollType`  
 Klasa standardowa biblioteka C++ kontenera.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IEnumOnSTLImpl::Clone](#clone)|Implementacja [IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx).|  
|[IEnumOnSTLImpl::Init](#init)|Inicjuje modułu wyliczającego.|  
|[IEnumOnSTLImpl::Next](#next)|Implementacja [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx).|  
|[IEnumOnSTLImpl::Reset](#reset)|Implementacja [IEnumXXXX::Reset](https://msdn.microsoft.com/library/ms693414.aspx).|  
|[IEnumOnSTLImpl::Skip](#skip)|Implementacja [IEnumXXXX::Skip](https://msdn.microsoft.com/library/ms690392.aspx).|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IEnumOnSTLImpl::m_iter](#m_iter)|Iterator reprezentujący element wyliczający bieżącą pozycję w kolekcji.|  
|[IEnumOnSTLImpl::m_pcollection](#m_pcollection)|Wskaźnik do kontenera standardowa biblioteka C++ zawierający elementy, które mają zostać wyliczone.|  
|[IEnumOnSTLImpl::m_spUnk](#m_spunk)|**IUnknown** wskaźnika obiektu podając kolekcji.|  
  
## <a name="remarks"></a>Uwagi  
 `IEnumOnSTLImpl`udostępnia implementację dla interfejsu COM modułu wyliczającego przechowywania wyliczany elementów w kontenerze zgodnej biblioteki C++ Standard. Ta klasa jest odpowiednikiem [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md) klasy, która dostarcza implementację interfejsu modułu wyliczającego na podstawie tablicy.  
  
> [!NOTE]
>  Zobacz [CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init) szczegółowe informacje na temat dalszych różnice między `CComEnumImpl` i `IEnumOnSTLImpl`.  
  
 Zazwyczaj będzie *nie* należy utworzyć przez wynikających z tą implementacją interfejsu klasy modułu wyliczającego. Jeśli chcesz użyć dostarczonych ATL modułu wyliczającego oparte na kontenera standardowa biblioteka C++ jest bardziej popularne, aby utworzyć wystąpienie [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md), lub można utworzyć klasy kolekcji, która zwraca moduł wyliczający przez wynikających z [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md).  
  
 Jednak jeśli konieczne jest zapewnienie niestandardowego modułu wyliczającego (na przykład taki, który udostępnia interfejsy oprócz interfejsu modułu wyliczającego), może dziedziczyć po tej klasie. W tej sytuacji jest prawdopodobne, że należy zastąpić [klonowania](#clone) metodę do własnych implementacji.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Base`  
  
 `IEnumOnSTLImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="init"></a>IEnumOnSTLImpl::Init  
 Inicjuje modułu wyliczającego.  
  
```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```  
  
### <a name="parameters"></a>Parametry  
 `pUnkForRelease`  
 [in] **IUnknown** wskaźnika obiektu, który musi być aktywne przez cały okres istnienia modułu wyliczającego. Przekaż **NULL** Jeśli nie istnieje żaden taki obiekt.  
  
 `collection`  
 Odwołanie do kontenera standardowa biblioteka C++, który zawiera elementy, które mają zostać wyliczone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku przekazania `Init` odwołania do kolekcji przechowywany w innym obiekcie, można użyć `pUnkForRelease` parametr Sprawdź, czy obiekt i kolekcji posiada, jest dostępna dla tak długo, jak moduł wyliczający wymaga on.  
  
 Tej metody należy wywołać przed przekazaniem wskaźnik do interfejsu modułu wyliczającego do wszystkich klientów.  
  
##  <a name="clone"></a>IEnumOnSTLImpl::Clone  
 Ta metoda zapewnia implementacji [IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx) metody poprzez utworzenie obiektu typu `CComEnumOnSTL`, inicjowanie go przy użyciu tej samej kolekcji i iteratora używane przez bieżący obiekt i zwracanie na interfejsie nowo utworzony obiekt.  
  
```
STDMETHOD(Clone)(Base** ppEnum);
```  
  
### <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Interfejs modułu wyliczającego na nowo utworzony obiekt sklonować z bieżącego modułu wyliczającego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
##  <a name="m_spunk"></a>IEnumOnSTLImpl::m_spUnk  
 **IUnknown** wskaźnika obiektu podając kolekcji.  
  
```
CComPtr<IUnknown> m_spUnk;
```  
  
### <a name="remarks"></a>Uwagi  
 This, wskaźnik inteligentny obsługuje odwołania na obiekt przekazany do [IEnumOnSTLImpl::Init](#init), zapewniając, że pozostaje aktywne przez cały okres istnienia modułu wyliczającego.  
  
##  <a name="m_pcollection"></a>IEnumOnSTLImpl::m_pcollection  
 Ten element członkowski punktów do kolekcji, która dostarcza dane kierowania implementacji interfejsu modułu wyliczającego.  
  
```
CollType* m_pcollection;
```  
  
### <a name="remarks"></a>Uwagi  
 Ten element członkowski jest inicjowany przez wywołanie [IEnumOnSTLImpl::Init](#init).  
  
##  <a name="m_iter"></a>IEnumOnSTLImpl::m_iter  
 Ten element członkowski przechowuje iteratora używane, aby oznaczyć bieżącą pozycję w kolekcji i przechodzić do kolejnych elementów.  
  
```
CollType::iterator m_iter;
```  
  
##  <a name="next"></a>IEnumOnSTLImpl::Next  
 Ta metoda zapewnia implementacji [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx) metody.  
  
```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```  
  
### <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba elementów żądanie.  
  
 `rgelt`  
 [out] Tablica wypełnia się elementów.  
  
 `pceltFetched`  
 [out] Liczba elementów w rzeczywistości zwracane w `rgelt`. Może to być mniejsza niż `celt` Jeśli mniej niż `celt` elementy pozostają na liście.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
##  <a name="reset"></a>IEnumOnSTLImpl::Reset  
 Ta metoda zapewnia implementacji [IEnumXXXX::Reset](https://msdn.microsoft.com/library/ms693414.aspx) metody.  
  
```
STDMETHOD(Reset)(void);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
##  <a name="skip"></a>IEnumOnSTLImpl::Skip  
 Ta metoda zapewnia implementacji [IEnumXXXX::Skip](https://msdn.microsoft.com/library/ms690392.aspx) metody.  
  
```
STDMETHOD(Skip)(ULONG celt);
```  
  
### <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba elementów do pominięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
