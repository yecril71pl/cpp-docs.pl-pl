---
title: Funkcje globalne kierowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlFreeMarshalStream
- atlbase/ATL::AtlMarshalPtrInProc
- atlbase/ATL::AtlUnmarshalPtr
dev_langs:
- C++
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44c5205416ff19eeb849b0532d015275e4eb166e
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879342"
---
# <a name="marshaling-global-functions"></a>Funkcje globalne kierowania
Te funkcje zapewniają obsługę do organizowania i konwersji organizowania danych na wskaźniki interfejsu.  
  
> [!IMPORTANT]
>  Funkcje wymienione w poniższej tabeli nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
|||  
|-|-|  
|[AtlFreeMarshalStream](#atlfreemarshalstream)|Zwalnia dane organizatora i `IStream` wskaźnika.|  
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|Tworzy nowy obiekt strumienia i organizuje określony wskaźnik interfejsu.|  
|[AtlUnmarshalPtr](#atlunmarshalptr)|Konwertuje dane dotyczące organizowania strumienia na wskaźnik interfejsu.|  

## <a name="requirements"></a>Wymagania:
**Nagłówek:** atlbase.h
  
##  <a name="atlfreemarshalstream"></a>  AtlFreeMarshalStream  
 Zwalnia dane organizatora w strumieniu, a następnie zwalnia wskaźnik strumienia.  

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```  
  
### <a name="parameters"></a>Parametry  
 *pStream*  
 [in] Wskaźnik do `IStream` interfejsu dla strumienia używane do kierowania.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [AtlMarshalPtrInProc](#atlmarshalptrinproc).  
  
##  <a name="atlmarshalptrinproc"></a>  AtlMarshalPtrInProc  
 Tworzy nowy obiekt strumienia, zapisuje identyfikator CLSID serwera proxy do strumienia i organizuje określony wskaźnik interfejsu, pisząc dane potrzebne do zainicjowania serwera proxy do strumienia.  
  
```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnk*  
 [in] Wskaźnik do interfejs, który ma być organizowany.  
  
 *IID*  
 [in] Identyfikator GUID interfejsu są przekazywane.  
  
 *ppStream*  
 [out] Wskaźnik do `IStream` interfejsu na nowy obiekt strumienia używane do kierowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Ustawiono flagę MSHLFLAGS_TABLESTRONG, dzięki czemu mogą być organizowane wskaźnik do wielu strumieni. Wskaźnik może być również wycofana wiele razy.  
  
 Jeśli przekazywanie zakończy się niepowodzeniem, wskaźnik strumienia jest zwalniana.  
  
 `AtlMarshalPtrInProc` należy używać tylko na wskaźnik do obiektu w trakcie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#50](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]  
  
##  <a name="atlunmarshalptr"></a>  AtlUnmarshalPtr  
 Konwertuje dane dotyczące organizowania strumienia na wskaźnik interfejsu, którego może używać klient.  
   
```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```  
  
### <a name="parameters"></a>Parametry  
 *pStream*  
 [in] Wskaźnik do strumienia jest wycofana.  
  
 *IID*  
 [in] Identyfikator GUID jest wycofana interfejsu.  
  
 *ppUnk*  
 [out] Wskaźnik do interfejsu wycofana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowe wartości HRESULT.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [AtlMarshalPtrInProc](#atlmarshalptrinproc).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../atl/reference/atl-functions.md)
