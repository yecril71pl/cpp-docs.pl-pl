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
ms.openlocfilehash: 5926f92ae636a13c1e5241792790151ee48ceddc
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884873"
---
# <a name="ccomcriticalsection-class"></a>Klasa CComCriticalSection
Ta klasa dostarcza metody do uzyskania i zwalniania własności obiektu sekcję krytyczną.  
  
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
|[CComCriticalSection::Init](#init)|Tworzy i inicjuje obiekt sekcję krytyczną.|  
|[CComCriticalSection::Lock](#lock)|Uzyskuje własność obiektu sekcję krytyczną.|  
|[CComCriticalSection::Term](#term)|Zwalnia zasoby systemowe używane przez obiekt sekcję krytyczną.|  
|[CComCriticalSection::Unlock](#unlock)|Zwalnia własność obiektu sekcję krytyczną.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComCriticalSection::m_sec](#m_sec)|Obiekt CRITICAL_SECTION.|  
  
## <a name="remarks"></a>Uwagi  
 `CComCriticalSection` jest podobna do klasy [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md), z tą różnicą, że musisz jawnie zainicjować i zwolnij sekcję krytyczną.  
  
 Zazwyczaj można użyć `CComCriticalSection` za pośrednictwem **typedef** nazwa [CriticalSection](ccommultithreadmodel-class.md#criticalsection). Ta nazwa odwołuje się do `CComCriticalSection` podczas [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) jest używana.  

  
 Zobacz [klasa CComCritSecLock](../../atl/reference/ccomcritseclock-class.md) dla bezpieczniejszy sposób użyć tej klasy niż wywoływania `Lock` i `Unlock` bezpośrednio.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcore.h  
  
##  <a name="ccomcriticalsection"></a>  CComCriticalSection::CComCriticalSection  
 Konstruktor.  
  
```
CComCriticalSection() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zestawy [m_sec](#m_sec) element członkowski danych na wartość NULL.  
  
##  <a name="init"></a>  CComCriticalSection::Init  
 Wywołuje funkcję Win32 [InitializeCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms683472), która inicjuje obiekt sekcję krytyczną, znajdujący się w [m_sec](#m_sec) element członkowski danych.  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia E_OUTOFMEMORY lub E_FAIL w przypadku niepowodzenia.  
  
##  <a name="lock"></a>  CComCriticalSection::Lock  
 Wywołuje funkcję Win32 [EnterCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682608), która czeka, aż wątek może zająć własności obiektu sekcję krytyczną, zawarte w [m_sec](#m_sec) element członkowski danych.  
  
```
HRESULT Lock() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia E_OUTOFMEMORY lub E_FAIL w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt sekcję krytyczną, najpierw musi zostać zainicjowany z wywołaniem [Init](#init) metody. Gdy chroniony kod zakończenia, wątek musi wywołać [Unlock](#unlock) zwolnić własności sekcję krytyczną.  
  
##  <a name="m_sec"></a>  CComCriticalSection::m_sec  
 Zawiera obiekt sekcję krytyczną, który jest używany przez wszystkie `CComCriticalSection` metody.  
  
```
CRITICAL_SECTION m_sec;
```  
  
##  <a name="term"></a>  CComCriticalSection::Term  
 Wywołuje funkcję Win32 [DeleteCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms682552), które zwalnia wszystkie zasoby używane przez obiekt sekcję krytyczną, zawarte w [m_sec](#m_sec) element członkowski danych.  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Raz `Term` została wywołana, krytycznej sekcji nie będzie można użyć do synchronizacji.  
  
##  <a name="unlock"></a>  CComCriticalSection::Unlock  
 Wywołuje funkcję Win32 [LeaveCriticalSection](http://msdn.microsoft.com/library/windows/desktop/ms684169), która uwalnia własność obiektu sekcję krytyczną, zawarte w [m_sec](#m_sec) element członkowski danych.  
  
```
HRESULT Unlock() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK.  
  
### <a name="remarks"></a>Uwagi  
 Najpierw uzyskać własności, wątek musi wywołać [blokady](#lock) metody. Każde wywołanie `Lock` wymaga odpowiedniego wywołania `Unlock` zwolnić własności sekcję krytyczną.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)   
 [Klasa CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)
