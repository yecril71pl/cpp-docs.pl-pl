---
title: Klasa CComEnum
ms.date: 11/04/2016
f1_keywords:
- CComEnum
- atlcom/ATL::CComEnum
helpviewer_keywords:
- CComEnum class
ms.assetid: bff7dd7b-eb6e-4d6e-96ed-2706e66c8b3b
ms.openlocfilehash: 7252eb2fa5d34618a1c38484a2506bae27a1106a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497219"
---
# <a name="ccomenum-class"></a>Klasa CComEnum

Ta klasa definiuje obiekt modułu wyliczającego COM w oparciu o tablicę.

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

*Opiera*<br/>
Interfejs modułu wyliczającego COM. Zapoznaj się z przykładem [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring) .

*piid*<br/>
Wskaźnik do identyfikatora interfejsu w interfejsie modułu wyliczającego.

*T*<br/>
Typ elementu uwidocznionego przez interfejs modułu wyliczającego.

*Kopiuj*<br/>
Jednorodna [Klasa zasad kopiowania](../../atl/atl-copy-policy-classes.md).

*ThreadModel*<br/>
Model wątkowości klasy. Ten parametr domyślnie jest modelem wątku obiektu globalnego używanym w projekcie.

## <a name="remarks"></a>Uwagi

`CComEnum`definiuje obiekt modułu wyliczającego COM na podstawie tablicy. Ta klasa jest analogiczna do [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md) , która implementuje moduł wyliczający C++ oparty na kontenerze biblioteki standardowej. Typowe kroki dotyczące korzystania z tej klasy przedstawiono poniżej. Aby uzyskać więcej informacji, zobacz [zestawy ATL i moduły wyliczające](../../atl/atl-collections-and-enumerators.md).

## <a name="to-use-this-class"></a>Aby użyć tej klasy:

- **element typedef** jest specjalizacją tej klasy.

- Użyj `CComObject`elementu **typedef** jako argumentu szablonu w specjalizacji.

- Utwórz wystąpienie `CComObject` specjalizacji.

- Zainicjuj obiekt Enumerator przez wywołanie [CComEnumImpl:: init](../../atl/reference/ccomenumimpl-class.md#init).

- Zwróć interfejs modułu wyliczającego do klienta.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CComObjectRootBase`

`Base`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)

`CComEnum`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcom. h

## <a name="example"></a>Przykład

Kod przedstawiony poniżej udostępnia funkcję wielokrotnego użytku do tworzenia i inicjowania obiektu modułu wyliczającego.

[!code-cpp[NVC_ATL_COM#32](../../atl/codesnippet/cpp/ccomenum-class_1.h)]

Ta funkcja szablonu może służyć do implementowania `_NewEnum` właściwości interfejsu kolekcji, jak pokazano poniżej:

[!code-cpp[NVC_ATL_COM#33](../../atl/codesnippet/cpp/ccomenum-class_2.h)]

Ten kod tworzy **element typedef** dla `CComEnum` , który uwidacznia wektor wariantów za pomocą `IEnumVariant` interfejsu. Klasa `CVariantArrayCollection` jest po prostu `CreateEnumerator` wyspecjalizowana do pracy z obiektami modułu wyliczającego tego typu i przekazuje wymagane argumenty.

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)<br/>
[Klasa CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)<br/>
[Klasa CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)
