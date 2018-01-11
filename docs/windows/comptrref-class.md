---
title: "Comptrref — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::Details::ComPtrRef
dev_langs: C++
helpviewer_keywords: ComPtrRef class
ms.assetid: d6bdfd20-e977-45b4-9ac1-1b8efbdb77de
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9b1bbe134f15fdba6863f1725cbcc7effcb6d94f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="comptrref-class"></a>ComPtrRef — Klasa
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <  
   typename T  
>  
class ComPtrRef : public ComPtrRefBase<T>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 A [comptr —\<T >](../windows/comptr-class.md) typu lub typu pochodnego w nie tylko interfejs reprezentowany przez comptr —.  
  
## <a name="remarks"></a>Uwagi  
 Reprezentuje odwołanie do obiektu typu comptr —\<T >.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ComPtrRef::ComPtrRef, konstruktor](../windows/comptrref-comptrref-constructor.md)|Inicjuje nowe wystąpienie klasy comptrref — od określonego wskaźnika do innego obiektu comptrref —.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ComPtrRef::GetAddressOf, metoda](../windows/comptrref-getaddressof-method.md)|Pobiera adres wskaźnika interfejsu reprezentowany przez bieżący obiekt comptrref —.|  
|[ComPtrRef::ReleaseAndGetAddressOf, metoda](../windows/comptrref-releaseandgetaddressof-method.md)|Bieżący obiekt comptrref — usuwa i zwraca wskaźnik do a wskaźnik do interfejsu, który był reprezentowany przez obiekt comptrref —.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Operator ComPtrRef::operator InterfaceType**](../windows/comptrref-operator-interfacetype-star-star-operator.md)|Bieżący obiekt comptrref — usuwa i zwraca wskaźnik do a wskaźnik do interfejsu, który był reprezentowany przez obiekt comptrref —.|  
|[Operator ComPtrRef::operator T*](../windows/comptrref-operator-t-star-operator.md)|Zwraca wartość [ptr_ — element](../windows/comptrrefbase-ptr-data-member.md) bieżącego obiektu comptrref — element członkowski danych.|  
|[Operator ComPtrRef::operator void**](../windows/comptrref-operator-void-star-star-operator.md)|Usuwa bieżący obiekt comptrref —, rzutuje wskaźnik do interfejsu, który był reprezentowany przez obiekt comptrref — jako wskaźnik do wskaźnik do `void`, a następnie zwraca wskaźnik rzutowania.|  
|[Operator ComPtrRef::operator*](../windows/comptrref-operator-star-operator.md)|Pobiera wskaźnik do interfejsu reprezentowany przez bieżący obiekt comptrref —.|  
|[Operator ComPtrRef::operator==](../windows/comptrref-operator-equality-operator.md)|Wskazuje, czy dwa obiekty comptrref — są takie same.|  
|[Operator ComPtrRef::operator!=](../windows/comptrref-operator-inequality-operator.md)|Wskazuje, czy dwa obiekty comptrref — nie są takie same.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ComPtrRefBase`  
  
 `ComPtrRef`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)