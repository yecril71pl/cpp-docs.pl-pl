---
title: Klasa CFileException
ms.date: 11/04/2016
f1_keywords:
- CFileException
- AFX/CFileException
- AFX/CFileException::CFileException
- AFX/CFileException::ErrnoToException
- AFX/CFileException::GetErrorMessage
- AFX/CFileException::OsErrorToException
- AFX/CFileException::ThrowErrno
- AFX/CFileException::ThrowOsError
- AFX/CFileException::m_cause
- AFX/CFileException::m_lOsError
- AFX/CFileException::m_strFileName
helpviewer_keywords:
- CFileException [MFC], CFileException
- CFileException [MFC], ErrnoToException
- CFileException [MFC], GetErrorMessage
- CFileException [MFC], OsErrorToException
- CFileException [MFC], ThrowErrno
- CFileException [MFC], ThrowOsError
- CFileException [MFC], m_cause
- CFileException [MFC], m_lOsError
- CFileException [MFC], m_strFileName
ms.assetid: f6491bb9-bfbc-42fd-a952-b33f9b62323f
ms.openlocfilehash: a3514c76d4136fe2bc0b096cc382e6f7f4dd3392
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855379"
---
# <a name="cfileexception-class"></a>Klasa CFileException

Reprezentuje warunek wyjątku związany z plikiem.

## <a name="syntax"></a>Składnia

```
class CFileException : public CException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CFileException::CFileException](#cfileexception)|Konstruuje obiekt `CFileException`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CFileException::ErrnoToException](#errnotoexception)|Zwraca kod spowodowany numerem błędu czasu wykonywania.|
|[CFileException::GetErrorMessage](#geterrormessage)|Pobiera komunikat opisujący wyjątek.|
|[CFileException::OsErrorToException](#oserrortoexception)|Zwraca kod przyczyny odpowiadający kodowi błędu systemu operacyjnego.|
|[CFileException::ThrowErrno](#throwerrno)|Zgłasza wyjątek pliku na podstawie numeru błędu środowiska uruchomieniowego.|
|[CFileException::ThrowOsError](#throwoserror)|Zgłasza wyjątek pliku na podstawie numeru błędu systemu operacyjnego.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CFileException:: m_cause](#m_cause)|Zawiera kod przenośny odpowiadający przyczynie wyjątku.|
|[CFileException:: m_lOsError](#m_loserror)|Zawiera powiązany numer błędu systemu operacyjnego.|
|[CFileException:: m_strFileName](#m_strfilename)|Zawiera nazwę pliku dla tego wyjątku.|

## <a name="remarks"></a>Uwagi

Klasa `CFileException` obejmuje publiczne elementy członkowskie danych, które przechowują kod przyczyny przenośnej oraz numer błędu specyficzny dla systemu operacyjnego. Klasa udostępnia również statyczne funkcje członkowskie do zgłaszania wyjątków plików i zwracania kodów przyczyny dla błędów systemu operacyjnego i błędów czasu wykonywania języka C.

obiekty `CFileException` są konstruowane i zgłaszane w `CFile` funkcjach Członkowskich oraz w funkcjach składowych klas pochodnych. Możesz uzyskać dostęp do tych obiektów w zakresie wyrażenia **catch** . W przypadku przenośności Użyj tylko kodu przyczyny, aby uzyskać przyczynę wyjątku. Aby uzyskać więcej informacji o wyjątkach, zobacz [Obsługa wyjątków artykułów (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CFileException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="cfileexception"></a>CFileException::CFileException

Konstruuje obiekt `CFileException`, który przechowuje kod przyczyny i kod systemu operacyjnego w obiekcie.

```
CFileException(
    int cause = CFileException::none,
    LONG lOsError = -1,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Parametry

*może*<br/>
Zmienna typu wyliczeniowego, która wskazuje przyczynę wyjątku. Aby uzyskać listę możliwych wartości, zobacz [CFileException:: m_cause](#m_cause) .

*lOsError*<br/>
Specyficzny dla systemu operacyjnego powód wyjątku, jeśli jest dostępny. Parametr *lOsError* zawiera więcej informacji niż *przyczyną* .

*lpszArchiveName*<br/>
Wskazuje ciąg zawierający nazwę obiektu `CFile` powodującego wyjątek.

### <a name="remarks"></a>Uwagi

Nie używaj tego konstruktora bezpośrednio, ale zamiast tego wywołaj funkcję globalną [AfxThrowFileException](exception-processing.md#afxthrowfileexception).

> [!NOTE]
>  Zmienna *lOsError* ma zastosowanie tylko do obiektów `CFile` i `CStdioFile`. Klasa `CMemFile` nie obsługuje tego kodu błędu.

##  <a name="errnotoexception"></a>CFileException::ErrnoToException

Konwertuje daną wartość błędu biblioteki wykonawczej na `CFileException` wyliczeniową wartość błędu.

```
static int PASCAL ErrnoToException(int nErrno);
```

### <a name="parameters"></a>Parametry

*nErrno*<br/>
Kod błędu liczby całkowitej, zgodnie z definicją w ERRNO pliku w czasie wykonywania. C.

### <a name="return-value"></a>Wartość zwracana

Wartość wyliczana odpowiadająca podanej wartości błędu biblioteki wykonawczej.

### <a name="remarks"></a>Uwagi

Aby uzyskać listę możliwych wartości wyliczanych, zobacz [CFileException:: m_cause](#m_cause) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#26](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]

##  <a name="geterrormessage"></a>CFileException::GetErrorMessage

Pobiera tekst opisujący wyjątek.

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT nMaxError,
    PUINT pnHelpContext = NULL) const;
```

### <a name="parameters"></a>Parametry

*lpszError*<br/>
[in. out] Wskaźnik do buforu, który odbiera komunikat o błędzie.

*nMaxError*<br/>
podczas Maksymalna liczba znaków, jaką może zawierać określony bufor. Obejmuje to kończący znak null.

*pnHelpContext*<br/>
[in. out] Wskaźnik na liczbę całkowitą bez znaku, która odbiera identyfikator kontekstu pomocy. Jeśli `NULL`, żaden identyfikator nie jest zwracany.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli metoda zakończyła się pomyślnie. w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli określony bufor jest za mały, komunikat o błędzie zostanie obcięty.

### <a name="example"></a>Przykład

Poniższy przykład używa `CFileException::GetErrorMessage`.

[!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]

##  <a name="m_cause"></a>CFileException:: m_cause

Zawiera wartości zdefiniowane przez `CFileException` typu wyliczeniowego.

```
int m_cause;
```

### <a name="remarks"></a>Uwagi

Ten element członkowski danych jest zmienną publiczną typu **int**. Moduły wyliczające i ich znaczenie są następujące:

- `CFileException::none` 0: nie wystąpił błąd.

- `CFileException::genericException` 1: Wystąpił nieokreślony błąd.

- `CFileException::fileNotFound` 2: nie można odnaleźć pliku.

- `CFileException::badPath` 3: cała ścieżka lub jej część jest nieprawidłowa.

- `CFileException::tooManyOpenFiles` 4: Przekroczono dozwoloną liczbę otwartych plików.

- `CFileException::accessDenied` 5: nie można uzyskać dostępu do pliku.

- `CFileException::invalidFile` 6: podjęto próbę użycia nieprawidłowego dojścia do pliku.

- `CFileException::removeCurrentDir` 7: nie można usunąć bieżącego katalogu roboczego.

- `CFileException::directoryFull` 8: nie ma więcej wpisów w katalogu.

- `CFileException::badSeek` 9: Wystąpił błąd podczas próby ustawienia wskaźnika pliku.

- `CFileException::hardIO` 10: Wystąpił błąd sprzętowy.

- `CFileException::sharingViolation` 11: Udostępnianie. Nie załadowano pliku EXE lub udostępniony region został zablokowany.

- `CFileException::lockViolation` 12: podjęto próbę zablokowania regionu, który został już zablokowany.

- `CFileException::diskFull` 14: dysk jest zapełniony.

- `CFileException::endOfFile` 15: osiągnięto koniec pliku.

    > [!NOTE]
    >  Te `CFileException` powodują, że moduły wyliczające są różne od `CArchiveException` przyczyn.

    > [!NOTE]
    > `CArchiveException::generic` jest przestarzały. Zamiast tego użyj polecenia cmdlet `genericException`. Jeśli **jest** używana w aplikacji i skompilowana przy użyciu opcji/CLR, powstałe błędy składni nie są łatwe do odszyfrowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]

##  <a name="m_loserror"></a>CFileException:: m_lOsError

Zawiera kod błędu systemu operacyjnego dla tego wyjątku.

```
LONG m_lOsError;
```

### <a name="remarks"></a>Uwagi

Zapoznaj się z podręcznikiem technicznym systemu operacyjnego, aby zapoznać się z listą kodów błędów. Ten element członkowski danych jest zmienną publiczną typu LONG.

##  <a name="m_strfilename"></a>CFileException:: m_strFileName

Zawiera nazwę pliku dla tego warunku wyjątku.

```
CString m_strFileName;
```

##  <a name="oserrortoexception"></a>CFileException::OsErrorToException

Zwraca moduł wyliczający, który odpowiada danej wartości *lOsError* . Jeśli kod błędu jest nieznany, funkcja zwraca `CFileException::generic`.

```
static int PASCAL OsErrorToException(LONG lOsError);
```

### <a name="parameters"></a>Parametry

*lOsError*<br/>
Kod błędu specyficzny dla systemu operacyjnego.

### <a name="return-value"></a>Wartość zwracana

Wartość wyliczana odpowiadająca danej wartości błędu systemu operacyjnego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#27](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]

##  <a name="throwerrno"></a>CFileException::ThrowErrno

Konstruuje obiekt `CFileException` odpowiadający danej wartości *nErrno* , a następnie zgłasza wyjątek.

```
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parametry

*nErrno*<br/>
Kod błędu liczby całkowitej, zgodnie z definicją w ERRNO pliku w czasie wykonywania. C.

*lpszFileName*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku, który spowodował wyjątek, jeśli jest dostępny.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#28](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]

##  <a name="throwoserror"></a>CFileException::ThrowOsError

Zgłasza `CFileException` odpowiadające danej wartości *lOsError* . Jeśli kod błędu jest nieznany, funkcja zgłasza wyjątek kodowany jako `CFileException::generic`.

```
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parametry

*lOsError*<br/>
Kod błędu specyficzny dla systemu operacyjnego.

*lpszFileName*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku, który spowodował wyjątek, jeśli jest dostępny.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#29](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CException](../../mfc/reference/cexception-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Przetwarzanie wyjątków](../../mfc/reference/exception-processing.md)
