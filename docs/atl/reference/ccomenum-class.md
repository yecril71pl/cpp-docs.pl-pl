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
ms.openlocfilehash: 7f9dff61a62eec37a503b1c0018ead6dce33065a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077116"
---
# <a name="ccomenum-class"></a>Klasa CComEnum

Ta klasa definiuje obiekt modułu wyliczającego COM, na podstawie tablicy.

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

*podstawowy*<br/>
Moduł wyliczający interfejsu COM. Zobacz [IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring) przykład.

*piid*<br/>
Wskaźnik do Identyfikatora interfejsu interfejsu modułu wyliczającego.

*T*<br/>
Typ elementu udostępnianych przez interfejs modułu wyliczającego.

*Kopiuj*<br/>
Jednorodnej [kopiowania klasy zasad](../../atl/atl-copy-policy-classes.md).

*ThreadModel*<br/>
Model wątkowości klasy. Ten parametr używany w projekcie modelu wątku obiektów globalnych.

## <a name="remarks"></a>Uwagi

`CComEnum` Definiuje obiekt modułu wyliczającego COM, na podstawie tablicy. Ta klasa jest odpowiednikiem [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md) który implementuje moduł wyliczający oparta na kontenerze standardowej biblioteki języka C++. Typowe kroki dotyczące korzystania z tej klasy są przedstawione poniżej. Aby uzyskać więcej informacji, zobacz [kolekcje i wyliczenia ATL](../../atl/atl-collections-and-enumerators.md).

## <a name="to-use-this-class"></a>Aby użyć tej klasy:

- **Element TypeDef** specjalizacji tej klasy.

- Użyj **typedef** jako argument szablonu w specjalizacji `CComObject`.

- Utwórz wystąpienie obiektu `CComObject` specjalizacji.

- Inicjują obiekt modułu wyliczającego, wywołując [CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init).

- Zwraca interfejs modułu wyliczającego do klienta.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CComObjectRootBase`

`Base`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)

`CComEnum`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom.h

## <a name="example"></a>Przykład

Kodu pokazany poniżej zawiera funkcję wielokrotnego użytku, do tworzenia i inicjowania obiekt modułu wyliczającego.

[!code-cpp[NVC_ATL_COM#32](../../atl/codesnippet/cpp/ccomenum-class_1.h)]

Ta funkcja szablonu może służyć do implementowania `_NewEnum` właściwość interfejsu kolekcji, jak pokazano poniżej:

[!code-cpp[NVC_ATL_COM#33](../../atl/codesnippet/cpp/ccomenum-class_2.h)]

Ten kod tworzy **typedef** dla `CComEnum` który uwidacznia wektor wariantów za pośrednictwem `IEnumVariant` interfejsu. `CVariantArrayCollection` Klasy po prostu specjalizuje się `CreateEnumerator` do pracy z obiektami modułu wyliczającego tego typu i przekazuje wymagane argumenty.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)<br/>
[Klasa CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)<br/>
[Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)
