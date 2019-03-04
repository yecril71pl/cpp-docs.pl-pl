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
ms.openlocfilehash: aa36fc0ac0eed5ea760224f9e0a3af1c97e18895
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263302"
---
# <a name="csimpleexception-class"></a>Klasa CSimpleException

Ta klasa jest klasa bazowa dla wyjątków MFC ważnych zasobów.

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

`CSimpleException` jest klasa bazowa dla wyjątków MFC ważnych zasobów i obsługuje prawo własności i inicjowania komunikat o błędzie. Następujące klasy użyj `CSimpleException` jako klasy podstawowej:

|||
|-|-|
|[Klasa CMemoryException](../../mfc/reference/cmemoryexception-class.md)|Wyjątek braku pamięci|
|[Klasa CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|Żądania nieobsługiwanej operacji|
|[Klasa CResourceException](../../mfc/reference/cresourceexception-class.md)|Windows zasób nie został znaleziony lub nie możliwe do utworzenia|
|[Klasa CUserException](../../mfc/reference/cuserexception-class.md)|Nie można odnaleźć wyjątek, który określa zasoby|
|[Klasa CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|Wyjątek, który wskazuje nieprawidłowy argument|

Ponieważ `CSimpleException` jest abstrakcyjna klasa bazowa nie można zadeklarować `CSimpleException` obiektu bezpośrednio. Zamiast tego należy zadeklarować obiektów pochodnych, takich jak w poprzedniej tabeli. Jeśli są deklarowanie klasy pochodnej, należy użyć poprzedniej klasy jako model.

Aby uzyskać więcej informacji, zobacz [klasa CException](../../mfc/reference/cexception-class.md) tematu i [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CSimpleException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="csimpleexception"></a>  CSimpleException::CSimpleException

Konstruktor.

```
CSimpleException();
explicit CSimpleException(BOOL bAutoDelete);
```

### <a name="parameters"></a>Parametry

*bAutoDelete*<br/>
Określ wartość PRAWDA, jeśli pamięć `CSimpleException` obiektów została przydzielona na stosie. Spowoduje to `CSimpleException` obiekt do usunięcia podczas `Delete` funkcja członkowska jest wywoływana, aby usunąć wyjątku. Określ wartość FALSE, jeśli `CSimpleException` jest na stosie obiektu lub obiektów globalnych. W tym przypadku `CSimpleException` obiekt nie będą usuwane, gdy `Delete` funkcja członkowska jest wywoływana.

### <a name="remarks"></a>Uwagi

Zwykle nigdy nie należy bezpośrednio wywołania tego konstruktora. Funkcja, która zgłasza wyjątek, należy utworzyć wystąpienie `CException`-klasę pochodną i wywołać jej konstruktora lub jest on powinien użycie MFC zgłosić funkcje, takie jak [afxthrowfileexception —](exception-processing.md#afxthrowfileexception), aby zgłosić wstępnie zdefiniowanego typu.

##  <a name="geterrormessage"></a>  CSimpleException::GetErrorMessage

Wywołaj tę funkcję elementu członkowskiego, aby umieścić tekst o błędzie, który wystąpił.

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT  nMaxError,
    PUNIT  pnHelpContext = NULL);
```

### <a name="parameters"></a>Parametry

*lpszError*<br/>
Wskaźnik do buforu, który zostanie wyświetlony komunikat o błędzie.

*nMaxError*<br/>
Maksymalna liczba znaków, które może przechowywać buforu, w tym terminator o wartości NULL.

*pnHelpContext*<br/>
Adres UINT, który będzie otrzymywał identyfikator kontekstu pomocy Jeśli ma wartość NULL, zostanie zwrócony żaden identyfikator.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja się powiedzie; w przeciwnym razie 0, jeśli żaden błąd tekst komunikatu jest dostępna.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [CException::GetErrorMessage](../../mfc/reference/cfileexception-class.md#geterrormessage).

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CException](../../mfc/reference/cexception-class.md)<br/>
[Obsługa wyjątków](../../mfc/exception-handling-in-mfc.md)
