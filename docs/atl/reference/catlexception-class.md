---
title: Klasa CAtlException | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlException
- ATLEXCEPT/ATL::CAtlException
- ATLEXCEPT/ATL::CAtlException::CAtlException
- ATLEXCEPT/ATL::CAtlException::m_hr
dev_langs: C++
helpviewer_keywords: CAtlException class
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b0a22b1918f255290ae6b47604aa57ef484a9527
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="catlexception-class"></a>Klasa CAtlException
Ta klasa definiuje wyjątek ATL.  
  
## <a name="syntax"></a>Składnia  
  
```
class CAtlException
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlException::CAtlException](#catlexception)|Konstruktor.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlException::operator HRESULT](#operator_hresult)|Rzutuje bieżący obiekt wartość HRESULT.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlException::m_hr](#m_hr)|Zmienna typu HRESULT utworzony przez obiekt i używany do przechowywania warunku błędu.|  
  
## <a name="remarks"></a>Uwagi  
 A `CAtlException` obiekt reprezentuje związanych z operacją ATL warunku wyjątku. `CAtlException` Klasa zawiera element członkowski danych publicznych, który przechowuje kod stanu wskazujący przyczynę wyjątek i operatora rzutowania, który umożliwia traktowanie wyjątek, tak jakby był on HRESULT.  
  
 Ogólnie rzecz biorąc, należy wywołać `AtlThrow` zamiast tworzenia `CAtlException` obiekt bezpośrednio.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlexcept.h  
  
##  <a name="catlexception"></a>CAtlException::CAtlException  
 Konstruktor.  
  
```
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hr`  
 `HRESULT` Kod błędu.  
  
##  <a name="operator_hresult"></a>CAtlException::operator HRESULT 
 Rzutuje bieżący obiekt wartość HRESULT.  
  
```  
operator HRESULT() const throw ();
```  
  
##  <a name="m_hr"></a>CAtlException::m_hr  
 `HRESULT` Element członkowski danych.  
  
```
HRESULT m_hr;
```  
  
### <a name="remarks"></a>Uwagi  
 Element członkowski danych, która przechowuje warunku błędu. Wartość HRESULT jest ustawiana przez konstruktora, [CAtlException::CAtlException](#catlexception).  
  
## <a name="see-also"></a>Zobacz też  
 [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)   
 [Przegląd klas](../../atl/atl-class-overview.md)
