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
ms.openlocfilehash: 375b4227a25ae4c18cfd263eff4c3ec13f1304e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370005"
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

Dalsze kwalifikacje nie są konieczne ani możliwe. Wyjątki pamięci są generowane automatycznie przez **nowe**. Jeśli piszesz własne funkcje `malloc`pamięci, na przykład przy użyciu , a następnie są odpowiedzialne za zgłaszanie wyjątków pamięci.

Aby uzyskać `CMemoryException`więcej informacji na temat , zobacz artykuł [Obsługa wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cexception](../../mfc/reference/cexception-class.md)

[Csimpleexception](../../mfc/reference/csimpleexception-class.md)

`CMemoryException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="cmemoryexceptioncmemoryexception"></a><a name="cmemoryexception"></a>CMemoryException::CMemoryException

Konstruuje `CMemoryException` obiekt.

```
CMemoryException();
```

### <a name="remarks"></a>Uwagi

Nie należy używać tego konstruktora bezpośrednio, ale raczej wywołać funkcję globalną [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). ta funkcja globalna może odnieść sukces w sytuacji braku pamięci, ponieważ konstruuje obiekt wyjątku w pamięci wcześniej przydzielone. Aby uzyskać więcej informacji na temat przetwarzania [wyjątków,](../exception-handling-in-mfc.md)zobacz wyjątki artykułu .

## <a name="see-also"></a>Zobacz też

[Klasa CException](cexception-class.md)<br/>
[Wykres hierarchii](../hierarchy-chart.md)
