---
title: Klasa CInvalidArgException
ms.date: 11/04/2016
f1_keywords:
- CInvalidArgException
- AFX/CInvalidArgException
- AFX/CInvalidArgException::CInvalidArgException
helpviewer_keywords:
- CInvalidArgException [MFC], CInvalidArgException
ms.assetid: e43d7c67-1157-47f8-817a-804083e8186e
ms.openlocfilehash: d532698b19a6652feb6e42fdb429d89d49e6ac7b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445425"
---
# <a name="cinvalidargexception-class"></a>Klasa CInvalidArgException

Ta klasa przedstawia wyjątek warunku nieprawidłowego argumentu.

## <a name="syntax"></a>Składnia

```
class CInvalidArgException : public CSimpleException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInvalidArgException::CInvalidArgException](#cinvalidargexception)|Konstruktor.|

## <a name="remarks"></a>Uwagi

A `CInvalidArgException` obiekt reprezentuje wyjątek warunku nieprawidłowego argumentu.

Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz [klasa CException](../../mfc/reference/cexception-class.md) tematu i [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CInvalidArgException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="cinvalidargexception"></a>  CInvalidArgException::CInvalidArgException

Konstruktor.

```
CInvalidArgException();
```

### <a name="remarks"></a>Uwagi

Nie należy używać tego konstruktora bezpośrednio; Wywołaj funkcję globalnego **AfxThrowInvalidArgException**.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CSimpleException](../../mfc/reference/csimpleexception-class.md)
