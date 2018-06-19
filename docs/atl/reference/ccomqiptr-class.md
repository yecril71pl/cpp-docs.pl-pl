---
title: Klasa CComQIPtr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
dev_langs:
- C++
helpviewer_keywords:
- CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66c6cc1484ef84ce53ffaf5529575eea43431869
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359182"
---
# <a name="ccomqiptr-class"></a>Klasa CComQIPtr
Klasa wskaźnika inteligentnego do wskaźników interfejsów COM. zarządzania.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T, const IID* piid= &__uuidof(T)>  
class CComQIPtr: public CComPtr<T>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Interfejs COM, określenie typu wskaźnika do zapisania.  
  
 `piid`  
 Wskaźnik na celu uzyskanie identyfikatora IID `T`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComQIPtr::CComQIPtr](#ccomqiptr)|Konstruktor.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComQIPtr::operator =](#operator_eq)|Przypisuje wskaźnik na wskaźnik elementu członkowskiego.|  
  
## <a name="remarks"></a>Uwagi  
 ATL używa `CComQIPtr` i [CComPtr](../../atl/reference/ccomptr-class.md) do zarządzania wskaźniki interfejsu COM, które pochodzi od [CComPtrBase](../../atl/reference/ccomptrbase-class.md). Automatyczne zliczanie za pośrednictwem wywołania wykonać obie klasy `AddRef` i **wersji**. Operatory przeciążone obsługiwać operacje wskaźnika.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)  
  
 [CComPtr](../../atl/reference/ccomptr-class.md)  
  
 `CComQIPtr`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcomcli.h  
  
##  <a name="ccomqiptr"></a>  CComQIPtr::CComQIPtr  
 Konstruktor.  
  
```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lp`  
 Używane w celu zainicjowania wskaźnika interfejsu.  
  
 `T`  
 Interfejs COM.  
  
 `piid`  
 Wskaźnik na celu uzyskanie identyfikatora IID `T`.  
  
##  <a name="operator_eq"></a>  CComQIPtr::operator =  
 Operator przypisania.  
  
```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lp`  
 Używane w celu zainicjowania wskaźnika interfejsu.  
  
 `T`  
 Interfejs COM.  
  
 `piid`  
 Wskaźnik na celu uzyskanie identyfikatora IID `T`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do zaktualizowanego `CComQIPtr` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [CComPtr::CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)   
 [CComQIPtr::CComQIPtr](#ccomqiptr)   
 [Klasa CComPtrBase](../../atl/reference/ccomptrbase-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Klasa CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)
