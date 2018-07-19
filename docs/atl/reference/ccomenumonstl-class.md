---
title: Klasa CComEnumOnSTL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComEnumOnSTL
- atlcom/ATL::CComEnumOnSTL
dev_langs:
- C++
helpviewer_keywords:
- CComEnumOnSTL class
ms.assetid: befe1a44-7a00-4f28-9a2e-cc0fa526643c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ca7b7d38c204d7dd8402b9d610a5800dcef6ced9
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883232"
---
# <a name="ccomenumonstl-class"></a>Klasa CComEnumOnSTL
Ta klasa definiuje obiekt modułu wyliczającego COM, na podstawie kolekcji standardowej biblioteki języka C++.  
  
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
 *podstawowy*  
 Moduł wyliczający COM ( [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) interfejsu.  
  
 *piid*  
 Wskaźnik do Identyfikatora interfejsu interfejsu modułu wyliczającego.  
  
 *T*  
 Typ elementu udostępnianych przez interfejs modułu wyliczającego.  
  
 *Kopiuj*  
 A [Kopiuj zasady](../../atl/atl-copy-policy-classes.md) klasy.  
  
 *CollType*  
 Klasa kontenera standardowej biblioteki języka C++.  
  
## <a name="remarks"></a>Uwagi  
 `CComEnumOnSTL` Definiuje obiekt modułu wyliczającego COM, na podstawie kolekcji standardowej biblioteki języka C++. Ta klasa może być używana, samodzielnie lub w połączeniu z [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md). Typowe kroki dotyczące korzystania z tej klasy są przedstawione poniżej. Aby uzyskać więcej informacji, zobacz [kolekcje i wyliczenia ATL](../../atl/atl-collections-and-enumerators.md).  
  
## <a name="to-use-this-class-with-icollectiononstlimpl"></a>Aby użyć tej klasy przy użyciu ICollectionOnSTLImpl:  
  
- **Element TypeDef** specjalizacji tej klasy.  
  
-   Użyj **typedef** jako ostatnim argumentem szablonu w specjalizacji `ICollectionOnSTLImpl`.  
  
 Zobacz [kolekcje i wyliczenia ATL](../../atl/atl-collections-and-enumerators.md) przykład.  
  
## <a name="to-use-this-class-independently-of-icollectiononstlimpl"></a>Aby użyć tej klasy, niezależnie od ICollectionOnSTLImpl:  
  
- **Element TypeDef** specjalizacji tej klasy.  
  
-   Użyj **typedef** jako argument szablonu w specjalizacji `CComObject`.  
  
-   Utwórz wystąpienie obiektu `CComObject` specjalizacji.  
  
-   Inicjują obiekt modułu wyliczającego, wywołując [IEnumOnSTLImpl::Init](../../atl/reference/ienumonstlimpl-class.md#init).  
  
-   Zwraca interfejs modułu wyliczającego do klienta.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CComObjectRootBase`  
  
 `Base`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)  
  
 `CComEnumOnSTL`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
## <a name="example"></a>Przykład  
 Kodu pokazany poniżej zawiera funkcję ogólną, do obsługi tworzenia i inicjowania obiekt modułu wyliczającego:  
  
 [!code-cpp[NVC_ATL_COM#34](../../atl/codesnippet/cpp/ccomenumonstl-class_1.h)]  
  
 Ta funkcja szablonu może służyć do implementowania `_NewEnum` właściwość interfejsu kolekcji, jak pokazano poniżej:  
  
 [!code-cpp[NVC_ATL_COM#35](../../atl/codesnippet/cpp/ccomenumonstl-class_2.h)]  
  
 Ten kod tworzy **typedef** dla `CComEnumOnSTL` który uwidacznia wektor `CComVariant`s poprzez `IEnumVariant` interfejsu. `CVariantCollection` Klasy po prostu specjalizuje się `CreateSTLEnumerator` do pracy z obiektami modułu wyliczającego tego typu.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)   
 [Przykład ATLCollections: Pokazuje kopii niestandardowych zasad klas, ICollectionOnSTLImpl i CComEnumOnSTL](../../visual-cpp-samples.md)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)   
 [Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)   
 [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)   
 [Klasa IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)
