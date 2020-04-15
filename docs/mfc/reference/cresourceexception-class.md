---
title: Klasa CResourceException
ms.date: 11/04/2016
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
helpviewer_keywords:
- CResourceException [MFC], CResourceException
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
ms.openlocfilehash: 557bfe1cc41c3dda65bd95d7d687820c0b9862b7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368327"
---
# <a name="cresourceexception-class"></a>Klasa CResourceException

Generowane, gdy system Windows nie może znaleźć lub przydzielić żądanego zasobu.

## <a name="syntax"></a>Składnia

```
class CResourceException : public CSimpleException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CResourceException::CResourceException](#cresourceexception)|Konstruuje `CResourceException` obiekt.|

## <a name="remarks"></a>Uwagi

Dalsze kwalifikacje nie są konieczne ani możliwe.

Aby uzyskać więcej `CResourceException`informacji na temat używania , zobacz artykuł [Obsługa wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cexception](../../mfc/reference/cexception-class.md)

[Csimpleexception](../../mfc/reference/csimpleexception-class.md)

`CResourceException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cresourceexceptioncresourceexception"></a><a name="cresourceexception"></a>CResourceException::CResourceException

Konstruuje `CResourceException` obiekt.

```
CResourceException();
```

### <a name="remarks"></a>Uwagi

Nie należy używać tego konstruktora bezpośrednio, ale raczej wywołać funkcję globalną [AfxThrowResourceException](exception-processing.md#afxthrowresourceexception). Aby uzyskać więcej informacji na temat wyjątków, zobacz artykuł [Obsługa wyjątków w MFC](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Zobacz też

[Klasa CException](cexception-class.md)<br/>
[Wykres hierarchii](../hierarchy-chart.md)
