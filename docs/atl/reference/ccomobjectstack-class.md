---
title: Klasa CComObjectStack | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectStack
- ATLCOM/ATL::CComObjectStack
- ATLCOM/ATL::CComObjectStack::CComObjectStack
- ATLCOM/ATL::CComObjectStack::AddRef
- ATLCOM/ATL::CComObjectStack::QueryInterface
- ATLCOM/ATL::CComObjectStack::Release
- ATLCOM/ATL::CComObjectStack::m_hResFinalConstruct
dev_langs:
- C++
helpviewer_keywords:
- CComObjectStack class
ms.assetid: 3da72c40-c834-45f6-bb76-6ac204028d80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ac37ac5abc193082aaccb8d5de1a4f75f8a3f7c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ccomobjectstack-class"></a>Klasa CComObjectStack
Ta klasa tworzy tymczasowy obiekt COM i dostarcza mu szkieletowych implementacja **IUnknown**.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class  Base>  
class CComObjectStack
 : public Base
```  
  
#### <a name="parameters"></a>Parametry  
 `Base`  
 Pochodne klasy, [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) lub [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak również od innych interfejsu mają być obsługiwane w obiekcie.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComObjectStack::CComObjectStack](#ccomobjectstack)|Konstruktor.|  
|[CComObjectStack:: ~ CComObjectStack](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComObjectStack::AddRef](#addref)|Zwraca wartość zero. W trybie debugowania, wywołuje `_ASSERTE`.|  
|[CComObjectStack::QueryInterface](#queryinterface)|Zwraca **E_NOINTERFACE**. W trybie debugowania, wywołuje `_ASSERTE`.|  
|[CComObjectStack::Release](#release)|Zwraca wartość zero. W trybie debugowania, wywołuje `_ASSERTE`. ~|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComObjectStack::m_hResFinalConstruct](#m_hresfinalconstruct)|Zawiera **HRESULT** zwrócony podczas tworzenia `CComObjectStack` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `CComObjectStack` Pozwala utworzyć tymczasowego obiektu modelu COM oraz określić obiekt szkieletowych wdrożenia **IUnknown**. Zazwyczaj obiekt jest używany jako zmienną lokalną w obrębie jednej funkcji (tj. spoczywa na stosie). Ponieważ obiekt zostanie zniszczony po zakończeniu działania funkcji, liczenie odwołań nie odbywa się zwiększyć wydajność.  
  
 Poniższy przykład pokazuje, jak utworzyć obiektu COM, użyć wewnątrz funkcji:  
  
 [!code-cpp[NVC_ATL_COM#42](../../atl/codesnippet/cpp/ccomobjectstack-class_1.cpp)]  
  
 Tymczasowy obiekt `Tempobj` spoczywa na stosie i automatycznie zniknie po zakończeniu działania funkcji.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `Base`  
  
 `CComObjectStack`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
##  <a name="addref"></a>  CComObjectStack::AddRef  
 Zwraca wartość zero.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 W trybie debugowania, wywołuje `_ASSERTE`.  
  
##  <a name="ccomobjectstack"></a>  CComObjectStack::CComObjectStack  
 Konstruktor.  
  
```
CComObjectStack(void* = NULL);
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołania `FinalConstruct` , a następnie ustawia [m_hResFinalConstruct](#m_hresfinalconstruct) do `HRESULT` zwrócony przez `FinalConstruct`. Jeśli nie ma pochodzi z klasy podstawowej [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), należy podać własne `FinalConstruct` metody. Wywołania destruktora `FinalRelease`.  
  
##  <a name="dtor"></a>  CComObjectStack:: ~ CComObjectStack  
 Destruktor.  
  
```
CComObjectStack();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwalnia wszystkie przydzielone zasoby i wywołania [FinalRelease](ccomobjectrootex-class.md#finalrelease).  
  
##  <a name="m_hresfinalconstruct"></a>  CComObjectStack::m_hResFinalConstruct  
 Zawiera `HRESULT` zwracana z wywołania `FinalConstruct` podczas budowy `CComObjectStack` obiektu.  
  
```
HRESULT    m_hResFinalConstruct;
```  
  
##  <a name="queryinterface"></a>  CComObjectStack::QueryInterface  
 Zwraca **E_NOINTERFACE**.  
  
```
HRESULT    QueryInterface(REFIID, void**)
 ;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **E_NOINTERFACE**.  
  
### <a name="remarks"></a>Uwagi  
 W trybie debugowania, wywołuje `_ASSERTE`.  
  
##  <a name="release"></a>  CComObjectStack::Release  
 Zwraca wartość zero.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 W trybie debugowania, wywołuje `_ASSERTE`.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CComAggObject](../../atl/reference/ccomaggobject-class.md)   
 [Element CComObject — klasa](../../atl/reference/ccomobject-class.md)   
 [Klasa CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
