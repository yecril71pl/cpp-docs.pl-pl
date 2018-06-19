---
title: Klasa CComEnum | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComEnum
- atlcom/ATL::CComEnum
dev_langs:
- C++
helpviewer_keywords:
- CComEnum class
ms.assetid: bff7dd7b-eb6e-4d6e-96ed-2706e66c8b3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 17046239cf4ca5cc95afbc709f10b9c8aedaa9fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362866"
---
# <a name="ccomenum-class"></a>Klasa CComEnum
Ta klasa definiuje obiekt modułu wyliczającego COM na podstawie tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class Base,
    const IID* piid, class T, class Copy, class ThreadModel = CcomObjectThreadModel>  
class ATL_NO_VTABLE CComEnum : public CComEnumImpl<Base, piid,
 T,
    Copy>,
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
 Jednorodnej [skopiuj klasy zasad](../../atl/atl-copy-policy-classes.md).  
  
 `ThreadModel`  
 Model wątkowości klasy. Ten parametr jest domyślnie używany w projekcie modelu wątku globalny obiekt.  
  
## <a name="remarks"></a>Uwagi  
 `CComEnum` Definiuje obiekt modułu wyliczającego COM na podstawie tablicy. Ta klasa jest odpowiednikiem [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md) która implementuje moduł wyliczający oparte na kontenera standardowa biblioteka C++. Typowe kroki do używania tej klasy są przedstawione poniżej. Aby uzyskać więcej informacji, zobacz [kolekcje i wyliczenia ATL](../../atl/atl-collections-and-enumerators.md).  
  
## <a name="to-use-this-class"></a>Aby użyć tej klasy:  
  
- `typedef` Specjalizacja tej klasy.  
  
-   Użyj `typedef` jako argument szablonu w specjalizacji `CComObject`.  
  
-   Utwórz wystąpienie `CComObject` specjalizacji.  
  
-   Zainicjowania obiektu modułu wyliczającego wywołując [CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init).  
  
-   Zwraca moduł wyliczający interfejsu do klienta.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CComObjectRootBase`  
  
 `Base`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)  
  
 `CComEnum`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
  
## <a name="example"></a>Przykład  
 Kodem przedstawionym poniżej zawiera funkcję wielokrotnego użytku do tworzenia i inicjowania obiektu modułu wyliczającego.  
  
 [!code-cpp[NVC_ATL_COM#32](../../atl/codesnippet/cpp/ccomenum-class_1.h)]  
  
 Ta funkcja szablonu może służyć do zaimplementowania `_NewEnum` właściwość interfejsu kolekcji, jak pokazano poniżej:  
  
 [!code-cpp[NVC_ATL_COM#33](../../atl/codesnippet/cpp/ccomenum-class_2.h)]  
  
 Ten kod tworzy `typedef` dla `CComEnum` który uwidacznia wektorem **VARIANT**s za pośrednictwem **interfejsu IEnumVariant** interfejsu. **CVariantArrayCollection** klasy po prostu specjalizuje się **CreateEnumerator** do pracy z modułu wyliczającego obiektów tego typu i przekazuje wymagane argumenty.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)   
 [Klasa CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)   
 [Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)
