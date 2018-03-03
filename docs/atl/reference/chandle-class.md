---
title: Klasa CHandle | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHandle
- ATLBASE/ATL::CHandle
- ATLBASE/ATL::CHandle::CHandle
- ATLBASE/ATL::CHandle::Attach
- ATLBASE/ATL::CHandle::Close
- ATLBASE/ATL::CHandle::Detach
- ATLBASE/ATL::CHandle::m_h
dev_langs:
- C++
helpviewer_keywords:
- CHandle class
ms.assetid: 883e9db5-40ec-4e29-9c74-4dd2ddd2e35d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cd58ba8ce15bb26b4e5b768baedbf8ddfe829f2b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="chandle-class"></a>Klasa CHandle
Ta klasa dostarcza metody do tworzenia i używania obiektu uchwyt.  
  
## <a name="syntax"></a>Składnia  
  
```
class CHandle
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHandle::CHandle](#chandle)|Konstruktor.|  
|[CHandle:: ~ CHandle](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHandle::Attach](#attach)|Wywołanie tej metody, aby dołączyć `CHandle` obiektu do istniejącego dojścia.|  
|[CHandle::Close](#close)|Wywołanie tej metody, aby zamknąć `CHandle` obiektu.|  
|[CHandle::Detach](#detach)|Wywołanie tej metody można odłączyć dojścia z `CHandle` obiektu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHandle::operator dojścia](#operator_handle)|Zwraca wartość przechowywanej dojścia.|  
|[CHandle::operator =](#operator_eq)|Operator przypisania.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CHandle::m_h](#m_h)|Zmiennej członkowskiej, która przechowuje dojście.|  
  
## <a name="remarks"></a>Uwagi  
 A `CHandle` obiektu można użyć w każdym przypadku, gdy jest wymagane dojście: główną różnicą jest to, że `CHandle` obiekt zostanie automatycznie usunięty.  
  
> [!NOTE]
>  Niektóre funkcje interfejsu API będzie używać wartości NULL jako pusty lub nieprawidłowy uchwyt, podczas gdy inne INVALID_HANDLE_VALUE. `CHandle`używa tylko wartości NULL i będzie traktować INVALID_HANDLE_VALUE jako prawdziwe dojścia. Wywołanie interfejsu API, która może zwracać INVALID_HANDLE_VALUE, należy sprawdzić, czy ta wartość przed wywołaniem [CHandle::Attach](#attach) lub przekazanie jej do `CHandle` konstruktora, a zamiast tego należy przekazać wartość NULL.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="attach"></a>CHandle::Attach  
 Wywołanie tej metody, aby dołączyć `CHandle` obiektu do istniejącego dojścia.  
  
```
void Attach(HANDLE h) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `h`  
 `CHandle`zostanie przejąć na własność dojście `h`.  
  
### <a name="remarks"></a>Uwagi  
 Przypisuje `CHandle` do obiektu `h` obsługi. W kompilacjach debuguje ATLASSERT zostanie wygenerowany, jeśli `h` ma wartość NULL. Nie inne co ważności dojście dokonuje.  
  
##  <a name="chandle"></a>CHandle::CHandle  
 Konstruktor.  
  
```
CHandle() throw();
CHandle(CHandle& h) throw();
explicit CHandle(HANDLE h) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `h`  
 Istniejące dojście lub `CHandle`.  
  
### <a name="remarks"></a>Uwagi  
 Tworzy nowy `CHandle` obiektu, opcjonalnie przy użyciu istniejących dojścia lub `CHandle` obiektu.  
  
##  <a name="dtor"></a>CHandle:: ~ CHandle  
 Destruktor.  
  
```
~CHandle() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia `CHandle` obiektu przez wywołanie metody [CHandle::Close](#close).  
  
##  <a name="close"></a>CHandle::Close  
 Wywołanie tej metody, aby zamknąć `CHandle` obiektu.  
  
```
void Close() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zamyka otwarty obiekt dojścia. Jeśli dojście ma wartość NULL, która będzie w przypadku, gdy **Zamknij** została już wywołana, ATLASSERT zostanie wygenerowany w kompilacjach debugowania.  
  
##  <a name="detach"></a>CHandle::Detach  
 Wywołanie tej metody można odłączyć dojścia z `CHandle` obiektu.  
  
```
HANDLE Detach() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca dojście odłączany.  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia własność uchwytu.  
  
##  <a name="m_h"></a>CHandle::m_h  
 Zmiennej członkowskiej, która przechowuje dojście.  
  
```
HANDLE m_h;
```  
  
##  <a name="operator_eq"></a>CHandle::operator =  
 Operator przypisania.  
  
```
CHandle& operator=(CHandle& h) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `h`  
 `CHandle`zostanie przejąć na własność dojście `h`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do nowego `CHandle` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `CHandle` obiektu zawiera obecnie uchwytu, zostanie zamknięte. `CHandle` Obiekt przekazywany będzie mieć odwołanie dojścia wartość NULL. Gwarantuje to, że dwa `CHandle` obiekty nigdy nie będzie zawierać tej samej aktywnej dojścia.  
  
##  <a name="operator_handle"></a>CHandle::operator dojścia  
 Zwraca wartość przechowywanej dojścia.  
  
```  
operator HANDLE() const throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwraca wartość przechowywana we [CHandle::m_h](#m_h).  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)
