---
title: Klasa CComCritSecLock | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComCritSecLock
- ATLBASE/ATL::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::Lock
- ATLBASE/ATL::CComCritSecLock::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CComCritSecLock class
ms.assetid: 223152a1-86c3-4ef9-89a7-f455fe791b0e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1cb07c2cca9394c23c6c3db156e205749f62e3f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ccomcritseclock-class"></a>Klasa CComCritSecLock
Ta klasa dostarcza metody do blokowanie i odblokowywanie obiektu sekcja krytyczna.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class TLock> class CComCritSecLock
```  
  
#### <a name="parameters"></a>Parametry  
 *TLock*  
 Obiekt zablokować i odblokować.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComCritSecLock::CComCritSecLock](#ctor)|Konstruktor.|  
|[CComCritSecLock:: ~ CComCritSecLock](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComCritSecLock::Lock](#lock)|Wywołanie tej metody można zablokować obiektu sekcja krytyczna.|  
|[CComCritSecLock::Unlock](#unlock)|Wywołaj tę metodę w celu odblokowania obiektu sekcja krytyczna.|  
  
## <a name="remarks"></a>Uwagi  
 Klasa używana do blokowania i odblokowywania obiektów w sposób bezpieczniejsze niż ze [klasy CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) lub [CComAutoCriticalSection klasy](../../atl/reference/ccomautocriticalsection-class.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="ctor"></a>CComCritSecLock::CComCritSecLock  
 Konstruktor.  
  
```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```  
  
### <a name="parameters"></a>Parametry  
 *CS*  
 Obiekt sekcja krytyczna.  
  
 `bInitialLock`  
 Stan początkowy blokady: **true** oznacza zablokowany.  
  
### <a name="remarks"></a>Uwagi  
 Inicjuje obiekt sekcja krytyczna.  
  
##  <a name="dtor"></a>CComCritSecLock:: ~ CComCritSecLock  
 Destruktor.  
  
```
~CComCritSecLock() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Umożliwia odblokowanie obiektu sekcja krytyczna.  
  
##  <a name="lock"></a>CComCritSecLock::Lock  
 Wywołanie tej metody można zablokować obiektu sekcja krytyczna.  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli obiekt został pomyślnie zablokowany lub błąd HRESULT w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli obiekt jest już zablokowany, wystąpi błąd potwierdzenia w kompilacjach debugowania.  
  
##  <a name="unlock"></a>CComCritSecLock::Unlock  
 Wywołaj tę metodę w celu odblokowania obiektu sekcja krytyczna.  
  
```
void Unlock() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli obiekt został już odblokowany, błąd ASSERT zostanie przeprowadzona w kompilacjach debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)   
 [Klasa CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)
