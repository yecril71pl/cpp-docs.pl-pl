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
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57305123"
---
# <a name="cfileexception-class"></a>Klasa CFileException

Przedstawia warunek wyjątku dotyczący pliku.

## <a name="syntax"></a>Składnia

```
class CFileException : public CException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFileException::CFileException](#cfileexception)|Konstruuje `CFileException` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFileException::ErrnoToException](#errnotoexception)|Zwraca spowodować, że kod odpowiada liczbą błędów czasu wykonywania.|
|[CFileException::GetErrorMessage](#geterrormessage)|Pobiera komunikat opisujący wyjątek.|
|[CFileException::OsErrorToException](#oserrortoexception)|Zwraca kod przyczyny odpowiadający kod błędu systemu operacyjnego.|
|[CFileException::ThrowErrno](#throwerrno)|Zgłasza wyjątek plików na podstawie liczby błędów środowiska uruchomieniowego.|
|[CFileException::ThrowOsError](#throwoserror)|Zgłasza wyjątek pliku, w oparciu o numer błędu systemu operacyjnego.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CFileException::m_cause](#m_cause)|Zawiera kod przenośny odpowiadający Przyczyna wyjątku.|
|[CFileException::m_lOsError](#m_loserror)|Zawiera liczbę błędów dotyczących systemu operacyjnego.|
|[CFileException::m_strFileName](#m_strfilename)|Zawiera nazwę pliku dla tego wyjątku.|

## <a name="remarks"></a>Uwagi

`CFileException` Klasa zawiera publiczne elementy członkowskie danych zawierających kod przenośny przyczyny i numer błędu operacyjnego specyficzne dla systemu. Ta klasa oferuje również statyczne funkcje Członkowskie zgłaszanie wyjątków z pliku i zwracanie kodów przyczyny, zarówno błędów systemu operacyjnego, jak i błędy czasu wykonania języka C.

`CFileException` obiekty są zbudowane i generowane w `CFile` funkcji elementów członkowskich i funkcji składowych klas pochodnych. Możesz uzyskać dostęp tych obiektów w zakresie **CATCH** wyrażenia. Do celów przenośności Użyj tylko kod przyczyny, aby pobrać Przyczyna, dla wyjątku. Aby uzyskać więcej informacji na temat wyjątków, zobacz artykuł [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CFileException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="cfileexception"></a>  CFileException::CFileException

Konstruuje `CFileException` obiekt, który przechowuje kod przyczyny i kod systemu operacyjnego w obiekcie.

```
CFileException(
    int cause = CFileException::none,
    LONG lOsError = -1,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Parametry

*cause*<br/>
Zmienna typu wyliczeniowego, która wskazuje przyczynę, dla wyjątku. Zobacz [CFileException::m_cause](#m_cause) listę możliwych wartości.

*lOsError*<br/>
Działania systemu specyficzne dla Przyczyna wyjątku, jeśli jest dostępny. *LOsError* parametr zawiera więcej informacji, niż *spowodować* jest.

*lpszArchiveName*<br/>
Wskazuje ciąg zawierający nazwę `CFile` obiektu, co powoduje wyjątek.

### <a name="remarks"></a>Uwagi

Nie należy używać tego konstruktora bezpośrednio, ale raczej wywołania funkcji globalnych [afxthrowfileexception —](exception-processing.md#afxthrowfileexception).

> [!NOTE]
>  Zmienna *lOsError* ma zastosowanie tylko do `CFile` i `CStdioFile` obiektów. `CMemFile` Klasa nie obsługuje tego kodu błędu.

##  <a name="errnotoexception"></a>  CFileException::ErrnoToException

Konwertuje wartość błędu danej biblioteki wykonawczej `CFileException` wyliczonych wartości błędu.

```
static int PASCAL ErrnoToException(int nErrno);
```

### <a name="parameters"></a>Parametry

*nErrno*<br/>
Kod błędu całkowitą zgodnie z definicją w pliku dołączania środowiska wykonawczego numer błędu. H.

### <a name="return-value"></a>Wartość zwracana

Wartość wyliczana odpowiada wartości błędu danej biblioteki wykonawczej.

### <a name="remarks"></a>Uwagi

Zobacz [CFileException::m_cause](#m_cause) listę możliwych wyliczonych wartości.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#26](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]

##  <a name="geterrormessage"></a>  CFileException::GetErrorMessage

Pobiera tekst, który opisuje wyjątek.

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT nMaxError,
    PUINT pnHelpContext = NULL) const;
```

### <a name="parameters"></a>Parametry

*lpszError*<br/>
[out w] Wskaźnik do buforu, który odbiera komunikat o błędzie.

*nMaxError*<br/>
[in] Maksymalna liczba znaków, które może przechowywać określonego bufora. Dotyczy to również kończącego znaku null.

*pnHelpContext*<br/>
[out w] Wskaźnik na liczbę całkowitą bez znaku, która odbiera identyfikator kontekstu pomocy Jeśli `NULL`, identyfikator nie jest zwracana.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Jeśli określony bufor jest zbyt mały, komunikat o błędzie zostanie obcięta.

### <a name="example"></a>Przykład

W poniższym przykładzie użyto `CFileException::GetErrorMessage`.

[!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]

##  <a name="m_cause"></a>  CFileException::m_cause

Zawiera wartości zdefiniowane przez `CFileException` Typ wyliczany.

```
int m_cause;
```

### <a name="remarks"></a>Uwagi

Ten element członkowski danych jest publiczną zmienną typu **int**. Moduły wyliczające i ich znaczenie są następujące:

- `CFileException::none` 0: Nie wystąpił błąd.

- `CFileException::genericException` 1: Wystąpił nieokreślony błąd.

- `CFileException::fileNotFound` 2: Nie można zlokalizować pliku.

- `CFileException::badPath` 3: Całość lub część ścieżki jest nieprawidłowy.

- `CFileException::tooManyOpenFiles` 4: Dozwolona liczba otwartych plików została przekroczona.

- `CFileException::accessDenied` 5: Nie można uzyskać dostępu do pliku.

- `CFileException::invalidFile` 6: Podczas próby użycia nieprawidłowe dojście do pliku.

- `CFileException::removeCurrentDir` 7: Nie można usunąć bieżącego katalogu roboczego.

- `CFileException::directoryFull` 8: Nie istnieją żadne więcej wpisów w katalogu.

- `CFileException::badSeek` 9: Wystąpił błąd podczas próby ustawienia wskaźnika pliku.

- `CFileException::hardIO` 10: Wystąpił błąd sprzętowy.

- `CFileException::sharingViolation` 11: Udostępnij. Nie załadowano plik EXE lub udostępniony region został zablokowany.

- `CFileException::lockViolation` 12: Podczas próby zablokować region, który został już zablokowany.

- `CFileException::diskFull` 14: Dysk jest pełny.

- `CFileException::endOfFile` 15: Osiągnięto koniec pliku.

    > [!NOTE]
    >  Te `CFileException` moduły wyliczające Przyczyna różnią się od `CArchiveException` spowodować modułów wyliczających.

    > [!NOTE]
    > `CArchiveException::generic` jest przestarzały. Zamiast nich należy używać słów kluczowych `genericException`. Jeśli **ogólny** jest używane w aplikacji i utworzonych za pomocą/CLR, wynikową składnię, błędy nie są łatwe do odszyfrowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]

##  <a name="m_loserror"></a>  CFileException::m_lOsError

Zawiera kod błędu systemu operacyjnego dla tego wyjątku.

```
LONG m_lOsError;
```

### <a name="remarks"></a>Uwagi

Zobacz techniczne instrukcji listę kodów błędów systemu operacyjnego. Ten element członkowski danych jest publiczną zmienną typu LONG.

##  <a name="m_strfilename"></a>  CFileException::m_strFileName

Zawiera nazwę pliku dla tego warunku wyjątku.

```
CString m_strFileName;
```

##  <a name="oserrortoexception"></a>  CFileException::OsErrorToException

Zwraca moduł wyliczający, który odpowiada danym *lOsError* wartości. Jeśli kod błędu: nieznany, wówczas funkcja zwraca `CFileException::generic`.

```
static int PASCAL OsErrorToException(LONG lOsError);
```

### <a name="parameters"></a>Parametry

*lOsError*<br/>
Kod błędu operacyjnego specyficzne dla systemu.

### <a name="return-value"></a>Wartość zwracana

Wartość wyliczenia, która odpowiada wartości danego błędu systemu operacyjnego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#27](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]

##  <a name="throwerrno"></a>  CFileException::ThrowErrno

Konstruuje `CFileException` obiekt odpowiadający danej *nErrno* wartości, a następnie zgłasza wyjątek.

```
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parametry

*nErrno*<br/>
Kod błędu całkowitą zgodnie z definicją w pliku dołączania środowiska wykonawczego numer błędu. H.

*lpszFileName*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku, który spowodował wyjątek, jeśli jest dostępny.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#28](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]

##  <a name="throwoserror"></a>  CFileException::ThrowOsError

Zgłasza `CFileException` odpowiadający danej *lOsError* wartości. Jeśli kod błędu jest nieznany, a następnie funkcja zgłasza wyjątek zakodowane jako `CFileException::generic`.

```
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parametry

*lOsError*<br/>
Kod błędu operacyjnego specyficzne dla systemu.

*lpszFileName*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku, który spowodował wyjątek, jeśli jest dostępny.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#29](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]

## <a name="see-also"></a>Zobacz także

[Klasa CException](../../mfc/reference/cexception-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Przetwarzanie wyjątków](../../mfc/reference/exception-processing.md)
