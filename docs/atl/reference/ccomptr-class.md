---
title: Klasa CComPtr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
dev_langs:
- C++
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8513a3de54f8a99191936dfff5b894962c597381
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881594"
---
# <a name="ccomptr-class"></a>Klasa CComPtr
Klasa inteligentnego wskaźnika do zarządzania wskaźniki interfejsu COM.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>  
class CComPtr
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Interfejs COM, określając typ wskaźnika, które mają być przechowywane.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComPtr::CComPtr](#ccomptr)|Konstruktor.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComPtr::operator =](#operator_eq)|Przypisuje wskaźnik do wskaźnika elementu członkowskiego.|  
  
## <a name="remarks"></a>Uwagi  
 Używa ATL `CComPtr` i [CComQIPtr](../../atl/reference/ccomqiptr-class.md) Zarządzanie wskaźniki interfejsu COM. Oba są uzyskiwane z [CComPtrBase](../../atl/reference/ccomptrbase-class.md), i jednocześnie wykonywać automatyczne liczenie odwołań.  
  
 `CComPtr` i [CComQIPtr](../../atl/reference/ccomqiptr-class.md) klas mogą pomóc wyeliminować przecieki pamięci, wykonując automatyczne liczenie odwołań.  Następujące funkcje zarówno wykonywania tej samej operacji logicznej; należy jednak zauważyć, jak druga wersja może być mniej podatne na błędy przy użyciu `CComPtr` klasy:  
  
 [!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]  
  
 [!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]  
  
 W kompilacjach do debugowania link atlsd.lib śledzenia kodu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)  
  
 `CComPtr`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="ccomptr"></a>  CComPtr::CComPtr  
 Konstruktor.  
  
```
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```  
  
### <a name="parameters"></a>Parametry  
 *LP*  
 Używane do zainicjowania wskaźnika interfejsu.  
  
 *T*  
 Interfejs COM.  
  
##  <a name="operator_eq"></a>  CComPtr::operator =  
 Operator przypisania.  
  
```
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do zaktualizowanego `CComPtr` obiektu  
  
### <a name="remarks"></a>Uwagi  
 Ta operacja AddRefs nowego obiektu i wersji istniejącego obiektu, jeśli taki istnieje.  
  
## <a name="see-also"></a>Zobacz też  
 [CComPtr::CComPtr](#ccomptr)   
 [CComQIPtr::CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
