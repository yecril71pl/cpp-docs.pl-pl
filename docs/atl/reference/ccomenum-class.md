---
title: Klasa CComEnum
ms.date: 11/04/2016
f1_keywords:
- CComEnum
- atlcom/ATL::CComEnum
helpviewer_keywords:
- CComEnum class
ms.assetid: bff7dd7b-eb6e-4d6e-96ed-2706e66c8b3b
ms.openlocfilehash: 8e0bf49b48c2c0f1a202231e67364637375f9342
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623538"
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
