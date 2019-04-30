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
ms.openlocfilehash: c3af508cd39e277ca4ae0a9aad5e639f66edc53b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407929"
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

## <a name="see-also"></a>Zobacz także

[Klasa CException](cexception-class.md)<br/>
[Wykres hierarchii](../hierarchy-chart.md)
