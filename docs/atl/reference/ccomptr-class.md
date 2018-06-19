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
ms.openlocfilehash: 5254e463050d685840ff90334ecbdb94372f27ef
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358543"
---
# <a name="ccomptr-class"></a>Klasa CComPtr
Klasa wskaźnika inteligentnego do wskaźników interfejsów COM. zarządzania.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class T>  
class CComPtr
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Interfejs COM, określenie typu wskaźnika do zapisania.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComPtr::CComPtr](#ccomptr)|Konstruktor.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComPtr::operator =](#operator_eq)|Przypisuje wskaźnik na wskaźnik elementu członkowskiego.|  
  
## <a name="remarks"></a>Uwagi  
 ATL używa `CComPtr` i [CComQIPtr](../../atl/reference/ccomqiptr-class.md) do wskaźników interfejsów COM. zarządzania. Oba wynikają z [CComPtrBase](../../atl/reference/ccomptrbase-class.md), i jednocześnie wykonywać automatyczne liczenie odwołań.  
  
 **CComPtr** i [CComQIPtr](../../atl/reference/ccomqiptr-class.md) klasy mogą pomóc w eliminowaniu przecieki pamięci, wykonując automatyczne liczenie odwołań.  Następujące funkcje obu wykonywania tych samych operacji logicznych; Zwróć jednak uwagę, jak druga wersja może być mniej podatne na błędy przy użyciu **CComPtr** klasy:  
  
 [!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]  
  
 [!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]  
  
 W kompilacjach do debugowania łącza atlsd.lib kod śledzenia.  
  
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
 `lp`  
 Używane w celu zainicjowania wskaźnika interfejsu.  
  
 `T`  
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
 Ta operacja AddRefs nowego obiektu i wersjach istniejący obiekt, jeśli istnieje.  
  
## <a name="see-also"></a>Zobacz też  
 [CComPtr::CComPtr](#ccomptr)   
 [CComQIPtr::CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)   
 [Przegląd klas](../../atl/atl-class-overview.md)
