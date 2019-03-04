---
title: CPtrList Class
ms.date: 11/04/2016
f1_keywords:
- CPtrList
helpviewer_keywords:
- lists, generic
- CPtrList class [MFC]
- generic lists
ms.assetid: 4139a09c-4338-4f42-9eea-51336120b43c
ms.openlocfilehash: 5b88b0950b3b46f9738bd26080883c00d46f8555
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266240"
---
# <a name="cptrlist-class"></a>CPtrList Class

Obsługuje listy wskaźników typu void.

## <a name="syntax"></a>Składnia

```
class CPtrList : public CObject
```

## <a name="members"></a>Elementy członkowskie

Funkcje elementów członkowskich `CPtrList` są podobne do funkcji elementów członkowskich klasy [CObList](../../mfc/reference/coblist-class.md). Ze względu na to podobieństwa można użyć `CObList` dokumentacji kątem specyfiki funkcja elementu członkowskiego. Po wyświetleniu `CObject` wskaźnik jako funkcja parametru lub zwracanej wartości, Wstaw wskaźnik do **void**.

`CObject*& CObList::GetHead() const;`

na przykład przekłada się na

`void*& CPtrList::GetHead() const;`

## <a name="remarks"></a>Uwagi

`CPtrList` dołącza IMPLEMENT_DYNAMIC — makro do obsługi dostępu typu run-time i zrzucanie `CDumpContext` obiektu. Zrzut elementów listy poszczególnych wskaźnika, należy należy ustawić głębokość kontekstu zrzutu do 1 lub większą.

Nie można serializować list wskaźnika.

Gdy `CPtrList` obiekt zostanie usunięty lub usunięcie jej elementy są usuwane tylko wskaźników, nie mogą odwoływać się do jednostki.

Aby uzyskać więcej informacji na temat korzystania z `CPtrList`, zapoznaj się z artykułem [kolekcje](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CPtrList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll.h

## <a name="see-also"></a>Zobacz także

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CObList](../../mfc/reference/coblist-class.md)
