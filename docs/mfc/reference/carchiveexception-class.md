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
ms.openlocfilehash: 731735bccf9225e67d82b1fe90336c92a630b368
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855368"
---
# <a name="carchiveexception-class"></a>Klasa CArchiveException

Reprezentuje warunek wyjątku serializacji

## <a name="syntax"></a>Składnia

```
class CArchiveException : public CException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CArchiveException::CArchiveException](#carchiveexception)|Konstruuje obiekt `CArchiveException`.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CArchiveException:: m_cause](#m_cause)|Wskazuje przyczynę wyjątku.|
|[CArchiveException:: m_strFileName](#m_strfilename)|Określa nazwę pliku dla tego warunku wyjątku.|

## <a name="remarks"></a>Uwagi

Klasa `CArchiveException` zawiera publiczny element członkowski danych, który wskazuje przyczynę wyjątku.

obiekty `CArchiveException` są konstruowane i zgłaszane w funkcjach składowych [CArchive](../../mfc/reference/carchive-class.md) . Możesz uzyskać dostęp do tych obiektów w zakresie wyrażenia **catch** . Kod przyczyny jest niezależny od systemu operacyjnego. Aby uzyskać więcej informacji na temat przetwarzania wyjątków, zobacz [Obsługa wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="carchiveexception"></a>CArchiveException::CArchiveException

Konstruuje obiekt `CArchiveException`, przechowując wartość *przyczyny* w obiekcie.

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Parametry

*może*<br/>
Zmienna typu wyliczeniowego, która wskazuje przyczynę wyjątku. Aby zapoznać się z listą modułów wyliczających, zobacz element członkowski danych [m_cause](#m_cause) .

*lpszArchiveName*<br/>
Wskazuje ciąg zawierający nazwę obiektu `CArchive` powodującego wyjątek.

### <a name="remarks"></a>Uwagi

Można utworzyć obiekt `CArchiveException` na stercie i zgłosić go samodzielnie lub pozwolić, aby funkcja globalna [AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception) go.

Nie używaj tego konstruktora bezpośrednio; Zamiast tego należy wywołać funkcję globalną `AfxThrowArchiveException`.

##  <a name="m_cause"></a>CArchiveException:: m_cause

Określa przyczynę wyjątku.

```
int m_cause;
```

### <a name="remarks"></a>Uwagi

Ten element członkowski danych jest zmienną publiczną typu **int**. Jego wartości są definiowane przez `CArchiveException` typu wyliczeniowego. Moduły wyliczające i ich znaczenie są następujące:

- `CArchiveException::none` nie wystąpił błąd.

- nieokreślony błąd `CArchiveException::genericException`.

- `CArchiveException::readOnly` nastąpiła próba zapisu w archiwum otwartym do ładowania.

- `CArchiveException::endOfFile` osiągnięto koniec pliku podczas odczytywania obiektu.

- `CArchiveException::writeOnly` próbował odczytać z archiwum otwartego do przechowywania.

- `CArchiveException::badIndex` nieprawidłowy format pliku.

- `CArchiveException::badClass` próbował odczytać obiekt w obiekcie nieprawidłowego typu.

- `CArchiveException::badSchema` próbował odczytać obiekt z inną wersją klasy.

    > [!NOTE]
    >  Te `CArchiveException` powodują, że moduły wyliczające są różne od `CFileException` przyczyn.

    > [!NOTE]
    > `CArchiveException::generic` jest przestarzały. Zamiast tego użyj polecenia cmdlet `genericException`. Jeśli **jest** używana w aplikacji i skompilowana przy użyciu opcji/CLR, wystąpią błędy składniowe, które nie są łatwe do odszyfrowania.

##  <a name="m_strfilename"></a>CArchiveException:: m_strFileName

Określa nazwę pliku dla tego warunku wyjątku.

```
CString m_strFileName;
```

## <a name="see-also"></a>Zobacz też

[Klasa CException](../../mfc/reference/cexception-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CArchive](../../mfc/reference/carchive-class.md)<br/>
[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[Przetwarzanie wyjątków](../../mfc/reference/exception-processing.md)
