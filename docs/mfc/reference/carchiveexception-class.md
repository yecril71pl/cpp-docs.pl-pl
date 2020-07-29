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
ms.openlocfilehash: 68f64cfd7dc96da04fcc0945a6b996eab4101487
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231887"
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
|[CArchiveException:: m_cause](#m_cause)|Wskazuje przyczynę wyjątku.|
|[CArchiveException:: m_strFileName](#m_strfilename)|Określa nazwę pliku dla tego warunku wyjątku.|

## <a name="remarks"></a>Uwagi

`CArchiveException`Klasa zawiera publiczny element członkowski danych, który wskazuje przyczynę wyjątku.

`CArchiveException`obiekty są konstruowane i zgłaszane w funkcjach składowych [CArchive](../../mfc/reference/carchive-class.md) . Możesz uzyskać dostęp do tych obiektów w zakresie wyrażenia **catch** . Kod przyczyny jest niezależny od systemu operacyjnego. Aby uzyskać więcej informacji na temat przetwarzania wyjątków, zobacz [Obsługa wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

## <a name="carchiveexceptioncarchiveexception"></a><a name="carchiveexception"></a>CArchiveException::CArchiveException

Konstruuje `CArchiveException` obiekt, przechowując wartość *przyczyny* w obiekcie.

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Parametry

*może*<br/>
Zmienna typu wyliczeniowego, która wskazuje przyczynę wyjątku. Aby zapoznać się z listą modułów wyliczających, zobacz element członkowski danych [m_cause](#m_cause) .

*lpszArchiveName*<br/>
Wskazuje ciąg zawierający nazwę `CArchive` obiektu powodującego wyjątek.

### <a name="remarks"></a>Uwagi

Można utworzyć `CArchiveException` obiekt na stercie i zgłosić go samodzielnie lub pozwolić, aby funkcja globalna [AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception) go.

Nie używaj tego konstruktora bezpośrednio; Zamiast tego należy wywołać funkcję globalną `AfxThrowArchiveException` .

## <a name="carchiveexceptionm_cause"></a><a name="m_cause"></a>CArchiveException:: m_cause

Określa przyczynę wyjątku.

```
int m_cause;
```

### <a name="remarks"></a>Uwagi

Ten element członkowski danych jest publiczną zmienną typu **`int`** . Jego wartości są definiowane przez `CArchiveException` Typ wyliczeniowy. Moduły wyliczające i ich znaczenie są następujące:

- `CArchiveException::none`Nie wystąpił błąd.

- `CArchiveException::genericException`Nieokreślony błąd.

- `CArchiveException::readOnly`Podjęto próbę zapisu w archiwum otwartym do załadowania.

- `CArchiveException::endOfFile`Osiągnięto koniec pliku podczas odczytywania obiektu.

- `CArchiveException::writeOnly`Podjęto próbę odczytu z archiwum otwartego do przechowywania.

- `CArchiveException::badIndex`Nieprawidłowy format pliku.

- `CArchiveException::badClass`Podjęto próbę odczytu obiektu do obiektu niewłaściwego typu.

- `CArchiveException::badSchema`Podjęto próbę odczytania obiektu z inną wersją klasy.

    > [!NOTE]
    >  Te `CArchiveException` wyliczające przyczyny różnią się od modułów `CFileException` wyliczających przyczyn.

    > [!NOTE]
    > `CArchiveException::generic`jest przestarzały. Zamiast tego użyj polecenia cmdlet `genericException`. Jeśli **jest** używana w aplikacji i skompilowana przy użyciu opcji/CLR, wystąpią błędy składniowe, które nie są łatwe do odszyfrowania.

## <a name="carchiveexceptionm_strfilename"></a><a name="m_strfilename"></a>CArchiveException:: m_strFileName

Określa nazwę pliku dla tego warunku wyjątku.

```
CString m_strFileName;
```

## <a name="see-also"></a>Zobacz także

[Klasa CException](../../mfc/reference/cexception-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CArchive](../../mfc/reference/carchive-class.md)<br/>
[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[Przetwarzanie wyjątku](../../mfc/reference/exception-processing.md)
