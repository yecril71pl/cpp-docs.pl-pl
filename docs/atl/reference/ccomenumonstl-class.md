---
title: Klasa CComEnumOnSTL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComEnumOnSTL
- atlcom/ATL::CComEnumOnSTL
dev_langs:
- C++
helpviewer_keywords:
- CComEnumOnSTL class
ms.assetid: befe1a44-7a00-4f28-9a2e-cc0fa526643c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d42d99baf154bc5434f2d771aeaabb71c5502b30
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ccomenumonstl-class"></a>Klasa CComEnumOnSTL
Ta klasa definiuje obiekt modułu wyliczającego COM oparte na kolekcji standardowa biblioteka C++.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Base,
    const IID* piid, class T, class Copy, class CollType, class ThreadModel = CComObjectThreadModel>  
class ATL_NO_VTABLE CComEnumOnSTL : public IEnumOnSTLImpl<Base, piid,
 T,
    Copy,
 CollType>,
    public CComObjectRootEx<ThreadModel>
```  
  
#### <a name="parameters"></a>Parametry  
 `Base`  
 Moduł wyliczający COM ( [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) interfejsu.  
  
 `piid`  
 Wskaźnik do Identyfikatora interfejsu interfejsu modułu wyliczającego.  
  
 `T`  
 Typ elementu udostępnianych przez interfejs modułu wyliczającego.  
  
 `Copy`  
 A [Kopiuj zasady](../../atl/atl-copy-policy-classes.md) klasy.  
  
 `CollType`  
 Klasa standardowa biblioteka C++ kontenera.  
  
## <a name="remarks"></a>Uwagi  
 `CComEnumOnSTL`Definiuje obiekt modułu wyliczającego COM oparte na kolekcji standardowa biblioteka C++. Ta klasa może być używana samodzielnie lub w połączeniu z [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md). Typowe kroki do używania tej klasy są przedstawione poniżej. Aby uzyskać więcej informacji, zobacz [kolekcje i wyliczenia ATL](../../atl/atl-collections-and-enumerators.md).  
  
## <a name="to-use-this-class-with-icollectiononstlimpl"></a>Aby użyć tej klasy z ICollectionOnSTLImpl:  
  
- `typedef`Specjalizacja tej klasy.  
  
-   Użyj `typedef` jako ostatnim argumentem szablonu w specjalizacji `ICollectionOnSTLImpl`.  
  
 Zobacz [kolekcje i wyliczenia ATL](../../atl/atl-collections-and-enumerators.md) przykład.  
  
## <a name="to-use-this-class-independently-of-icollectiononstlimpl"></a>Aby użyć tej klasy, niezależnie od ICollectionOnSTLImpl:  
  
- `typedef`Specjalizacja tej klasy.  
  
-   Użyj `typedef` jako argument szablonu w specjalizacji `CComObject`.  
  
-   Utwórz wystąpienie `CComObject` specjalizacji.  
  
-   Zainicjowania obiektu modułu wyliczającego wywołując [IEnumOnSTLImpl::Init](../../atl/reference/ienumonstlimpl-class.md#init).  
  
-   Zwraca moduł wyliczający interfejsu do klienta.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CComObjectRootBase`  
  
 `Base`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)  
  
 `CComEnumOnSTL`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
## <a name="example"></a>Przykład  
 Kodem przedstawionym poniżej zawiera ogólne funkcji obsługi tworzenia i inicjowania obiektu modułu wyliczającego:  
  
 [!code-cpp[NVC_ATL_COM#34](../../atl/codesnippet/cpp/ccomenumonstl-class_1.h)]  
  
 Ta funkcja szablonu może służyć do zaimplementowania `_NewEnum` właściwość interfejsu kolekcji, jak pokazano poniżej:  
  
 [!code-cpp[NVC_ATL_COM#35](../../atl/codesnippet/cpp/ccomenumonstl-class_2.h)]  
  
 Ten kod tworzy `typedef` dla `CComEnumOnSTL` który uwidacznia wektorem `CComVariant`s za pomocą klasy **interfejsu IEnumVariant** interfejsu. **CVariantCollection** klasy po prostu specjalizuje się **CreateSTLEnumerator** do pracy z modułu wyliczającego obiektów tego typu.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)   
 [Przykład ATLCollections: Pokazuje klasy zasady niestandardowe kopiowania, CComEnumOnSTL i ICollectionOnSTLImpl](../../visual-cpp-samples.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)   
 [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)   
 [Klasa IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)
