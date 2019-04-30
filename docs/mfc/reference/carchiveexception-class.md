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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391312"
---
# <a name="carchiveexception-class"></a>Klasa CArchiveException

Przedstawia warunek wyjątku serializacji

## <a name="syntax"></a>Składnia

```
class CArchiveException : public CException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CArchiveException::CArchiveException](#carchiveexception)|Konstruuje `CArchiveException` obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CArchiveException::m_cause](#m_cause)|Wskazuje przyczynę wyjątku.|
|[CArchiveException::m_strFileName](#m_strfilename)|Określa nazwę pliku dla tego warunku wyjątku.|

## <a name="remarks"></a>Uwagi

`CArchiveException` Klasa zawiera element członkowski danych publicznych, które wskazują przyczynę wyjątku.

`CArchiveException` obiekty są zbudowane i zgłaszane w [CArchive](../../mfc/reference/carchive-class.md) funkcji elementów członkowskich. Możesz uzyskać dostęp tych obiektów w zakresie **CATCH** wyrażenia. Kod przyczyny nie zależy od systemu operacyjnego. Aby uzyskać więcej informacji na temat wyjątek podczas przetwarzania zobacz [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="carchiveexception"></a>  CArchiveException::CArchiveException

Konstruuje `CArchiveException` obiekt przechowywania wartości *spowodować* w obiekcie.

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Parametry

*cause*<br/>
Zmienna typu wyliczeniowego, która wskazuje przyczynę, dla wyjątku. Aby uzyskać listę modułów wyliczających, zobacz [m_cause](#m_cause) element członkowski danych.

*lpszArchiveName*<br/>
Wskazuje ciąg zawierający nazwę `CArchive` obiektu, co powoduje wyjątek.

### <a name="remarks"></a>Uwagi

Możesz utworzyć `CArchiveException` obiektów na stosie i zgłosić samodzielnie lub pozwolić funkcja globalna [afxthrowarchiveexception —](../../mfc/reference/exception-processing.md#afxthrowarchiveexception) go obsłużyć za Ciebie.

Nie należy używać tego konstruktora bezpośrednio; Zamiast tego należy wywołać funkcję globalnego `AfxThrowArchiveException`.

##  <a name="m_cause"></a>  CArchiveException::m_cause

Określa przyczyną wyjątku.

```
int m_cause;
```

### <a name="remarks"></a>Uwagi

Ten element członkowski danych jest publiczną zmienną typu **int**. Wartości są definiowane przez `CArchiveException` Typ wyliczany. Moduły wyliczające i ich znaczenie są następujące:

- `CArchiveException::none` Nie wystąpił błąd.

- `CArchiveException::genericException` Nieokreślony błąd.

- `CArchiveException::readOnly` Podjęto próbę zapisu w archiwum otwartym do załadowania.

- `CArchiveException::endOfFile` Osiągnięto koniec pliku podczas odczytywania obiektu.

- `CArchiveException::writeOnly` Podjęto próbę odczytu z archiwum otwartym do przechowywania.

- `CArchiveException::badIndex` Nieprawidłowy format pliku.

- `CArchiveException::badClass` Podjęto próbę odczytania obiektu do obiektu niewłaściwego typu.

- `CArchiveException::badSchema` Podjęto próbę odczytania obiektu z nieco innej klasy.

    > [!NOTE]
    >  Te `CArchiveException` moduły wyliczające Przyczyna różnią się od `CFileException` spowodować modułów wyliczających.

    > [!NOTE]
    > `CArchiveException::generic` jest przestarzały. Zamiast nich należy używać słów kluczowych `genericException`. Jeśli **ogólny** jest używane w aplikacji i zbudowany z/CLR, wystąpią błędy składniowe, które nie są łatwe do odszyfrowania.

##  <a name="m_strfilename"></a>  CArchiveException::m_strFileName

Określa nazwę pliku dla tego warunku wyjątku.

```
CString m_strFileName;
```

## <a name="see-also"></a>Zobacz także

[Klasa CException](../../mfc/reference/cexception-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CArchive](../../mfc/reference/carchive-class.md)<br/>
[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[Przetwarzanie wyjątków](../../mfc/reference/exception-processing.md)
