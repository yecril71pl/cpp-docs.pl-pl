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
ms.openlocfilehash: afd83c1ddd6f68b10c5cc8c47c0e939bbd01b6c2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840716"
---
# <a name="csimpleexception-class"></a>Klasa CSimpleException

Ta klasa jest klasą bazową dla wyjątków MFC o kluczowym znaczeniu dla zasobów.

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
|[CSimpleException::GetErrorMessage](#geterrormessage)|Zawiera tekst dotyczący błędu, który wystąpił.|

## <a name="remarks"></a>Uwagi

`CSimpleException` jest klasą bazową dla wyjątków MFC o krytycznym znaczeniu dla zasobów i obsługuje własność i inicjalizację komunikatu o błędzie. Następujące klasy są używane `CSimpleException` jako klasa podstawowa:

|Nazwa|Opis|
|-|-|
|[Klasa CMemoryException](../../mfc/reference/cmemoryexception-class.md)|Wyjątek braku pamięci|
|[Klasa CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|Żądania nieobsługiwanej operacji|
|[Klasa CResourceException](../../mfc/reference/cresourceexception-class.md)|Nie znaleziono zasobu systemu Windows lub nie można go uzyskać|
|[Klasa CUserException](../../mfc/reference/cuserexception-class.md)|Wyjątek wskazujący, że nie można znaleźć zasobu|
|[Klasa CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|Wyjątek wskazujący nieprawidłowy argument|

Ponieważ `CSimpleException` jest abstrakcyjną klasą bazową, nie można zadeklarować `CSimpleException` obiektu bezpośrednio. Zamiast tego należy zadeklarować obiekty pochodne, takie jak te w poprzedniej tabeli. Jeśli deklarujesz własną klasę pochodną, użyj powyższych klas jako modelu.

Aby uzyskać więcej informacji, zobacz temat [Klasa CException](../../mfc/reference/cexception-class.md) i [Obsługa wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CSimpleException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

## <a name="csimpleexceptioncsimpleexception"></a><a name="csimpleexception"></a> CSimpleException::CSimpleException

Konstruktor.

```
CSimpleException();
explicit CSimpleException(BOOL bAutoDelete);
```

### <a name="parameters"></a>Parametry

*bAutoDelete*<br/>
Określ wartość TRUE, jeśli pamięć dla `CSimpleException` obiektu została przypisana na stercie. Spowoduje to `CSimpleException` usunięcie obiektu, gdy `Delete` wywoływana jest funkcja członkowska, aby usunąć wyjątek. Określ wartość FAŁSZ, jeśli `CSimpleException` obiekt znajduje się na stosie lub jest obiektem globalnym. W takim przypadku `CSimpleException` obiekt nie zostanie usunięty, gdy `Delete` wywoływana jest funkcja członkowska.

### <a name="remarks"></a>Uwagi

Zwykle nigdy nie trzeba wywoływać tego konstruktora bezpośrednio. Funkcja, która zgłasza wyjątek, powinna utworzyć wystąpienie `CException` klasy pochodnej i wywołać jej konstruktora lub użyć jednej z funkcji Throw MFC, takich jak [AfxThrowFileException](exception-processing.md#afxthrowfileexception), aby zgłosić wstępnie zdefiniowany typ.

## <a name="csimpleexceptiongeterrormessage"></a><a name="geterrormessage"></a> CSimpleException::GetErrorMessage

Wywołaj tę funkcję elementu członkowskiego, aby podać tekst dotyczący błędu, który wystąpił.

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
Maksymalna liczba znaków, jaką może zawierać bufor, łącznie z terminatorem o wartości NULL.

*pnHelpContext*<br/>
Adres klasy UINT, która będzie odbierać identyfikator kontekstu pomocy. Jeśli wartość jest równa NULL, żaden identyfikator nie zostanie zwrócony.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja się powiedzie; w przeciwnym razie, jeśli tekst komunikatu o błędzie nie jest dostępny.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [CException:: GetErrorMessage](../../mfc/reference/cfileexception-class.md#geterrormessage).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CException](../../mfc/reference/cexception-class.md)<br/>
[Obsługa wyjątków](../../mfc/exception-handling-in-mfc.md)
