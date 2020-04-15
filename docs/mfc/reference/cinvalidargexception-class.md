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
ms.openlocfilehash: b28b6e84043b85a8117694a67ff5fff13e7c786b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372373"
---
# <a name="cinvalidargexception-class"></a>Klasa CInvalidArgException

Ta klasa reprezentuje warunek wyjątku nieprawidłowego argumentu.

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

Obiekt `CInvalidArgException` reprezentuje warunek wyjątku nieprawidłowego argumentu.

Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz [CException Class](../../mfc/reference/cexception-class.md) tematu i [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cexception](../../mfc/reference/cexception-class.md)

[Csimpleexception](../../mfc/reference/csimpleexception-class.md)

`CInvalidArgException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="cinvalidargexceptioncinvalidargexception"></a><a name="cinvalidargexception"></a>CInvalidArgException::CInvalidArgException

Konstruktor.

```
CInvalidArgException();
```

### <a name="remarks"></a>Uwagi

Nie należy używać tego konstruktora bezpośrednio; wywołać globalną funkcję **AfxThrowInvalidArgException**.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CSimpleException](../../mfc/reference/csimpleexception-class.md)
