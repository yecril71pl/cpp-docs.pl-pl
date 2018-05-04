---
title: Klasa CComCriticalSection | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComCriticalSection
- ATLCORE/ATL::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::Init
- ATLCORE/ATL::CComCriticalSection::Lock
- ATLCORE/ATL::CComCriticalSection::Term
- ATLCORE/ATL::CComCriticalSection::Unlock
- ATLCORE/ATL::CComCriticalSection::m_sec
dev_langs:
- C++
helpviewer_keywords:
- CComCriticalSection class
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25376aba3cfbade202d1cf95c2218e88713ac22a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ccomcriticalsection-class"></a>Klasa CComCriticalSection
Ta klasa dostarcza metody uzyskiwania i zwalniania prawo własności obiektu sekcja krytyczna.  
  
## <a name="syntax"></a>Składnia  
  
```
class CComCriticalSection
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComCriticalSection::CComCriticalSection](#ccomcriticalsection)|Konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComCriticalSection::Init](#init)|Tworzy i inicjuje obiekt sekcja krytyczna.|  
|[CComCriticalSection::Lock](#lock)|Uzyskuje prawo własności obiektu sekcja krytyczna.|  
|[CComCriticalSection::Term](#term)|Zwalnia zasoby systemowe, używane przez obiekt sekcja krytyczna.|  
|[CComCriticalSection::Unlock](#unlock)|Zwalnia prawo własności obiektu sekcja krytyczna.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComCriticalSection::m_sec](#m_sec)|A **CRITICAL_SECTION** obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `CComCriticalSection` jest podobny do klasy [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md), ale należy jawnie zainicjować i zwolnij sekcja krytyczna.  
  
 Zazwyczaj `CComCriticalSection` za pośrednictwem `typedef` nazwa [criticalsection —](ccommultithreadmodel-class.md#criticalsection). Ta nazwa odwołuje się do `CComCriticalSection` podczas [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) jest używany.  

  
 Zobacz [klasy CComCritSecLock](../../atl/reference/ccomcritseclock-class.md) dla Najbezpieczniejszym sposobem używać tej klasy niż wywoływania `Lock` i `Unlock` bezpośrednio.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcore.h  
  
##  <a name="ccomcriticalsection"></a>  CComCriticalSection::CComCriticalSection  
 Konstruktor.  
  
```
CComCriticalSection() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Ustawia [m_sec](#m_sec) element członkowski danych null **.**  
  
##  <a name="init"></a>  CComCriticalSection::Init  
 Wywołania funkcji Win32 [InitializeCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms683472), które inicjuje obiekt sekcja krytyczna znajdujący się w [m_sec](#m_sec) element członkowski danych.  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia **E_OUTOFMEMORY** lub **E_FAIL** w przypadku awarii.  
  
##  <a name="lock"></a>  CComCriticalSection::Lock  
 Wywołania funkcji Win32 [EnterCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682608), które czeka, aż wątku mogą przejąć prawo własności obiektu sekcja krytyczna zawarte w [m_sec](#m_sec) element członkowski danych.  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia **E_OUTOFMEMORY** lub **E_FAIL** w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt sekcja krytyczna najpierw musi zostać zainicjowany z wywołaniem do [Init](#init) metody. Po zakończeniu chronionych kodu wykonywania wątku należy wywołać [Unlock](#unlock) zwolnienia własność sekcja krytyczna.  
  
##  <a name="m_sec"></a>  CComCriticalSection::m_sec  
 Zawiera obiekt sekcja krytyczna, który jest używany przez wszystkie `CComCriticalSection` metody.  
  
```
CRITICAL_SECTION m_sec;
```  
  
##  <a name="term"></a>  CComCriticalSection::Term  
 Wywołania funkcji Win32 [DeleteCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682552), który zwalnia wszystkie zasoby używane przez obiekt sekcja krytyczna zawarte w [m_sec](#m_sec) element członkowski danych.  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Raz `Term` została wywołana, krytycznej sekcji można już używać do synchronizacji.  
  
##  <a name="unlock"></a>  CComCriticalSection::Unlock  
 Wywołania funkcji Win32 [LeaveCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms684169), który zwalnia prawo własności obiektu sekcja krytyczna zawarte w [m_sec](#m_sec) element członkowski danych.  
  
```
HRESULT Unlock() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK`.  
  
### <a name="remarks"></a>Uwagi  
 Najpierw uzyskać prawo własności, należy wywołać wątku [blokady](#lock) metody. Każde wywołanie `Lock` wymaga odpowiedniego wywołania `Unlock` zwolnienia własność sekcja krytyczna.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Klasa CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)
