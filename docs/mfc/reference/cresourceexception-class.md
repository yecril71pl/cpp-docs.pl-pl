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
ms.openlocfilehash: b29112b4901a1fecac37aa7ae61496e874959370
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268112"
---
# <a name="cresourceexception-class"></a>Klasa CResourceException

Generowane, gdy Windows nie można odnaleźć lub przydzielić żądanego zasobu.

## <a name="syntax"></a>Składnia

```
class CResourceException : public CSimpleException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CResourceException::CResourceException](#cresourceexception)|Konstruuje `CResourceException` obiektu.|

## <a name="remarks"></a>Uwagi

Nie dalszych kwalifikacji jest konieczne lub niemożliwe.

Aby uzyskać więcej informacji na temat korzystania z `CResourceException`, zapoznaj się z artykułem [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CResourceException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="cresourceexception"></a>  CResourceException::CResourceException

Konstruuje `CResourceException` obiektu.

```
CResourceException();
```

### <a name="remarks"></a>Uwagi

Nie należy używać tego konstruktora bezpośrednio, ale raczej wywołania funkcji globalnych [afxthrowresourceexception —](exception-processing.md#afxthrowresourceexception). Aby uzyskać więcej informacji na temat wyjątków, zobacz artykuł [obsługi wyjątków w MFC](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Zobacz także

[Klasa CException](cexception-class.md)<br/>
[Wykres hierarchii](../hierarchy-chart.md)
