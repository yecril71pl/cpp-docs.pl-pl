---
title: Klasa IDataObjectImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl
- ATLCTL/ATL::IDataObjectImpl::DAdvise
- ATLCTL/ATL::IDataObjectImpl::DUnadvise
- ATLCTL/ATL::IDataObjectImpl::EnumDAdvise
- ATLCTL/ATL::IDataObjectImpl::EnumFormatEtc
- ATLCTL/ATL::IDataObjectImpl::FireDataChange
- ATLCTL/ATL::IDataObjectImpl::GetCanonicalFormatEtc
- ATLCTL/ATL::IDataObjectImpl::GetData
- ATLCTL/ATL::IDataObjectImpl::GetDataHere
- ATLCTL/ATL::IDataObjectImpl::QueryGetData
- ATLCTL/ATL::IDataObjectImpl::SetData
dev_langs:
- C++
helpviewer_keywords:
- data transfer [C++]
- data transfer [C++], Uniform Data Transfer
- IDataObjectImpl class
- IDataObject, ATL implementation
ms.assetid: b680f0f7-7795-40a1-a0f6-f48768201c89
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a3ffcdd8cc8320b2534d928171fe75619062b300
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="idataobjectimpl-class"></a>Klasa IDataObjectImpl
Ta klasa zawiera metody pomocnicze Uniform transferu danych i zarządzanie połączeniami.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>  
class IDataObjectImpl
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `IDataObjectImpl`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IDataObjectImpl::DAdvise](#dadvise)|Ustanawia połączenie między obiektem danych i odbiorczy porada. Dzięki temu zbiornika Porada otrzymywać powiadomienia o zmianach w obiekcie.|  
|[IDataObjectImpl::DUnadvise](#dunadvise)|Przerywa połączenie wcześniej ustanowione za pośrednictwem `DAdvise`.|  
|[IDataObjectImpl::EnumDAdvise](#enumdadvise)|Tworzy moduł wyliczający do iteracji bieżących połączeń advisory.|  
|[IDataObjectImpl::EnumFormatEtc](#enumformatetc)|Tworzy moduł wyliczający do iteracji **FORMATETC** struktury obsługiwane przez obiekt danych. Zwraca implementację ATL **E_NOTIMPL**.|  
|[IDataObjectImpl::FireDataChange](#firedatachange)|Wysyła powiadomienia o zmianach z powrotem do każdej Porada ujścia.|  
|[IDataObjectImpl::GetCanonicalFormatEtc](#getcanonicalformatetc)|Pobiera logicznie równoważne **FORMATETC** struktury, który jest bardziej złożony. Zwraca implementację ATL **E_NOTIMPL**.|  
|[IDataObjectImpl::GetData](#getdata)|Przesyła dane z obiektem danych do klienta. Dane są opisane w **FORMATETC** struktury i są przesyłane za pośrednictwem **STGMEDIUM** struktury.|  
|[IDataObjectImpl::GetDataHere](#getdatahere)|Podobnie jak `GetData`, z wyjątkiem klienta należy przydzielić **STGMEDIUM** struktury. Zwraca implementację ATL **E_NOTIMPL**.|  
|[IDataObjectImpl::QueryGetData](#querygetdata)|Określa, czy obiekt danych obsługuje określonego **FORMATETC** struktury do przesyłania danych. Zwraca implementację ATL **E_NOTIMPL**.|  
|[IDataObjectImpl::SetData](#setdata)|Przesyła dane z klienta do obiektu danych. Zwraca implementację ATL **E_NOTIMPL**.|  
  
## <a name="remarks"></a>Uwagi  
 [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) interfejsu udostępnia metody do obsługi Uniform transferu danych. `IDataObject` używa struktury formatem [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) i [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) do pobierania i przechowywania danych.  
  
 `IDataObject` zarządza także połączenia informujące wychwytywanie do obsługi powiadomień o zmianie danych. Aby klienta do otrzymywania powiadomień o zmianie danych z obiektu danych, klient musi implementować [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513) interfejsu dla obiektu o nazwie zbiornika porada. Gdy klient następnie wywołuje **IDataObject::DAdvise**, między obiektem danych i odbiorczy Porada jest nawiązywane połączenie.  
  
 Klasa `IDataObjectImpl` udostępnia domyślną implementację elementu `IDataObject` i implementuje **IUnknown** , wysyłając informacje o do zrzutu kompilacje urządzenia podczas debugowania.  
  
 **Innych pokrewnych artykułach** [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md), [tworzenie Projekt ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IDataObject`  
  
 `IDataObjectImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
##  <a name="dadvise"></a>  IDataObjectImpl::DAdvise  
 Ustanawia połączenie między obiektem danych i odbiorczy porada.  
  
```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```  
  
### <a name="remarks"></a>Uwagi  
 Dzięki temu zbiornika Porada otrzymywać powiadomienia o zmianach w obiekcie.  
  
 Aby zakończyć połączenie, należy wywołać [DUnadvise](#dunadvise).  
  
 Zobacz [IDataObject::DAdvise](http://msdn.microsoft.com/library/windows/desktop/ms692579) w systemie Windows SDK.  
  
##  <a name="dunadvise"></a>  IDataObjectImpl::DUnadvise  
 Przerywa połączenie wcześniej ustanowione za pośrednictwem [DAdvise](#dadvise).  
  
```
HRESULT DUnadvise(DWORD dwConnection);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IDataObject::DUnadvise](http://msdn.microsoft.com/library/windows/desktop/ms692448) w systemie Windows SDK.  
  
##  <a name="enumdadvise"></a>  IDataObjectImpl::EnumDAdvise  
 Tworzy moduł wyliczający do iteracji bieżących połączeń advisory.  
  
```
HRESULT DAdvise(
    FORMATETC* pformatetc,
    DWORD advf,
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IDataObject::EnumDAdvise](http://msdn.microsoft.com/library/windows/desktop/ms680127) w systemie Windows SDK.  
  
##  <a name="enumformatetc"></a>  IDataObjectImpl::EnumFormatEtc  
 Tworzy moduł wyliczający do iteracji **FORMATETC** struktury obsługiwane przez obiekt danych.  
  
```
HRESULT EnumFormatEtc(  
    DWORD dwDirection,
    IEnumFORMATETC** ppenumFormatEtc);
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IDataObject::EnumFormatEtc](http://msdn.microsoft.com/library/windows/desktop/ms683979) w systemie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **E_NOTIMPL**.  
  
##  <a name="firedatachange"></a>  IDataObjectImpl::FireDataChange  
 Wysyła powiadomienia o zmianach z powrotem do zbiornika każdej Porada, który jest obecnie zarządzany.  
  
```
HRESULT FireDataChange();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
##  <a name="getcanonicalformatetc"></a>  IDataObjectImpl::GetCanonicalFormatEtc  
 Pobiera logicznie równoważne **FORMATETC** struktury, który jest bardziej złożony.  
  
```
HRESULT GetCanonicalFormatEtc(FORMATETC* pformatetcIn, FORMATETC* pformatetcOut);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **E_NOTIMPL**.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IDataObject::GetCanonicalFormatEtc](http://msdn.microsoft.com/library/windows/desktop/ms680685) w systemie Windows SDK.  
  
##  <a name="getdata"></a>  IDataObjectImpl::GetData  
 Przesyła dane z obiektem danych do klienta.  
  
```
HRESULT GetData(
    FORMATETC* pformatetcIn,
    STGMEDIUM* pmedium);
```  
  
### <a name="remarks"></a>Uwagi  
 *PformatetcIn* parametr musi określać typ średnia magazynu z **TYMED_MFPICT**.  
  
 Zobacz [Metoda IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) w systemie Windows SDK.  
  
##  <a name="getdatahere"></a>  IDataObjectImpl::GetDataHere  
 Podobnie jak `GetData`, z wyjątkiem klienta należy przydzielić **STGMEDIUM** struktury.  
  
```
HRESULT GetDataHere(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **E_NOTIMPL**.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [Metoda IDataObject::GetDataHere](http://msdn.microsoft.com/library/windows/desktop/ms687266) w systemie Windows SDK.  
  
##  <a name="querygetdata"></a>  IDataObjectImpl::QueryGetData  
 Określa, czy obiekt danych obsługuje określonego **FORMATETC** struktury do przesyłania danych.  
  
```
HRESULT QueryGetData(FORMATETC* pformatetc);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **E_NOTIMPL**.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IDataObject::QueryGetData](http://msdn.microsoft.com/library/windows/desktop/ms680637) w systemie Windows SDK.  
  
##  <a name="setdata"></a>  IDataObjectImpl::SetData  
 Przesyła dane z klienta do obiektu danych.  
  
```
HRESULT SetData(
    FORMATETC* pformatetc,
    STGMEDIUM* pmedium,
    BOOL fRelease);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **E_NOTIMPL**.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [IDataObject::SetData](http://msdn.microsoft.com/library/windows/desktop/ms686626) w systemie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
