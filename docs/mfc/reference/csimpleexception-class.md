---
title: Klasa CSimpleException
ms.date: 11/04/2016
f1_keywords:
- CSimpleException
- AFX/CSimpleException
- AFX/CSimpleException::CSimpleException
- AFX/CSimpleException::GetErrorMessage
helpviewer_keywords:
- CSimpleException [MFC], CSimpleException
- CSimpleException [MFC], GetErrorMessage
ms.assetid: be0eb8ef-e5b9-47d6-b0fb-efaff2d1e666
ms.openlocfilehash: eb94ba9e3d26b3cd910f23c3d4abb29d3b8b1cd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318363"
---
# <a name="csimpleexception-class"></a>Klasa CSimpleException

Ta klasa jest klasą podstawową dla wyjątków MFC o krytycznym znaczeniu dla zasobów.

## <a name="syntax"></a>Składnia

```
class AFX_NOVTABLE CSimpleException : public CException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleException::CSimpleException](#csimpleexception)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleException::GetErrorMessage](#geterrormessage)|Zawiera tekst o błędzie, który wystąpił.|

## <a name="remarks"></a>Uwagi

`CSimpleException`jest klasą podstawową dla wyjątków MFC o krytycznym znaczeniu dla zasobów i obsługuje własność i inicjowanie komunikatu o błędzie. Następujące klasy `CSimpleException` używają jako ich klasy podstawowej:

|||
|-|-|
|[Klasa CMemoryException](../../mfc/reference/cmemoryexception-class.md)|Wyjątek braku pamięci|
|[Klasa CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|Żądania nieobsługiwały operacji|
|[Klasa CResourceException](../../mfc/reference/cresourceexception-class.md)|Nie znaleziono lub nie można utworzyć zasobu systemu Windows|
|[Klasa CUserException](../../mfc/reference/cuserexception-class.md)|Nie można odnaleźć wyjątku wskazującego, że nie można odnaleźć zasobu|
|[Klasa CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|Wyjątek wskazujący nieprawidłowy argument|

Ponieważ `CSimpleException` jest abstrakcyjną klasą podstawową, nie można zadeklarować `CSimpleException` obiektu bezpośrednio. Zamiast tego należy zadeklarować pochodne obiekty, takie jak te w poprzedniej tabeli. Jeśli deklarujesz własną klasę pochodną, użyj poprzednich klas jako modelu.

Aby uzyskać więcej informacji, zobacz [temat klasy CException](../../mfc/reference/cexception-class.md) i [obsługa wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cexception](../../mfc/reference/cexception-class.md)

`CSimpleException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="csimpleexceptioncsimpleexception"></a><a name="csimpleexception"></a>CSimpleException::CSimpleException

Konstruktor.

```
CSimpleException();
explicit CSimpleException(BOOL bAutoDelete);
```

### <a name="parameters"></a>Parametry

*bAutoDelete*<br/>
Określ wartość PRAWDA, `CSimpleException` jeśli pamięć dla obiektu została przydzielona na stercie. Spowoduje to, `CSimpleException` że obiekt zostanie `Delete` usunięty, gdy funkcja elementu członkowskiego jest wywoływana, aby usunąć wyjątek. Określ wartość `CSimpleException` FAŁSZ, jeśli obiekt znajduje się na stosie lub jest obiektem globalnym. W takim przypadku `CSimpleException` obiekt nie zostanie `Delete` usunięty, gdy wywoływana jest funkcja elementu członkowskiego.

### <a name="remarks"></a>Uwagi

Zwykle nigdy nie trzeba wywołać tego konstruktora bezpośrednio. Funkcja, która zgłasza wyjątek należy utworzyć `CException`wystąpienie klasy pochodnej i wywołać jego konstruktora lub należy użyć jednej z funkcji MFC throw, takich jak [AfxThrowFileException](exception-processing.md#afxthrowfileexception), aby rzucić wstępnie zdefiniowany typ.

## <a name="csimpleexceptiongeterrormessage"></a><a name="geterrormessage"></a>CSimpleException::GetErrorMessage

Wywołanie tej funkcji elementu członkowskiego, aby zapewnić tekst o wystąpił błąd.

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT  nMaxError,
    PUNIT  pnHelpContext = NULL);
```

### <a name="parameters"></a>Parametry

*lpszError*<br/>
Wskaźnik do buforu, który otrzyma komunikat o błędzie.

*nMaxError*<br/>
Maksymalna liczba znaków, które bufor może pomieścić, łącznie z terminatorem NULL.

*pnHelpContext*<br/>
Adres UINT, który otrzyma identyfikator kontekstu pomocy. Jeśli null, identyfikator nie zostaną zwrócone.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończy się pomyślnie; w przeciwnym razie 0, jeśli nie jest dostępny tekst komunikatu o błędzie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [CException::GetErrorMessage](../../mfc/reference/cfileexception-class.md#geterrormessage).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CException](../../mfc/reference/cexception-class.md)<br/>
[Obsługa wyjątków](../../mfc/exception-handling-in-mfc.md)
