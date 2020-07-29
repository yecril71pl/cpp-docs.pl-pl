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
ms.openlocfilehash: 71b17e777db9d6351192da7cffd075b3a64553bd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222930"
---
# <a name="cmemoryexception-class"></a>Klasa CMemoryException

Reprezentuje warunek wyjątku braku pamięci.

## <a name="syntax"></a>Składnia

```
class CMemoryException : public CSimpleException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMemoryException::CMemoryException](#cmemoryexception)|Konstruuje `CMemoryException` obiekt.|

## <a name="remarks"></a>Uwagi

Dalsze kwalifikacje nie są wymagane ani możliwe. Wyjątki pamięci są generowane automatycznie przez program **`new`** . W przypadku pisania własnych funkcji pamięci przy użyciu programu `malloc` , na przykład, użytkownik jest odpowiedzialny za zgłaszanie wyjątków pamięci.

Aby uzyskać więcej informacji na temat `CMemoryException` , zobacz [Obsługa wyjątków artykułów (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CMemoryException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

## <a name="cmemoryexceptioncmemoryexception"></a><a name="cmemoryexception"></a>CMemoryException::CMemoryException

Konstruuje `CMemoryException` obiekt.

```
CMemoryException();
```

### <a name="remarks"></a>Uwagi

Nie używaj tego konstruktora bezpośrednio, ale zamiast tego wywołaj funkcję globalną [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). Ta funkcja globalna może się powieść w sytuacji braku pamięci, ponieważ konstruuje obiekt Exception w wcześniej przydzielonym pamięci. Aby uzyskać więcej informacji na temat przetwarzania wyjątków, zobacz [wyjątki](../exception-handling-in-mfc.md)w artykule.

## <a name="see-also"></a>Zobacz także

[Klasa CException](cexception-class.md)<br/>
[Wykres hierarchii](../hierarchy-chart.md)
