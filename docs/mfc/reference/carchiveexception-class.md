---
title: Klasa CArchiveException
ms.date: 11/04/2016
f1_keywords:
- CArchiveException
- AFX/CArchiveException
- AFX/CArchiveException::CArchiveException
- AFX/CArchiveException::m_cause
- AFX/CArchiveException::m_strFileName
helpviewer_keywords:
- CArchiveException [MFC], CArchiveException
- CArchiveException [MFC], m_cause
- CArchiveException [MFC], m_strFileName
ms.assetid: da31a127-e86c-41d1-b0b6-bed0865b1b49
ms.openlocfilehash: ad2a9d8c5b4466a04b5a88fcce7679911bf1b81a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377010"
---
# <a name="carchiveexception-class"></a>Klasa CArchiveException

Reprezentuje warunek wyjątku serializacji

## <a name="syntax"></a>Składnia

```
class CArchiveException : public CException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CArchiveException::CArchiveException](#carchiveexception)|Konstruuje `CArchiveException` obiekt.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CArchiveException::m_cause](#m_cause)|Wskazuje przyczynę wyjątku.|
|[CArchiveException::m_strFileName](#m_strfilename)|Określa nazwę pliku dla tego warunku wyjątku.|

## <a name="remarks"></a>Uwagi

Klasa `CArchiveException` zawiera element członkowski danych publicznych, który wskazuje przyczynę wyjątku.

`CArchiveException`obiekty są konstruowane i wyrzucane wewnątrz [funkcji carchive](../../mfc/reference/carchive-class.md) elementu członkowskiego. Można uzyskać dostęp do tych obiektów w zakresie wyrażenia **CATCH.** Kod przyczyny jest niezależny od systemu operacyjnego. Aby uzyskać więcej informacji na temat przetwarzania [wyjątków, zobacz Obsługa wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cexception](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="carchiveexceptioncarchiveexception"></a><a name="carchiveexception"></a>CArchiveException::CArchiveException

Konstruuje `CArchiveException` obiekt, przechowując wartość *przyczyny* w obiekcie.

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Parametry

*Spowodować*<br/>
Zmienna typu wyliczona, która wskazuje przyczynę wyjątku. Aby uzyskać listę wyliczaczy, zobacz [m_cause](#m_cause) element członkowski danych.

*lpszArchiveName*<br/>
Wskazuje ciąg zawierający nazwę `CArchive` obiektu powodującego wyjątek.

### <a name="remarks"></a>Uwagi

Można utworzyć `CArchiveException` obiekt na stosie i rzucić go samodzielnie lub niech funkcja globalna [AfxThrowArchiveException obsłużyć](../../mfc/reference/exception-processing.md#afxthrowarchiveexception) go za Ciebie.

Nie należy używać tego konstruktora bezpośrednio; zamiast tego wywołać `AfxThrowArchiveException`funkcję globalną .

## <a name="carchiveexceptionm_cause"></a><a name="m_cause"></a>CArchiveException::m_cause

Określa przyczynę wyjątku.

```
int m_cause;
```

### <a name="remarks"></a>Uwagi

Ten element członkowski danych jest zmienną publiczną typu **int**. Jego wartości są `CArchiveException` definiowane przez typ wyliczony. Wyliczenia i ich znaczenie są następujące:

- `CArchiveException::none`Nie wystąpił żaden błąd.

- `CArchiveException::genericException`Nieokreślony błąd.

- `CArchiveException::readOnly`Próbowałem zapisać w archiwum otwartym do załadowania.

- `CArchiveException::endOfFile`Osiągnięto koniec pliku podczas odczytywania obiektu.

- `CArchiveException::writeOnly`Próbowałem odczytać z archiwum otwartego do przechowywania.

- `CArchiveException::badIndex`Nieprawidłowy format pliku.

- `CArchiveException::badClass`Próbowałem odczytać obiekt do obiektu o niewłaściwym typie.

- `CArchiveException::badSchema`Próbowałem odczytać obiekt z inną wersją klasy.

    > [!NOTE]
    >  Te `CArchiveException` wyliczacze przyczyny różnią `CFileException` się od wyliczaczy przyczyny.

    > [!NOTE]
    > `CArchiveException::generic`jest przestarzały. Zamiast tego użyj polecenia cmdlet `genericException`. Jeśli **ogólny** jest używany w aplikacji i zbudowany z /clr, będą błędy składni, które nie są łatwe do odszyfrowania.

## <a name="carchiveexceptionm_strfilename"></a><a name="m_strfilename"></a>CArchiveException::m_strFileName

Określa nazwę pliku dla tego warunku wyjątku.

```
CString m_strFileName;
```

## <a name="see-also"></a>Zobacz też

[Klasa CException](../../mfc/reference/cexception-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CArchive](../../mfc/reference/carchive-class.md)<br/>
[AfxThrowArchiveException (Nieeksceptacja afxthrowarchiveexception)](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[Przetwarzanie wyjątków](../../mfc/reference/exception-processing.md)
