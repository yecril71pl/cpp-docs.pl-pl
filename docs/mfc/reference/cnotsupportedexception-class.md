---
title: Klasa CNotSupportedException | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CNotSupportedException
- AFX/CNotSupportedException
- AFX/CNotSupportedException::CNotSupportedException
dev_langs:
- C++
helpviewer_keywords:
- CNotSupportedException [MFC], CNotSupportedException
ms.assetid: e517391b-eb94-4c39-ae32-87b45bf7d624
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b52151dba90c0cfd0ed834e2ef351838d598eb90
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50068805"
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

