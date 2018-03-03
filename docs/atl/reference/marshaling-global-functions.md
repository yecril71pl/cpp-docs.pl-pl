---
title: Organizowanie funkcje globalne | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlFreeMarshalStream
- atlbase/ATL::AtlMarshalPtrInProc
- atlbase/ATL::AtlUnmarshalPtr
dev_langs:
- C++
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a12f719d2cb893a5d2989a80f5fe09a5b49aeca2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="marshaling-global-functions"></a>Organizowanie globalne funkcje
Funkcje te zapewniają obsługę organizowanie i konwersji organizowania danych do wskaźników interfejsów.  
  
> [!IMPORTANT]
>  Funkcje wymienione w poniższej tabeli nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
|||  
|-|-|  
|[AtlFreeMarshalStream](#atlfreemarshalstream)|Kierowanie dane są uwalniane i `IStream` wskaźnika.|  
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|Tworzy nowy obiekt strumienia i marshals wskaźnika określonego interfejsu.|  
|[AtlUnmarshalPtr](#atlunmarshalptr)|Konwertuje dane kierowania strumienia wskaźnika interfejsu.|  

## <a name="requirements"></a>Wymagania:
**Nagłówek:** atlbase.h
  
##  <a name="atlfreemarshalstream"></a>AtlFreeMarshalStream  
 Zwalnia dane organizatora w strumieniu, a następnie zwalnia wskaźnik strumienia.  

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```  
  
### <a name="parameters"></a>Parametry  
 `pStream`  
 [in] Wskaźnik do `IStream` interfejs używany do przekazywania międzyprocesowego strumienia.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [AtlMarshalPtrInProc](#atlmarshalptrinproc).  
  
##  <a name="atlmarshalptrinproc"></a>AtlMarshalPtrInProc  
 Tworzy nowy obiekt strumienia, zapisuje identyfikator CLSID serwera proxy do strumienia i organizuje określony wskaźnik interfejsu, pisząc dane potrzebne do zainicjowania serwera proxy do strumienia.  
  
```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnk*  
 [in] Wskaźnik do interfejsu, który ma być przekazywane.  
  
 `iid`  
 [in] Identyfikator GUID interfejsu są organizowane.  
  
 `ppStream`  
 [out] Wskaźnik do `IStream` interfejs dla nowego obiektu strumienia, używany do przekazywania międzyprocesowego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa wartość HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 **MSHLFLAGS_TABLESTRONG** flaga jest ustawiona dlatego wskaźnik mogą być przekazywane do wielu strumieni. Wskaźnik może być również wchodzącej wiele razy.  
  
 Jeśli przekazywanie zakończy się niepowodzeniem, zwolnieniu wskaźnika strumienia.  
  
 `AtlMarshalPtrInProc`można użyć tylko na wskaźnik do obiektu w trakcie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#50](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]  
  
##  <a name="atlunmarshalptr"></a>AtlUnmarshalPtr  
 Konwertuje dane dotyczące organizowania strumienia na wskaźnik interfejsu, którego może używać klient.  
   
```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```  
  
### <a name="parameters"></a>Parametry  
 `pStream`  
 [in] Wskaźnik do strumienia zostanie wycofana.  
  
 `iid`  
 [in] Identyfikator GUID interfejsu zostanie wycofana.  
  
 `ppUnk`  
 [out] Wskaźnik do interfejsu wycofana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa wartość HRESULT.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [AtlMarshalPtrInProc](#atlmarshalptrinproc).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../atl/reference/atl-functions.md)
