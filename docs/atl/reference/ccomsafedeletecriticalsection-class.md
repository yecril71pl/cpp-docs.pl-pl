---
title: Klasa CComSafeDeleteCriticalSection | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Init
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Lock
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Term
- ATLCORE/ATL::m_bInitialized
dev_langs: C++
helpviewer_keywords: CComSafeDeleteCriticalSection class
ms.assetid: 4d2932c4-ba8f-48ec-8664-1db8bed01314
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: df86d5219940ffc1dd3c34f47920675014eefd13
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ccomsafedeletecriticalsection-class"></a>Klasa CComSafeDeleteCriticalSection
Ta klasa dostarcza metody uzyskiwania i zwalniania prawo własności obiektu sekcja krytyczna.  
  
## <a name="syntax"></a>Składnia  
  
```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection](#ccomsafedeletecriticalsection)|Konstruktor.|  
|[CComSafeDeleteCriticalSection:: ~ CComSafeDeleteCriticalSection](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComSafeDeleteCriticalSection::Init](#init)|Tworzy i inicjuje obiekt sekcja krytyczna.|  
|[CComSafeDeleteCriticalSection::Lock](#lock)|Uzyskuje prawo własności obiektu sekcja krytyczna.|  
|[CComSafeDeleteCriticalSection::Term](#term)|Zwalnia zasoby systemowe, używane przez obiekt sekcja krytyczna.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|||  
|-|-|  
|[m_bInitialized](#m_binitialized)|Flagi czy wewnętrznej **CRITICAL_SECTION** obiekt został zainicjowany.|  
  
## <a name="remarks"></a>Uwagi  
 `CComSafeDeleteCriticalSection`pochodzi z klasy [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Jednak `CComSafeDeleteCriticalSection` udostępnia mechanizmy dodatkowego bezpieczeństwa w porównaniu z [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).  
  
 Gdy wystąpienie klasy `CComSafeDeleteCriticalSection` wykracza poza zakres lub jest jawnie usunięte z pamięci, obiekt sekcja krytyczna zostaną automatycznie wyczyszczone, jeśli jest nadal ważny. Ponadto [CComSafeDeleteCriticalSection::Term](#term) metody zakończyć bezpiecznie Jeśli sekcja krytyczna obiekt źródłowy nie został jeszcze przydzielony lub już została zwolniona z pamięci.  
  
 Zobacz [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) uzyskać więcej informacji na temat klas pomocniczych sekcja krytyczna.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 `CComSafeDeleteCriticalSection`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcore.h  
  
##  <a name="ccomsafedeletecriticalsection"></a>CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection  
 Konstruktor.  
  
```
CComSafeDeleteCriticalSection();
```  
  
### <a name="remarks"></a>Uwagi  
 Ustawia [m_bInitialized](#m_binitialized) element członkowski danych do **false**.  
  
##  <a name="dtor"></a>CComSafeDeleteCriticalSection:: ~ CComSafeDeleteCriticalSection  
 Destruktor.  
  
```
~CComSafeDeleteCriticalSection() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wewnętrznej **CRITICAL_SECTION** obiekt z pamięci, jeśli [m_bInitialized](#m_binitialized) ma ustawioną wartość elementu członkowskiego danych **true**.  
  
##  <a name="init"></a>CComSafeDeleteCriticalSection::Init  
 Klasa podstawowa implementacja wywołuje [Init](/visualstudio/debugger/init) i ustawia [m_bInitialized](#m_binitialized) do **true** w przypadku powodzenia.  
  
```
HRESULT Init() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wynik [CComCriticalSection::Init](../../atl/reference/ccomcriticalsection-class.md#init).  
  
##  <a name="lock"></a>CComSafeDeleteCriticalSection::Lock  
Klasa podstawowa implementacja wywołuje [blokady](ccomcriticalsection-class.md#lock).  

  
```
HRESULT Lock();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wynik [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda przyjmuje [m_bInitialized](#m_binitialized) ma ustawioną wartość elementu członkowskiego danych **true** wejścia. Potwierdzenia jest generowany w kompilacjach debugowania Jeśli ta condidtion nie są spełnione.  
  
 Aby uzyskać więcej informacji dotyczących zachowania funkcji, zapoznaj się [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).  
  
##  <a name="m_binitialized"></a>CComSafeDeleteCriticalSection::m_bInitialized  
 Flagi czy wewnętrznej **CRITICAL_SECTION** obiekt został zainicjowany.  
  
```
bool m_bInitialized;
```  
  
### <a name="remarks"></a>Uwagi  
 **M_bInitialized** elementu członkowskiego danych jest używane do śledzenia ważności podstawowych **CRITICAL_SECTION** obiekt skojarzony z [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) klasy. Podstawowa **CRITICAL_SECTION** obiektu nie zostanie podjęta próba zwolniona z pamięci, jeśli ta flaga nie jest równa **true**.  
  
##  <a name="term"></a>CComSafeDeleteCriticalSection::Term  
 Klasa podstawowa implementacja wywołuje [CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term) Jeśli wewnętrznej **CRITICAL_SECTION** obiekt jest prawidłowy.  
  
```
HRESULT Term() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wynik [CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term), lub **S_OK** Jeśli [m_bInitialized](#m_binitialized) ustawiono **false** wejścia.  
  
### <a name="remarks"></a>Uwagi  
 Można bezpiecznie wywołać tej metody, nawet jeśli wewnętrznej **CRITICAL_SECTION** obiekt jest nieprawidłowy. Destruktor tej klasy wywołuje tę metodę, jeśli [m_bInitialized](#m_binitialized) ma ustawioną wartość elementu członkowskiego danych **true**.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
