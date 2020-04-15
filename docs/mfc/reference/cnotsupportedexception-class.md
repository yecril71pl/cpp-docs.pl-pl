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
ms.openlocfilehash: b859b939baef018e69b245e597eea90e608253ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363192"
---
# <a name="cnotsupportedexception-class"></a>Klasa CNotSupportedException

Reprezentuje wyjątek, który jest wynikiem żądania dla nieobsługiconej funkcji.

## <a name="syntax"></a>Składnia

```
class CNotSupportedException : public CSimpleException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CNotSupportedException::CNotSupportedException](#cnotsupportedexception)|Konstruuje `CNotSupportedException` obiekt.|

## <a name="remarks"></a>Uwagi

Dalsze kwalifikacje nie są konieczne ani możliwe.

Aby uzyskać więcej `CNotSupportedException`informacji na temat używania , zobacz artykuł [Obsługa wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cexception](../../mfc/reference/cexception-class.md)

[Csimpleexception](../../mfc/reference/csimpleexception-class.md)

`CNotSupportedException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="cnotsupportedexceptioncnotsupportedexception"></a><a name="cnotsupportedexception"></a>CNotSupportedException::CNotSupportedException

Konstruuje `CNotSupportedException` obiekt.

```
CNotSupportedException();
```

### <a name="remarks"></a>Uwagi

Nie należy używać tego konstruktora bezpośrednio, ale raczej wywołać funkcję globalną [AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception). Aby uzyskać więcej informacji na temat przetwarzania wyjątków, zobacz artykuł [Obsługa wyjątków w MFC](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Zobacz też

[Klasa CException](cexception-class.md)<br/>
[Wykres hierarchii](../hierarchy-chart.md)
