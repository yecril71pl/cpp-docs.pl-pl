---
title: Klasa CNotSupportedException
ms.date: 11/04/2016
f1_keywords:
- CNotSupportedException
- AFX/CNotSupportedException
- AFX/CNotSupportedException::CNotSupportedException
helpviewer_keywords:
- CNotSupportedException [MFC], CNotSupportedException
ms.assetid: e517391b-eb94-4c39-ae32-87b45bf7d624
ms.openlocfilehash: 0eb3bf0de51345ed4316d2a1c5c29b8ecb3e8bba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456566"
---
# <a name="cnotsupportedexception-class"></a>Klasa CNotSupportedException

Reprezentuje wyjątek, który jest wynikiem żądania nieobsługiwanej funkcji.

## <a name="syntax"></a>Składnia

```
class CNotSupportedException : public CSimpleException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CNotSupportedException::CNotSupportedException](#cnotsupportedexception)|Konstruuje `CNotSupportedException` obiektu.|

## <a name="remarks"></a>Uwagi

Nie dalszych kwalifikacji jest konieczne lub niemożliwe.

Aby uzyskać więcej informacji na temat korzystania z `CNotSupportedException`, zapoznaj się z artykułem [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CNotSupportedException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="cnotsupportedexception"></a>  CNotSupportedException::CNotSupportedException

Konstruuje `CNotSupportedException` obiektu.

```
CNotSupportedException();
```

### <a name="remarks"></a>Uwagi

Nie należy używać tego konstruktora bezpośrednio, ale raczej wywołania funkcji globalnych [afxthrownotsupportedexception —](exception-processing.md#afxthrownotsupportedexception). Aby uzyskać więcej informacji na temat przetwarzanie wyjątków, zobacz artykuł [obsługi wyjątków w MFC](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Zobacz też

[Klasa CException](cexception-class.md)<br/>
[Wykres hierarchii](../hierarchy-chart.md)

