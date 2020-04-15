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
ms.openlocfilehash: 2d1025ca33d5641982ba52f1ac539db85df3bfd5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373891"
---
# <a name="cfileexception-class"></a>Klasa CFileException

Reprezentuje warunek wyjątku związanego z plikiem.

## <a name="syntax"></a>Składnia

```
class CFileException : public CException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFileException::CFileException](#cfileexception)|Konstruuje `CFileException` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFileException::ErrnoToException](#errnotoexception)|Zwraca kod przyczyny odpowiadający numerowi błędu w czasie wykonywania.|
|[CFileException::GetErrorMessage](#geterrormessage)|Pobiera komunikat opisujący wyjątek.|
|[CFileException::OsErrorToException](#oserrortoexception)|Zwraca kod przyczyny odpowiadający kodowi błędu systemu operacyjnego.|
|[CFileException::ThrowErrno](#throwerrno)|Zgłasza wyjątek pliku na podstawie numeru błędu środowiska uruchomieniowego.|
|[CFileException::ThrowOsError](#throwoserror)|Zgłasza wyjątek pliku na podstawie numeru błędu systemu operacyjnego.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CFileException::m_cause](#m_cause)|Zawiera przenośny kod odpowiadający sprawie wyjątku.|
|[CFileException::m_lOsError](#m_loserror)|Zawiera powiązany numer błędu systemu operacyjnego.|
|[CFileException::m_strFileName](#m_strfilename)|Zawiera nazwę pliku dla tego wyjątku.|

## <a name="remarks"></a>Uwagi

Klasa `CFileException` zawiera elementy członkowskie danych publicznych, które przechowują kod przyczyny przenośnej i numer błędu specyficzne dla systemu operacyjnego. Klasa zawiera również funkcje statyczne elementy członkowskie do zgłaszania wyjątków plików i zwracania kodów przyczyn dla zarówno błędów systemu operacyjnego, jak i błędów w czasie wykonywania języka C.

`CFileException`obiekty są konstruowane `CFile` i generowane w funkcjach członkowskich i w funkcjach członkowskich klas pochodnych. Można uzyskać dostęp do tych obiektów w zakresie wyrażenia **CATCH.** Aby można było przenieść, użyj tylko kodu przyczyny, aby uzyskać przyczynę wyjątku. Aby uzyskać więcej informacji na temat wyjątków, zobacz artykuł [Obsługa wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cexception](../../mfc/reference/cexception-class.md)

`CFileException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="cfileexceptioncfileexception"></a><a name="cfileexception"></a>CFileException::CFileException

Konstruuje `CFileException` obiekt, który przechowuje kod przyczyny i kod systemu operacyjnego w obiekcie.

```
CFileException(
    int cause = CFileException::none,
    LONG lOsError = -1,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Parametry

*Spowodować*<br/>
Zmienna typu wyliczona, która wskazuje przyczynę wyjątku. Zobacz [CFileException::m_cause](#m_cause) listę możliwych wartości.

*lOsError*<br/>
Wyjątek jest specyficzny dla systemu operacyjnego, jeśli jest dostępny. Parametr *lOsError* zawiera więcej informacji niż *przyczyna.*

*lpszArchiveName*<br/>
Wskazuje ciąg zawierający nazwę `CFile` obiektu powodującego wyjątek.

### <a name="remarks"></a>Uwagi

Nie należy używać tego konstruktora bezpośrednio, ale raczej wywołać funkcję globalną [AfxThrowFileException](exception-processing.md#afxthrowfileexception).

> [!NOTE]
> Zmienna *lOsError* dotyczy `CFile` tylko `CStdioFile` i obiektów. Klasa `CMemFile` nie obsługuje tego kodu błędu.

## <a name="cfileexceptionerrnotoexception"></a><a name="errnotoexception"></a>CFileException::ErrnoToException

Konwertuje daną wartość błędu biblioteki w czasie wykonywania na wyliczoną `CFileException` wartość błędu.

```
static int PASCAL ErrnoToException(int nErrno);
```

### <a name="parameters"></a>Parametry

*nErrno ( nErrno )*<br/>
Kod błędu liczby całkowitej zdefiniowany w czasie wykonywania obejmuje plik ERRNO. H.

### <a name="return-value"></a>Wartość zwracana

Wyliczona wartość odpowiadająca danej wartości błędu biblioteki w czasie wykonywania.

### <a name="remarks"></a>Uwagi

Zobacz [CFileException::m_cause](#m_cause) listę możliwych wartości wyliczonych.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#26](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]

## <a name="cfileexceptiongeterrormessage"></a><a name="geterrormessage"></a>CFileException::GetErrorMessage

Pobiera tekst opisujący wyjątek.

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT nMaxError,
    PUINT pnHelpContext = NULL) const;
```

### <a name="parameters"></a>Parametry

*lpszError*<br/>
[w, na zewnątrz] Wskaźnik do buforu, który odbiera komunikat o błędzie.

*nMaxError*<br/>
[w] Maksymalna liczba znaków, które może pomieścić określony bufor. Obejmuje to kończący się znak null.

*pnHelpContext*<br/>
[w, na zewnątrz] Wskaźnik do niepodpisanej liczby całkowitej, która odbiera identyfikator kontekstu pomocy. Jeśli `NULL`nie zostanie zwrócony identyfikator.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli określony bufor jest zbyt mały, komunikat o błędzie jest obcinany.

### <a name="example"></a>Przykład

W poniższym `CFileException::GetErrorMessage`przykładzie użyto pliku .

[!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]

## <a name="cfileexceptionm_cause"></a><a name="m_cause"></a>CFileException::m_cause

Zawiera wartości zdefiniowane przez `CFileException` typ wyliczony.

```
int m_cause;
```

### <a name="remarks"></a>Uwagi

Ten element członkowski danych jest zmienną publiczną typu **int**. Wyliczenia i ich znaczenie są następujące:

- `CFileException::none`0: Nie wystąpił błąd.

- `CFileException::genericException`1: Wystąpił nieokreślony błąd.

- `CFileException::fileNotFound`2: Nie można zlokalizować pliku.

- `CFileException::badPath`3: Całość lub część ścieżki jest nieprawidłowa.

- `CFileException::tooManyOpenFiles`4: Przekroczono dozwoloną liczbę otwartych plików.

- `CFileException::accessDenied`5: Nie można uzyskać dostępu do pliku.

- `CFileException::invalidFile`6: Podjęto próbę użycia nieprawidłowego dojścia do pliku.

- `CFileException::removeCurrentDir`7: Nie można usunąć bieżącego katalogu roboczego.

- `CFileException::directoryFull`8: Nie ma więcej wpisów katalogu.

- `CFileException::badSeek`9: Wystąpił błąd podczas próby skonfigurowania wskaźnika pliku.

- `CFileException::hardIO`10: Wystąpił błąd sprzętowy.

- `CFileException::sharingViolation`11: UDOSTĘPNIJ. EXE nie został załadowany lub region udostępniony został zablokowany.

- `CFileException::lockViolation`12: Podjęto próbę zablokowania regionu, który był już zablokowany.

- `CFileException::diskFull`14: Dysk jest zapełniony.

- `CFileException::endOfFile`15: Osiągnięto koniec pliku.

    > [!NOTE]
    >  Te `CFileException` wyliczacze przyczyny różnią `CArchiveException` się od wyliczaczy przyczyny.

    > [!NOTE]
    > `CArchiveException::generic`jest przestarzały. Zamiast tego użyj polecenia cmdlet `genericException`. Jeśli **ogólny** jest używany w aplikacji i zbudowany z /clr, wynikające błędy składni nie są łatwe do odszyfrowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]

## <a name="cfileexceptionm_loserror"></a><a name="m_loserror"></a>CFileException::m_lOsError

Zawiera kod błędu systemu operacyjnego dla tego wyjątku.

```
LONG m_lOsError;
```

### <a name="remarks"></a>Uwagi

Lista kodów błędów można znaleźć w instrukcji obsługi systemu operacyjnego. Ten element członkowski danych jest zmienną publiczną typu LONG.

## <a name="cfileexceptionm_strfilename"></a><a name="m_strfilename"></a>CFileException::m_strFileName

Zawiera nazwę pliku dla tego warunku wyjątku.

```
CString m_strFileName;
```

## <a name="cfileexceptionoserrortoexception"></a><a name="oserrortoexception"></a>CFileException::OsErrorToException

Zwraca wyliczenia, który odpowiada danej wartości *lOsError.* Jeśli kod błędu jest nieznany, `CFileException::generic`funkcja zwraca .

```
static int PASCAL OsErrorToException(LONG lOsError);
```

### <a name="parameters"></a>Parametry

*lOsError*<br/>
Kod błędu specyficzny dla systemu operacyjnego.

### <a name="return-value"></a>Wartość zwracana

Wyliczona wartość odpowiadająca danej wartości błędu systemu operacyjnego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#27](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]

## <a name="cfileexceptionthrowerrno"></a><a name="throwerrno"></a>CFileException::ThrowErrno

Konstruuje `CFileException` obiekt odpowiadający danej wartości *nErrno,* a następnie zgłasza wyjątek.

```
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parametry

*nErrno ( nErrno )*<br/>
Kod błędu liczby całkowitej zdefiniowany w czasie wykonywania obejmuje plik ERRNO. H.

*lpszFileName*<br/>
Wskaźnik do ciągu zawierający nazwę pliku, który spowodował wyjątek, jeśli jest dostępny.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#28](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]

## <a name="cfileexceptionthrowoserror"></a><a name="throwoserror"></a>CFileException::ThrowOsError

Rzuca odpowiadającą `CFileException` danej wartości *lOsError.* Jeśli kod błędu jest nieznany, funkcja zgłasza wyjątek `CFileException::generic`kodowany jako .

```
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parametry

*lOsError*<br/>
Kod błędu specyficzny dla systemu operacyjnego.

*lpszFileName*<br/>
Wskaźnik do ciągu zawierający nazwę pliku, który spowodował wyjątek, jeśli jest dostępny.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#29](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CException](../../mfc/reference/cexception-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Przetwarzanie wyjątków](../../mfc/reference/exception-processing.md)
