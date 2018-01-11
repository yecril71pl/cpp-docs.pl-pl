---
title: Klasa CComEnumImpl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComEnumImpl
- ATLCOM/ATL::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::CComEnumImpl
- ATLCOM/ATL::CComEnumImpl::Clone
- ATLCOM/ATL::CComEnumImpl::Init
- ATLCOM/ATL::CComEnumImpl::Next
- ATLCOM/ATL::CComEnumImpl::Reset
- ATLCOM/ATL::CComEnumImpl::Skip
- ATLCOM/ATL::CComEnumImpl::m_begin
- ATLCOM/ATL::CComEnumImpl::m_dwFlags
- ATLCOM/ATL::CComEnumImpl::m_end
- ATLCOM/ATL::CComEnumImpl::m_iter
- ATLCOM/ATL::CComEnumImpl::m_spUnk
dev_langs: C++
helpviewer_keywords: CComEnumImpl class
ms.assetid: cc0d8e76-e608-46db-87cd-4c7161fe32d2
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7cda4598f5d5b0e5b3dbca265066c8366cfd6d67
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ccomenumimpl-class"></a>Klasa CComEnumImpl
Ta klasa zawiera implementację interfejsu COM modułu wyliczającego przechowywania wyliczany elementów w tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Base,
    const IID* piid, class T, class Copy>  
class ATL_NO_VTABLE CComEnumImpl : public Base
```  
  
#### <a name="parameters"></a>Parametry  
 `Base`  
 Moduł wyliczający COM ( [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) interfejsu.  
  
 `piid`  
 Wskaźnik do Identyfikatora interfejsu interfejsu modułu wyliczającego.  
  
 `T`  
 Typ elementu udostępnianych przez interfejs modułu wyliczającego.  
  
 `Copy`  
 Jednorodnej [skopiuj klasy zasad](../../atl/atl-copy-policy-classes.md).  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComEnumImpl::CComEnumImpl](#ccomenumimpl)|Konstruktor.|  
|[CComEnumImpl:: ~ CComEnumImpl](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComEnumImpl::Clone](#clone)|Implementacja [IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx).|  
|[CComEnumImpl::Init](#init)|Inicjuje modułu wyliczającego.|  
|[CComEnumImpl::Next](#next)|Implementacja [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx).|  
|[CComEnumImpl::Reset](#reset)|Implementacja [IEnumXXXX::Reset](https://msdn.microsoft.com/library/ms693414.aspx).|  
|[CComEnumImpl::Skip](#skip)|Implementacja [IEnumXXXX::Skip](https://msdn.microsoft.com/library/ms690392.aspx).|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComEnumImpl::m_begin](#m_begin)|Wskaźnik do pierwszego elementu w tablicy.|  
|[CComEnumImpl::m_dwFlags](#m_dwflags)|Skopiuj flagi przekazywane za pośrednictwem `Init`.|  
|[CComEnumImpl::m_end](#m_end)|Wskaźnik lokalizacji bezpośrednio po ostatnim elemencie tablicy.|  
|[CComEnumImpl::m_iter](#m_iter)|Wskaźnik do bieżącego elementu w tablicy.|  
|[CComEnumImpl::m_spUnk](#m_spunk)|**IUnknown** wskaźnika obiektu podając wyliczany kolekcji.|  
  
## <a name="remarks"></a>Uwagi  
 `CComEnumImpl`udostępnia implementację dla interfejsu COM modułu wyliczającego przechowywania wyliczany elementów w tablicy. Ta klasa jest odpowiednikiem `IEnumOnSTLImpl` w kontenerze standardowa biblioteka C++ na podstawie klasy, która dostarcza implementację interfejsu modułu wyliczającego.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat dalszych różnic między `CComEnumImpl` i `IEnumOnSTLImpl`, zobacz [CComEnumImpl::Init](#init).  
  
 Zazwyczaj będzie *nie* należy utworzyć przez wynikających z tą implementacją interfejsu klasy modułu wyliczającego. Jeśli chcesz użyć dostarczonych ATL modułu wyliczającego na podstawie tablicy jest bardziej popularne, aby utworzyć wystąpienie [CComEnum](../../atl/reference/ccomenum-class.md).  
  
 Jednak jeśli konieczne jest zapewnienie niestandardowego modułu wyliczającego (na przykład taki, który udostępnia interfejsy oprócz interfejsu modułu wyliczającego), może dziedziczyć po tej klasie. W takiej sytuacji jest prawdopodobne, że należy zastąpić [CComEnumImpl::Clone](#clone) metodę do własnych implementacji.  
  
 Aby uzyskać więcej informacji, zobacz [kolekcje i wyliczenia ATL](../../atl/atl-collections-and-enumerators.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Base`  
  
 `CComEnumImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="ccomenumimpl"></a>CComEnumImpl::CComEnumImpl  
 Konstruktor.  
  
```
CComEnumImpl();
```  
  
##  <a name="dtor"></a>CComEnumImpl:: ~ CComEnumImpl  
 Destruktor.  
  
```
~CComEnumImpl();
```  
  
##  <a name="init"></a>CComEnumImpl::Init  
 Tej metody należy wywołać przed przekazaniem wskaźnik do interfejsu modułu wyliczającego do wszystkich klientów.  
  
```
HRESULT Init(
    T* begin,
    T* end,
    IUnknown* pUnk,
    CComEnumFlags flags = AtlFlagNoCopy);
```  
  
### <a name="parameters"></a>Parametry  
 *Rozpocznij*  
 Wskaźnik do pierwszego elementu obiektu tablicę zawierającą elementy, które mają zostać wyliczone.  
  
 `end`  
 Wskaźnik lokalizacji bezpośrednio po ostatnim elemencie tablicy zawierającej elementy, które mają zostać wyliczone.  
  
 *pUnk*  
 [in] **IUnknown** wskaźnika obiektu, który musi być aktywne przez cały okres istnienia modułu wyliczającego. Przekaż **NULL** Jeśli nie istnieje żaden taki obiekt.  
  
 `flags`  
 Flagi określające, czy moduł wyliczający powinna przejąć na własność tablicy lub wykonaj jego kopię. Możliwe wartości są opisane poniżej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Tylko jeden raz wywołać tę metodę — Inicjowanie modułu wyliczającego, użyj go, a następnie jej wyrzucać.  
  
 Jeśli przekazujesz wskaźników do elementów w tablicy przechowywany w innym obiekcie (i nie pytaj modułu wyliczającego, aby skopiować dane), możesz użyć *pUnk* parametr, aby upewnić się, że obiekt a tablica posiada są dostępne dla tak długo, jak moduł wyliczający należy je. Moduł wyliczający zawiera po prostu odwołania COM na obiekt, aby go podtrzymywania. Odwołanie COM jest wydawane automatycznie, gdy moduł wyliczający zostanie zniszczony.  
  
 `flags` Parametr umożliwia określenie, jak moduł wyliczający powinny traktować przekazany do niego elementów tablicy. `flags`można wykonać jedną z wartości z **CComEnumFlags** wyliczenie pokazano poniżej:  
  
```  
enum CComEnumFlags  
   {  
   AtlFlagNoCopy = 0,  
   AtlFlagTakeOwnership = 2, // BitOwn  
   AtlFlagCopy = 3           // BitOwn | BitCopy  
   };  
```  
  
 **AtlFlagNoCopy** oznacza, że okres istnienia tablicy nie są kontrolowane przez moduł wyliczający. W takim przypadku albo tablicy będzie static lub obiekt identyfikowane przez *pUnk* będzie odpowiedzialna za zwalnianie tablicy nie jest już potrzebne.  
  
 **AtlFlagTakeOwnership** oznacza, że zniszczenie tablicy jest kontrolowany przez moduł wyliczający. W takim przypadku tablicy musi dynamicznie przydzielono za pomocą **nowe**. Moduł wyliczający spowoduje usunięcie tablicy w jego destruktora. Zazwyczaj przejdzie **NULL** dla *pUnk*, mimo że nadal można przekazać prawidłowego wskaźnika, jeśli chcesz otrzymywać powiadomienia o zniszczenie modułu wyliczającego jakiegoś powodu.  
  
 **AtlFlagCopy** oznacza, że nowe tablicy ma być utworzony przez skopiowanie Tablica przekazana do `Init`. Okres istnienia nowej tablicy jest kontrolowany przez moduł wyliczający. Moduł wyliczający spowoduje usunięcie tablicy w jego destruktora. Zazwyczaj przejdzie **NULL** dla *pUnk*, mimo że nadal można przekazać prawidłowego wskaźnika, jeśli chcesz otrzymywać powiadomienia o zniszczenie modułu wyliczającego jakiegoś powodu.  
  
> [!NOTE]
>  Prototyp ta metoda określa elementy tablicy jako typu **T**, gdzie **T** został zdefiniowany jako parametr szablonu do klasy. Jest to ten sam typ uwidocznionego za pomocą metody interfejsu COM [CComEnumImpl::Next](#next). Wpływ na tego jest fakt, że w przeciwieństwie do [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md), ta klasa nie obsługuje innego magazynu i udostępniany typów danych. Typ danych elementów w tablicy musi być taki sam jak typ danych udostępniane za pomocą interfejsu COM.  
  
##  <a name="clone"></a>CComEnumImpl::Clone  
 Ta metoda zapewnia implementacji [IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx) metody poprzez utworzenie obiektu typu `CComEnum`, inicjowanie go przy użyciu tej samej tablicy i iteratora używane przez bieżący obiekt i zwracanie na interfejsie nowo utworzony obiekt.  
  
```
STDMETHOD(Clone)(Base** ppEnum);
```  
  
### <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Interfejs modułu wyliczającego na nowo utworzony obiekt sklonować z bieżącego modułu wyliczającego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, że sklonowany moduły wyliczające nie należy wprowadzać ich własnych kopiowania (lub Przejmij na własność) dane używane przez oryginalnego modułu wyliczającego. W razie potrzeby sklonowany moduły wyliczające będzie podtrzymywania oryginalnego modułu wyliczającego (przy użyciu odwołania COM) aby upewnić się, że dane są dostępne dla tak długo, jak potrzebują.  
  
##  <a name="m_spunk"></a>CComEnumImpl::m_spUnk  
 This, wskaźnik inteligentny obsługuje odwołania na obiekt przekazany do [CComEnumImpl::Init](#init), zapewniając, że pozostaje aktywne przez cały okres istnienia modułu wyliczającego.  
  
```
CComPtr<IUnknown> m_spUnk;
```  
  
##  <a name="m_begin"></a>CComEnumImpl::m_begin  
 Wskaźnik lokalizacji bezpośrednio po ostatnim elemencie tablicy zawierającej elementy, które mają zostać wyliczone.  
  
```
T* m_begin;
```  
  
##  <a name="m_end"></a>CComEnumImpl::m_end  
 Wskaźnik do pierwszego elementu obiektu tablicę zawierającą elementy, które mają zostać wyliczone.  
  
```
T* m_end;
```  
  
##  <a name="m_iter"></a>CComEnumImpl::m_iter  
 Wskaźnik do bieżącego elementu tablicę zawierającą elementy, które mają zostać wyliczone.  
  
```
T* m_iter;
```  
  
##  <a name="m_dwflags"></a>CComEnumImpl::m_dwFlags  
 Flagi przekazywane do [CComEnumImpl::Init](#init).  
  
```
DWORD m_dwFlags;
```  
  
##  <a name="next"></a>CComEnumImpl::Next  
 Ta metoda zapewnia implementacji [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx) metody.  
  
```
STDMETHOD(Next)(ULONG celt, T* rgelt, ULONG* pceltFetched);
```  
  
### <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba elementów żądanie.  
  
 `rgelt`  
 [out] Tablica ma zostać wypełniony z elementami.  
  
 `pceltFetched`  
 [out] Liczba elementów w rzeczywistości zwracane w `rgelt`. Może to być mniejsza niż `celt` Jeśli mniej niż `celt` elementy pozostają na liście.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
##  <a name="reset"></a>CComEnumImpl::Reset  
 Ta metoda zapewnia implementacji [IEnumXXXX::Reset](https://msdn.microsoft.com/library/ms693414.aspx) metody.  
  
```
STDMETHOD(Reset)(void);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
##  <a name="skip"></a>CComEnumImpl::Skip  
 Ta metoda zapewnia implementacji [IEnumXXXX::Skip](https://msdn.microsoft.com/library/ms690392.aspx) metody.  
  
```
STDMETHOD(Skip)(ULONG celt);
```  
  
### <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba elementów do pominięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca E_INVALIDARG, jeśli `celt` wynosi zero, zwraca wartości S_FALSE, jeśli mniej niż `celt` elementy są zwracane, w przeciwnym razie zwraca wartość S_OK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)   
 [Klasa CComEnum](../../atl/reference/ccomenum-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
