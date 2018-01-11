---
title: Implementowanie element CComObject, CComAggObject i CComPolyObject | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CComPolyObject
- CComAggObject
- CComObject
dev_langs: C++
helpviewer_keywords:
- CComPolyObject class, implementing
- CreateInstance method
- CComAggObject class
- CComObject class, implementing
ms.assetid: 5aabe938-104d-492e-9c41-9f7fb1c62098
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 54f237a629c4af9ea7ae30aeca21c03786abcd97
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-ccomobject-ccomaggobject-and-ccompolyobject"></a>Implementowanie element CComObject, CComAggObject i CComPolyObject
Klasy szablonów [element CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md), i [CComPolyObject](../atl/reference/ccompolyobject-class.md) są zawsze najdalszych pochodnych klas w łańcuch dziedziczenia. Ich odpowiedzialność za obsługę wszystkich metod **IUnknown**: `QueryInterface`, `AddRef`, i **wersji**. Ponadto `CComAggObject` i `CComPolyObject` (jeśli jest używane dla obiektów zagregowane) podaj liczenie odwołań w specjalne i `QueryInterface` semantyki wymagane wewnętrzny nieznany.  
  
 Czy `CComObject`, `CComAggObject`, lub `CComPolyObject` służy zależy od zadeklarować jedną lub żadne następujące makra:  
  
|Makra|Efekt|  
|-----------|------------|  
|`DECLARE_NOT_AGGREGATABLE`|Zawsze używa `CComObject`.|  
|`DECLARE_AGGREGATABLE`|Używa `CComAggObject` Jeśli obiekt jest agregowana i `CComObject` Jeśli nie jest. `CComCoClass`zawiera to makro, jeśli żadna z **DECLARE_\*_AGGREGATABLE** makra są zadeklarowane w klasie, będzie to wartość domyślna.|  
|`DECLARE_ONLY_AGGREGATABLE`|Zawsze używa `CComAggObject`. Zwraca błąd, jeśli obiekt nie jest agregowany.|  
|`DECLARE_POLY_AGGREGATABLE`|ATL tworzy wystąpienie **CComPolyObject\<CYourClass >** podczas **IClassFactory::CreateInstance** jest wywoływana. Podczas tworzenia zaznaczono wartość zewnętrzne nieznany. Jeśli jest **NULL**, **IUnknown** jest zaimplementowany dla obiekt nieagregowane. Jeśli nie jest zewnętrzna nieznany **NULL**, **IUnknown** jest zaimplementowany dla obiekt zagregowanych.|  
  
 Zaletą używania `CComAggObject` i `CComObject` jest to, że implementacja **IUnknown** jest zoptymalizowana pod kątem rodzaj tworzony obiekt. Dla wystąpienia obiektu nieagregowane musi tylko liczbę odwołań, gdy obiekt zagregowane wymaga zarówno liczebności referencyjnej wewnętrzny nieznany i wskaźnika do zewnętrznego nieznany.  
  
 Zaletą używania `CComPolyObject` jest uniknąć oba mających `CComAggObject` i `CComObject` w module obsługi zagregowane i nieagregowane przypadkach. Pojedynczy `CComPolyObject` obiektu obsługuje w obu przypadkach. Oznacza to, że tylko jedna kopia vtable i jedną kopię funkcji istnieje w module. Jeśli Twoje vtable jest duży, to znacznie zmniejszyć rozmiar modułu użytkownika. Jednak jeśli Twoje vtable jest mały, za pomocą `CComPolyObject` może spowodować nieco większy rozmiar modułu, ponieważ nie jest zoptymalizowana dla obiekt zagregowane lub nieagregowane są `CComAggObject` i `CComObject`.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje na temat ATL COM — obiekty](../atl/fundamentals-of-atl-com-objects.md)   
 [Makra agregacji i fabryki klas](../atl/reference/aggregation-and-class-factory-macros.md)

