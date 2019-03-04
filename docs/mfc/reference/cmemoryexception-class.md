---
title: Klasa CMemoryException
ms.date: 11/04/2016
f1_keywords:
- CMemoryException
- AFX/CMemoryException
- AFX/CMemoryException::CMemoryException
helpviewer_keywords:
- CMemoryException [MFC], CMemoryException
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
ms.openlocfilehash: 11be0eba080085c507ed718ea23219ca1c93aeba
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57294749"
---
# <a name="cmemoryexception-class"></a>Klasa CMemoryException

Przedstawia warunek wyjątku braku pamięci.

## <a name="syntax"></a>Składnia

```
class CMemoryException : public CSimpleException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMemoryException::CMemoryException](#cmemoryexception)|Konstruuje `CMemoryException` obiektu.|

## <a name="remarks"></a>Uwagi

Nie dalszych kwalifikacji jest konieczne lub niemożliwe. Pamięć wyjątki są zgłaszane automatycznie przez **nowe**. Jeśli piszesz funkcje pamięci, za pomocą `malloc`dla przykładu, a następnie użytkownik jest odpowiedzialny za zgłaszanie wyjątków z pamięci.

Aby uzyskać więcej informacji na temat `CMemoryException`, zapoznaj się z artykułem [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CMemoryException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="cmemoryexception"></a>  CMemoryException::CMemoryException

Konstruuje `CMemoryException` obiektu.

```
CMemoryException();
```

### <a name="remarks"></a>Uwagi

Nie należy używać tego konstruktora bezpośrednio, ale raczej wywołania funkcji globalnych [afxthrowmemoryexception —](exception-processing.md#afxthrowmemoryexception). Ta funkcja globalna może się powieść w sytuacji braku pamięci, ponieważ jego tworzy obiekt wyjątku w pamięci uprzednio przydzielony. Aby uzyskać więcej informacji na temat przetwarzanie wyjątków, zobacz artykuł [wyjątki](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Zobacz także

[Klasa CException](cexception-class.md)<br/>
[Wykres hierarchii](../hierarchy-chart.md)
