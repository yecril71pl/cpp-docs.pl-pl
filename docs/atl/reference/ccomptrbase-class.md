---
title: Klasa CComPtrBase | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase::Advise
- ATLCOMCLI/ATL::CComPtrBase::Attach
- ATLCOMCLI/ATL::CComPtrBase::CoCreateInstance
- ATLCOMCLI/ATL::CComPtrBase::CopyTo
- ATLCOMCLI/ATL::CComPtrBase::Detach
- ATLCOMCLI/ATL::CComPtrBase::IsEqualObject
- ATLCOMCLI/ATL::CComPtrBase::QueryInterface
- ATLCOMCLI/ATL::CComPtrBase::Release
- ATLCOMCLI/ATL::CComPtrBase::SetSite
- ATLCOMCLI/ATL::CComPtrBase::p
dev_langs:
- C++
helpviewer_keywords:
- CComPtrBase class
ms.assetid: 6dbe9543-dee8-4a97-b02f-dd3a25f4a1a0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f0d9b4d49a7568df905a595e2cf6494b2b98706d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ccomptrbase-class"></a>Klasa CComPtrBase
Ta klasa stanowi podstawę dla klas wskaźnika inteligentnego przy użyciu procedury oparte na modelu COM pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>  
class CComPtrBase
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ obiektu do odwoływać się wskaźnika inteligentnego.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComPtrBase:: ~ CComPtrBase](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComPtrBase::Advise](#advise)|Wywołanie tej metody, aby utworzyć połączenie między `CComPtrBase`przez punkt połączenia i odbiorczy klienta.|  
|[CComPtrBase::Attach](#attach)|Wywołaj tę metodę, aby przejąć na własność istniejącego wskaźnika.|  
|[CComPtrBase::CoCreateInstance](#cocreateinstance)|Wywołanie tej metody, aby utworzyć obiekt klasy skojarzone z określonym identyfikator klasy lub identyfikator programu.|  
|[CComPtrBase::CopyTo](#copyto)|Wywołanie tej metody, aby skopiować `CComPtrBase` wskaźnika do innej zmiennej wskaźnika.|  
|[CComPtrBase::Detach](#detach)|Wywołanie tej metody, aby zwolnić własność wskaźnika.|  
|[CComPtrBase::IsEqualObject](#isequalobject)|Wywołanie tej metody, aby sprawdzić, czy określony **IUnknown** punktów do tego samego obiektu skojarzone z `CComPtrBase` obiektu.|  
|[CComPtrBase::QueryInterface](#queryinterface)|Wywołaj tę metodę w celu zwraca wskaźnik do określonego interfejsu.|  
|[CComPtrBase::Release](#release)|Wywołanie tej metody, aby zwolnić interfejsu.|  
|[CComPtrBase::SetSite](#setsite)|Wywołanie tej metody, aby ustawić lokacji z `CComPtrBase` do obiektu **IUnknown** obiektu nadrzędnego.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComPtrBase::operator T *](#operator_t_star)|Operator rzutowania.|  
|[CComPtrBase::operator!](#operator_not)|NOT operator.|  
|[CComPtrBase::operator &](#operator_amp)|& — Operator.|  
|[CComPtrBase::operator *](#operator_star)|* — Operator.|  
|[CComPtrBase::operator <](#ccomptrbase__operator lt)|Less — niż operator.|  
|[CComPtrBase::operator ==](#operator_eq_eq)|Operator równości.|  
|[CComPtrBase::operator ->](#operator_ptr)|Operator wskaźników do elementów członkowskich.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComPtrBase::p](#p)|Zmienna elementu członkowskiego danych wskaźnika.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa stanowi podstawę dla innych wskaźniki inteligentne, korzystających z procedury zarządzania pamięci dla modelu COM, takie jak [CComQIPtr](../../atl/reference/ccomqiptr-class.md) i [CComPtr](../../atl/reference/ccomptr-class.md). Klasy pochodne dodać własne konstruktory i operatory, ale są oparte na metodach udostępniane przez `CComPtrBase`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcomcli.h  
  
##  <a name="advise"></a>CComPtrBase::Advise  
 Wywołanie tej metody, aby utworzyć połączenie między `CComPtrBase`przez punkt połączenia i odbiorczy klienta.  
  
```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *pUnk*  
 Wskaźnik do klienta **IUnknown**.  
  
 `iid`  
 Identyfikator GUID punktu połączenia. Zazwyczaj jest to ten sam interfejs wychodzących, zarządzane przez punkt połączenia.  
  
 `pdw`  
 Wskaźnik do pliku cookie, który unikatowo identyfikuje połączenie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [AtlAdvise](connection-point-global-functions.md#atladvise) Aby uzyskać więcej informacji.  
  
##  <a name="attach"></a>CComPtrBase::Attach  
 Wywołaj tę metodę, aby przejąć na własność istniejącego wskaźnika.  
  
```
void Attach(T* p2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p2`  
 `CComPtrBase` Obiektu będzie przejąć na własność ten wskaźnik.  
  
### <a name="remarks"></a>Uwagi  
 **Dołącz** wywołania [CComPtrBase::Release](#release) na istniejące [CComPtrBase::p](#p) zmiennej członkowskiej, a następnie przypisuje `p2` do `CComPtrBase::p`. Gdy `CComPtrBase` obiektu przejmuje wskaźnik, automatycznie wywoła `Release` na wskaźniku, co spowoduje usunięcie wskaźnika i wszystkie przydzielone danych, 0 Jeśli liczba odwołań do obiektu.  
  
##  <a name="dtor"></a>CComPtrBase:: ~ CComPtrBase  
 Destruktor.  
  
```
~CComPtrBase() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Udostępnia interfejs wskazywana przez `CComPtrBase`.  
  
##  <a name="cocreateinstance"></a>CComPtrBase::CoCreateInstance  
 Wywołanie tej metody, aby utworzyć obiekt klasy skojarzone z określonym identyfikator klasy lub identyfikator programu.  
  
```
HRESULT CoCreateInstance(  
    LPCOLESTR szProgID,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();

HRESULT CoCreateInstance(  
    REFCLSID rclsid,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `szProgID`  
 Wskaźnik do ProgID, używane do odzyskiwania identyfikatora CLSID.  
  
 `pUnkOuter`  
 Jeśli **NULL**, wskazuje, że obiekt jest nie utworzony jako część agregacji. Jeśli z systemem innym niż **NULL**, jest wskaźnik do obiektu agregacji **IUnknown** interfejsu (kontrolowanie **IUnknown**).  
  
 `dwClsContext`  
 Kontekst, w którym będzie uruchamiany kod, który zarządza nowo utworzony obiekt.  
  
 `rclsid`  
 Identyfikatora CLSID skojarzonego z danymi i kod, który będzie używany do utworzenia obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK sukces, lub REGDB_E_CLASSNOTREG, CLASS_E_NOAGGREGATION, CO_E_CLASSSTRING lub E_NOINTERFACE w przypadku awarii. Zobacz [CoCreateClassInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615) i [CLSIDFromProgID](http://msdn.microsoft.com/library/windows/desktop/ms688386) opis tych błędów.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli pierwszy formularz metoda jest wywoływana, [CLSIDFromProgID](http://msdn.microsoft.com/library/windows/desktop/ms688386) służy do odzyskania identyfikatora CLSID. Następnie wywołaj zarówno formularzy [CoCreateClassInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).  
  
 W kompilacjach debugowania, wystąpi błąd potwierdzenia Jeśli [CComPtrBase::p](#p) nie jest równa NULL.  
  
##  <a name="copyto"></a>CComPtrBase::CopyTo  
 Wywołanie tej metody, aby skopiować `CComPtrBase` wskaźnika do innej zmiennej wskaźnika.  
  
```
HRESULT CopyTo(T** ppT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *ppT*  
 Adres zmiennej, która otrzyma `CComPtrBase` wskaźnika.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia E_POINTER w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Kopie `CComPtrBase` wskaźnik do *ppT*. Odwołanie count [CComPtrBase::p](#p) zmiennej członkowskiej jest zwiększany.  
  
 Błąd HRESULT zostanie zwrócony, jeśli *ppT* jest równa NULL. W kompilacjach debugowania, wystąpi błąd potwierdzenia Jeśli *ppT* jest równa NULL.  
  
##  <a name="detach"></a>CComPtrBase::Detach  
 Wywołanie tej metody, aby zwolnić własność wskaźnika.  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca kopię wskaźnika.  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia własność wskaźnik, ustawia [CComPtrBase::p](#p) danych zmiennej członkowskiej na wartość NULL i zwraca kopię wskaźnika.  
  
##  <a name="isequalobject"></a>CComPtrBase::IsEqualObject  
 Wywołanie tej metody, aby sprawdzić, czy określony **IUnknown** punktów do tego samego obiektu skojarzone z `CComPtrBase` obiektu.  
  
```
bool IsEqualObject(IUnknown* pOther) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pOther`  
 **IUnknown \***  do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli obiekty są identyczne, wartość false w przeciwnym razie wartość.  
  
##  <a name="operator_not"></a>CComPtrBase::operator!  
 NOT operator.  
  
```
bool operator!() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true, jeśli `CComHeapPtr` wskaźnika jest równa NULL, wartość false w przeciwnym razie wartość.  
  
##  <a name="operator_amp"></a>CComPtrBase::operator&amp;  
 & — Operator.  
  
```
T** operator&() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca adres wskazywanego przez obiekt `CComPtrBase` obiektu.  
  
##  <a name="operator_star"></a>CComPtrBase::operator *  
 * — Operator.  
  
```
T& operator*() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość [CComPtrBase::p](#p); oznacza to, że wskaźnik do obiektu odwołuje się `CComPtrBase` obiektu.  
  
 Jeśli wydajność debugowania kompilacji, potwierdzenia, wystąpi błąd Jeśli [CComPtrBase::p](#p) nie jest równa NULL.  
  
##  <a name="operator_eq_eq"></a>CComPtrBase::operator ==  
 Operator równości.  
  
```
bool operator== (T* pT) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *pT*  
 Wskaźnik do obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość true, jeśli `CComPtrBase` i *pT* wskazywać tego samego obiektu false w przeciwnym razie wartość.  
  
##  <a name="operator_ptr"></a>CComPtrBase::operator-&gt;  

 Operator wskaźnika do elementu członkowskiego.  
  
```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość [CComPtrBase::p](#p) zmiennej członka danych.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego operatora, aby wywołać metodę w klasie wskazywana przez `CComPtrBase` obiektu. W kompilacjach do debugowania błędu potwierdzenia wystąpi, jeśli `CComPtrBase` element członkowski danych wskazuje na wartość NULL.  
  
##  <a name="operator_lt"></a>CComPtrBase::operator&lt;  
 Less — niż operator.  
  
```
bool operator<(T* pT) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *pT*  
 Wskaźnik do obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli wskaźnik jest zarządzany przez bieżący obiekt jest mniejszy niż wskaźnika, które są porównywane.  
  
##  <a name="operator_t_star"></a>CComPtrBase::operator T *  
 Operator rzutowania.  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwraca wskaźnik do typu danych obiektu zdefiniowaną w szablonie klasy.  
  
##  <a name="p"></a>CComPtrBase::p  
 Zmienna elementu członkowskiego danych wskaźnika.  
  
```
T* p;
```  
  
### <a name="remarks"></a>Uwagi  
 Ta zmienna elementu członkowskiego zawiera informacje wskaźnika.  
  
##  <a name="queryinterface"></a>CComPtrBase::QueryInterface  
 Wywołaj tę metodę w celu zwraca wskaźnik do określonego interfejsu.  
  
```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `Q`  
 Typ obiektu, którego wskaźnika interfejsu jest wymagana.  
  
 `pp`  
 Adres zmiennej danych wyjściowych, która odbiera wskaźnika żądanego interfejsu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK na powodzenie lub E_NOINTERFACE w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wywołuje [IUnknown::QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521).  
  
 W kompilacjach debugowania, wystąpi błąd potwierdzenia Jeśli *PZ* nie jest równa NULL.  
  
##  <a name="release"></a>CComPtrBase::Release  
 Wywołanie tej metody, aby zwolnić interfejsu.  
  
```
void Release() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Interfejs wydaniu i [CComPtrBase::p](#p) jest równa NULL.  
  
##  <a name="setsite"></a>CComPtrBase::SetSite  
 Wywołanie tej metody, aby ustawić lokacji z `CComPtrBase` do obiektu **IUnknown** obiektu nadrzędnego.  
  
```
HRESULT SetSite(IUnknown* punkParent) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `punkParent`  
 Wskaźnik do **IUnknown** interfejsu elementu nadrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wywołuje [AtlSetChildSite](composite-control-global-functions.md#atlsetchildsite).  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
